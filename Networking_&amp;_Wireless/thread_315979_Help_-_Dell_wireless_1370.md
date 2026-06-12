---
title: "Help - Dell wireless 1370"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by Oblivion165 on 2006-12-10
Hello, im a long time widows user and im trying to get my foot in the door. I love ubuntu and went with it because i heard it was designed for people coming off of windows.

Well my problem is i cant seem to do much, typical newbie. I have ubuntu dual-booted with winxp pro and am trying to get my wireless card to function in ubuntu.

As you can read from the topic title its a dell wireless 1370 Mini-PCI, ive copied over the drivers from another computer with internet access via sdcard and set them un-packaged on the desktop.

I understand that i need to use ndiswrapper to install the driver but i cant even figure out how to change the terminals path to my desktop. I do have ndiswrapper installed, i get a usage tip's -i inffile etc etc when i try the command line:

sudo /usr/sbin/ndiswrapper -i/usr/local/DRIVER/bcmwl5.inf

Which i got from another forum with a similar case. However that post soon got over my head with something called modprobe and so on.

I guess im looking for some command lines or something, but keep in mind that the machine in ubuntu mode does NOT have internet, i see alot of those replies. However i can copy files from another machine.

Thanks for reading,
-Oby

---

### Post by CRCarl on 2006-12-10
I had the same issue with a Inspiron 2200. If you are running Edgy (6.10) click System --> Administration --> Windows Wireless Drivers. 

Open that application, click install new driver. Browse to the folder with bcmwl5.inf, select bcmwl5.inf, click OK. It should say Hardware present: YES. 

Reboot.

Good luck, 

Craig

---

### Post by Oblivion165 on 2006-12-10
Nothing, looked in administration and no luck. Ive looked for a download of edgy but it appears to be built in or something?

Searched the add/remove programs, no results for Edgy

---

### Post by CRCarl on 2006-12-10
Edgy refers to the version of Ubuntu you are running. No worries. 

Can you try the steps in this post?  [http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

---

### Post by Oblivion165 on 2006-12-10
> **CRCarl said:**
> Edgy refers to the version of Ubuntu you are running. No worries. 

Can you try the steps in this post?  [http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")


Thanks alot, im all set now!

---

