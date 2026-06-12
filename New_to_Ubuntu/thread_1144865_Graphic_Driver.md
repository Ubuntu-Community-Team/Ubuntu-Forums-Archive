---
title: "Graphic Driver"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by old_dope on 2009-05-01
During a failed install of Xubuntu 9.04 i received a message stating that the AMD graphics driver my computer uses was not supported. Could this be the reason why when i attempt to boot up without a "Live CD" i see a mass of broken colours on the screen?

Could some knowledgable forum member tell me how i might find out what graphics driver my computer is currently using and if possible how i might update it please.

Many thanks

---

### Post by pro003 on 2009-05-01
What driver did you install and how?

And post the output of this in terminal:

```
# fglrxinfo
```

---

### Post by old_dope on 2009-05-01
Hi pro003
I haven't a installed driver. I thought the driver that was installed by the computer manufacturer could be updated?

I opened a terminal and typed 'fglrxinfo' and received the following output:

ubuntu@ubuntu:~$ fglrxinfo
The program 'fglrxinfo' can be found in the following packages:
 * xorg-driver-fglrx
 * xorg-driver-fglrx-envy
Try: sudo apt-get install <selected package>
bash: fglrxinfo: command not found
ubuntu@ubuntu:~$ 

Sorry for being such a n00b but what should i do next please

---

### Post by pro003 on 2009-05-01
Open terminal and type:

```
sudo apt-get update
``` 

enter your root password...

& Then go to System > ADministration > Hardware Driver ...and activate the source driver for your card, you;ll need an active internet connection to do this.

---

### Post by old_dope on 2009-05-01
I can only access the Internet by using a "Live CD" but i did open a terminal and typed 'sudo apt-get update'. But when the updates were being installed my computer crashed?

I did go along to: Applications -> System but i could find no mention of 'Administration' although i did see a link for Hardware Drivers which i clicked on and it showed all the drivers that are activated and currently in use as well as those drivers that are not activated.

---

### Post by pro003 on 2009-05-01
> **old_dope said:**
> I can only access the Internet by using a "Live CD" but i did open a terminal and typed 'sudo apt-get update'. But when the updates were being installed my computer crashed?

I did go along to: Applications -> System but i could find no mention of 'Administration' although i did see a link for Hardware Drivers which i clicked on and it showed all the drivers that are activated and currently in use as well as those drivers that are not activated.

You mean? You have an INTERNET and you can use it ONLY with LIVE CD?

Why can't you use internet on installed system?

---

### Post by old_dope on 2009-05-01
I was running Xubuntu 8.10 but i tried a fresh install of Xubuntu 9.04 and after the install when i tried to re-boot the computer all i get is:

GRUB Boot Error 15

The only way i can access the Internet now is by using the "Live CD".

I am trying all different people and forums for help to resolve the Error 15 and get my computer to boot up properly but fast losing hope.

If there is anyone out there with the knowledge to rectify the above error i would really appreciate it.

---

### Post by pro003 on 2009-05-01
> **old_dope said:**
> I was running Xubuntu 8.10 but i tried a fresh install of Xubuntu 9.04 and after the install when i tried to re-boot the computer all i get is:

GRUB Boot Error 15

The only way i can access the Internet now is by using the "Live CD".

I am trying all different people and forums for help to resolve the Error 15 and get my computer to boot up properly but fast losing hope.

If there is anyone out there with the knowledge to rectify the above error i would really appreciate it.

Insert your install CD and boot into RESCUE or REPAIR MODE and then you follow instructions until you get menu to drop to shell or fix screen issues or reinstall grub..

---

