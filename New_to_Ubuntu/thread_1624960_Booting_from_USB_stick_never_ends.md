---
title: "Booting from USB stick never ends"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Jetro on 2010-11-18
Hello there,

I downloaded Ubuntu 10.04 and followed the [instructions](http://www.ubuntu.com/desktop/get-ubuntu/download) to make a proper install on a USB stick.

I wanted to boot it from USB because my existing Ubuntu was not booting due to an error.

It all works all right, I choose "Run Ubuntu from this USB", until the point where the Ubuntu logo comes up and the dots are "animated". It goes on forever, forever & forever. After 20 minutes I realised it was probably hanged up.

I pressed ESC, and this comes up:
```
(process:347): GLib-WARNING**: getpwuid_r(): failed due to unknown user id (0)
                    Begin: Loading essential drivers... ...
Done.
Being: Running /scripts/init-premount...
Done.
Being: Mounting root file system... ...
Begin: Running /scripts/casper-premount ...
Done.
Done.
stdin: error 0
Killed
unable to open '/dev/sda'
stdin: error 0
[    64.632117] usb-4-1: USB disconnect, address 2
```
I've tried this at least three times, all with the same results. :(

---

### Post by ppv on 2010-11-18
You can try and see if using unetbootin to create your live usb boots. unetbootin is another utility to create live usb sticks.

---

### Post by Jetro on 2010-11-18
That worked, thank you very much! :)

---

