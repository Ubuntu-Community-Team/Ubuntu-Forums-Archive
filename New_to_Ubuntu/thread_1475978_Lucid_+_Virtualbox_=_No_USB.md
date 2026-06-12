---
title: "Lucid + Virtualbox = No USB"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-05-07
Hello everyone.  It seems like this is quite a common problem in 10.04, and after doing several searches, I was unable to find a solution.  I did recompile the kernel module, and ran some lines of code (I don't even remember what I tried).  I even tried to edit the fstab like I had to do with Karmic, but this created a boot error.  Unless of it changed it when I upgraded to Lucid this is the PUEL version, not the OSE version.  I also checked for updates.  I am running the most current version.  

If someone could guide me in the right direction I'd appreciate it!

Thanks in advance,

Mike

---

### Post by brk3 on 2010-05-07
Install the Lucid package from here:

[http://download.virtualbox.org/virtualbox/3.2.0_BETA1/]("http://download.virtualbox.org/virtualbox/3.2.0_BETA1/")

If you don't want to use the beta you can run

```
sudo hald --daemon=no
```

prior to running Virtualbox.

---

### Post by giddyup306 on 2010-05-07
> **brk3 said:**
> Install the Lucid package from here:

[http://download.virtualbox.org/virtualbox/3.2.0_BETA1/](http://download.virtualbox.org/virtualbox/3.2.0_BETA1/)

If you don't want to use the beta you can run

```
sudo hald --daemon=no
```prior to running Virtualbox.

Thanks for the reply.  I tried that command before and it gave me:

Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
Error binding udev_event socket: Address already in use


I'll try and install the beta. :guitar:

---

### Post by _0R10N on 2010-05-07
Well, if this is a fresh install of vbox, then you have to go to the "Users and groups" option in your "Administration" menu. Enter the "Privileges" tab scroll down to the option that allows you to use VirtualBox. If you have already installed VBox and upgraded your system, then you should run
```
sudo /etc/init.d/vboxdrv setup
```
to recompile the vbox kernel.

---

### Post by _0R10N on 2010-05-07
> **brk3 said:**
> Install the Lucid package from here:

[http://download.virtualbox.org/virtualbox/3.2.0_BETA1/]("http://download.virtualbox.org/virtualbox/3.2.0_BETA1/")

If you don't want to use the beta you can run

```
sudo hald --daemon=no
```

prior to running Virtualbox.

I have vbox running on Lucid and I didn't have to download any extra package, the only thing I had to do was recompile the kernel.

---

### Post by kwacka on 2010-05-07
post deleted - no new information added

---

### Post by giddyup306 on 2010-05-07
BTW I lol'd at your sig. 

I installed the beta version.  I had to download it 5 times before I could get it to install.  I tried recompiling the Kernal and it gave me some error message.  I just deleted VB and reinstalled the beta.

Thanks guys I'm gonna mark this bad boy as "[SOLVED]".

---

### Post by bobpress on 2010-05-08
There is now a BETA 2. Go to the parent directory and then to the 3.2.0_BETA2 directory for the latest.  Also remember to download the latest Guest Additions .iso image in the same directory.  I was having problems with USB (everything else worked) after moving from 9.04 to 10.02.  This corrected that problem. [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by evelynb on 2010-10-22
I still dont have USB in VirtualBox 3.2.8 OSE. had Ubunto 10.04 upgraded to 10.10 but still no USB, tried the items above 

sudo /etc/init.d/vboxdrv setupgave Commnand not found error

sudo hald --daemon=nohad no effect

I dont know how to recompile the kernel

I already have Windows XP in the virtualbox, how can I upgrade VB or swicth to Beta? will I have to delete the the XP install?

Thank for the help

---

### Post by lkraemer on 2010-10-23
evelynb,
Your XP intall is contained in a VDI (Virtual Disk Image) located at
/home/loginuser/.VirtualBox/HardDisks/*.vdi

To see your hidden VirtualBox folder use CNTL H  from /home/loginuser

All you need to do is get VirtualBox and Guest Additions installed and
then use your VDI file.  (Installing VirtualBox or removing same, won't
remove the VDI files.)

You will need to add a filter to get the USB enabled.

lk

---

### Post by drewsus on 2010-11-26
```
sudo usermod -aG vboxusers $USER
```

Logout, and in.

---

### Post by c0d3m0nk3y on 2011-03-01
hey all, i am on 10.10, with VB 3.2.8

Now i added myself to the group vboxusers, logged in, logged out and then opened up VB with still, no usb support

I tried to do the sudo /etc/init.d/vboxdrv setup, also gave me Commnand not found error

sudo hald --daemon=no as well had no effect

any other suggestions?

---

