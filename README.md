# Ubuntu mouse wheel bug after wake up

In ```/lib/systemd/system-sleep/``` , create a file named ```mouse-wheel``` and open it with ```nano```:

```bash
$ cd /lib/systemd/system-sleep/
$ sudo nano mouse-wheel
```

Write this script:

```bash
#!/bin/bash

#This is the fix for mircosoft mouse scrolling issue after wake from a suspension
if [[ $1 == post ]]; then
    modprobe -r usbhid
    modprobe usbhid
fi
```

Save with CTRL+X / O and change file permissions:

```bash
$ sudo chmod a+x mouse-wheel
```

Now, after each wake up, your mouse work correctly.
