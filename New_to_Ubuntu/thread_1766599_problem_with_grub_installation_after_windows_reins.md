---
title: "problem with grub installation after windows reinstall"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by nkd on 2011-05-24
hi all,
I had a dual boot system with vista and ubuntu 10.10
I recently did a reinstall of vista and my grub was gone.
So I booted up with the live-cd of ubuntu and did a grub install with the following steps:-


> mounted the ubuntu partition
changed dir to the ubuntu partition
executed the following commands
chroot .
mount /proc
mount /dev
grub-install /dev/sda
The hard disk is sda and the last step reported a success.
I got the grub screen on rebooting. But when I chose to boot up ubuntu it gave me a login screen with a popup warning saying this :-

> Install Problem !
The configuration defaults for Gnome Power Manager have not been installed correctly.Please contact your computer adminstrator.
Funny thing is I am unable to login into the system even with a correct password , it is just throwing back the login screen after a few seconds of accepting the password. However, I can login in to a virtual terminal alright.

What should I do to reclaim my lost ubuntu partition !
plz help me out and thanks in advance
nishith

---

### Post by seawolf167 on 2011-05-24
Open tty1 with [CTRL][ALT][F1], and login, then type

```
sudo dpkg --configure -a
```

[Here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")is a guide to reinstalling GRUB if anyone happens here and needs it

---

### Post by nkd on 2011-05-25
I tried 
> sudo dpkg --configure -a
But the problem continues !
So I tried the link you suggested and the document is just wonderful and very illustrative. I tried the ***section 13 Reinstalling GRUB2*** now I have  a new grub2 installation and it boots up just fine now :-
> 
[I][B]sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/B][/I]
Thanks a ton . I have my installation back !
regards
nishith

---

### Post by seawolf167 on 2011-05-25
Awesome, glad you got it working

---

