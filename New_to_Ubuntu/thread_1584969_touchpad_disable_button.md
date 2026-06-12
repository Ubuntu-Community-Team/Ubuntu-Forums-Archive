---
title: "touchpad disable button"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by tedygram311 on 2010-09-29
I have a pavilion dv5 and there is a button on here where you can disable the touchpad.  However when I hit this button the entire keyboard becomes disabled and will not activate again until I restart the computer.  I am only able to do that by holding down the power button until it turns off. Any ideas?

---

### Post by kerry_s on 2010-09-29
> Any ideas?

don't press the button! :lolflag:

(sorry, couldn't help myself :) )

---

### Post by tedygram311 on 2010-09-29
Har har, that is what I have been doing but I was looking for something a little better than that.

---

### Post by kerry_s on 2010-09-29
i did find a bug report on it, maybe read through it, see if any of those fixes work.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/571638](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/571638)

---

### Post by Chris1274 on 2010-09-29
I don't know how to get the button to work right, but you can turn off the touchpad with this terminal command:
```
sudo synclient TouchpadOff=1
```
To reenable it, just do the same command but with '0' instead of '1'.

---

### Post by robert shearer on 2010-09-29
For future reference, powering off/hard reset risks file corruption.  :(

Here is a link to the right way to exit a freeze.

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down.  :)

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

---

### Post by Chris1274 on 2010-09-29
> **robert shearer said:**
> For future reference, powering off/hard reset risks file corruption.  :(

Here is a link to the right way to exit a freeze.

[http://www.arsgeek.com/2006/12/12/ho...ll-else-fails/](http://www.arsgeek.com/2006/12/12/ho...ll-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down.  :)

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

Your link seems to be defunct :-k

---

### Post by robert shearer on 2010-09-29
> **Chris1274 said:**
> Your link seems to be defunct :-k

Rats !!

Try this...

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

Will fix the other one.
Thanks..:)

---

### Post by tedygram311 on 2010-10-05
```
 sudo synclient Touchpadoff=1 
```no dice on this. tried 0 and still the touchpad works fine... thoughts?

---

### Post by KernelPanic14 on 2010-10-13
I once accidentally clicked it. Turned it back on, and the touchpad didn't work. worst thing, after turning the computer back on, the touchpad would work until I logged in, as soon as the login sound was heard it would deactivate.

I turned it again on by running gconf-editor (Alt+F2 then type gconf-editor) then navigating with the arrows to /desktop/gnome/peripherals/touchpad, tab until you get to the options at the right, arrows till you get to touchpad_enabled, space and a window pops up, space to change to true, then tab until you're at OK and enter.

---

