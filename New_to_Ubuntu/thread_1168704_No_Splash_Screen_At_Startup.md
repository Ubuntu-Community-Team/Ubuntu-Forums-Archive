---
title: "No Splash Screen At Startup"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by RJ12 on 2009-05-24
For some reason when I start Ubuntu 9.04 I dont get a splash screen or text just a blank screen untill it reaches the login window and I have this problem for about 2 weeks when I installed it using Wubi it does the same for shutting off

Please help:cry:

---

### Post by RJ12 on 2009-05-24
*Bump*

---

### Post by shifty_powers on 2009-05-24
have you tried installing startupmanager (search in synaptic)?

---

### Post by kukibird1 on 2009-05-24
I have had this same problem since Gutsy. This may work for you.

in terminal type 

sudo cp /boot/grub/menu.lst  /boot/grub/menu.list.backup

sudo nano /boot/grub/menu.lst


find these lines 

## additional options to use with the default boot option, but not wit$
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet 

and try adding  vga=773 after quiet or whatever is there   
   
save the file  and run 

sudo update-grub

and restart.

If you get errors  on reboot here are other resolutions.

[https://wiki.ubuntu.com/FrameBuffer]("https://wiki.ubuntu.com/FrameBuffer")

---

### Post by RJ12 on 2009-05-24
> **kukibird1 said:**
> I have had this same problem since Gutsy. This may work for you.

in terminal type 

sudo cp /boot/grub/menu.lst  /boot/grub/menu.list.backup

sudo nano /boot/grub/menu.lst


find these lines 

## additional options to use with the default boot option, but not wit$
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet 

and try adding  vga=773 after quiet or whatever is there   
   
save the file  and run 

sudo update-grub

and restart.

If you get errors  on reboot here are other resolutions.

[https://wiki.ubuntu.com/FrameBuffer]("https://wiki.ubuntu.com/FrameBuffer")

When I type in the command nothing happens it just says sudo password for rj then I type it in press enter then nothing happens

---

### Post by miegiel on 2009-05-24
> **RJ12 said:**
> When I type in the command nothing happens it just says sudo password for rj then I type it in press enter then nothing happens

Just because the *cp* command doesn't give any output doesn't mean it didn't make a backup copy of your *menu.lst*. Just go to */boot/grub/* to see if the backup copy is there ;)

```
sudo cp **-v** /boot/grub/menu.lst /boot/grub/menu.list.backup
```should give more info while copying.

---

