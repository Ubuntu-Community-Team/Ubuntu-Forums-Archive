---
title: "Want to startup without GUI"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by shawnisalk on 2009-08-01
Hey, folks,

I'd like to startup Ubuntu without automatically starting up a graphical interface, so I can learn the command-line interface without a graphical crutch.

Can anyone tell me how to do this? I assume there's a file that needs to be edited but don't know where it might be.

Thanks!

---

### Post by Tclarkie on 2009-08-01
when login screen comes up. change session to Failsafe terminal in bottom left

---

### Post by Clorow on 2009-08-01
In the GRUB menu, boot to recovery mode. I think you'll see "drop to root shell" or something like that.

---

### Post by Tclarkie on 2009-08-01
To get full screen, login in gui and then fold ctrl-alt-f1

---

### Post by dennisntstar on 2009-08-01
In fedora and redhat,it was easy and you can do it by editing /etc/inittab file.For 
ubuntu you have to do a bit more work. Chech out this link:
[http://nixcraft.com/linux-software/2654-ubuntu-set-default-runlevel-etc-inittab.html](http://nixcraft.com/linux-software/2654-ubuntu-set-default-runlevel-etc-inittab.html)

---

### Post by shawnisalk on 2009-08-01
Wow. Awesome! Thank you, everyone for the quick replies! I think I'm set.:D

---

### Post by JohnLau on 2009-08-01
I suppose it's not good to modify the GRUB menu
you simply need to stop the GUI service
firstly you install [sysv-rc-conf]("apt: sysc-rc-conf")
then run it in the terminal
```
sudo sysv-rc-conf
```
after that, locate gdm
and press spacebar to remove all the 'x's next to gdm
press q to exit the program
reboot and you won't see the gui...

if you want to launch the gui in the console, you can input
```
startx
```
after you log in

the instructions is a bit hard to understand coz I wrote it in a hurry
sorry for that...

John

---

### Post by metalf8801 on 2009-08-01
> **shawnisalk said:**
> Hey, folks,

I'd like to startup Ubuntu without automatically starting up a graphical interface, so I can learn the command-line interface without a graphical crutch.

Can anyone tell me how to do this? I assume there's a file that needs to be edited but don't know where it might be.

Thanks!

try System > Administration > Services 
make sure you unlock it then scroll down to Graphical login manager (gdm) and un check the box next to it

I hope this helps 
Dan

---

