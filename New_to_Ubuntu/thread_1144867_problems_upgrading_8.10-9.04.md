---
title: "problems upgrading 8.10-9.04"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by niket_a on 2009-05-01
I downloaded the image file and mounted at this path
sudo mount -o loop /home/niket/ubuntu-9.04-desktop-i386.iso /media/cdrom
I even got the icon on desktop --- cdrom0
but i can't see any upgrade dialogue box
i also tried to autorun t but it still doesn't work
 then i tried  to run using alt+ f2 n typing the following command
gksu "sh /cdrom/cdromupgrade"
still its not working
guys please tellme where I am goin wrong

regards
niket

---

### Post by billgoldberg on 2009-05-01
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by blazemore on 2009-05-01
**Network Upgrade for Ubuntu Desktops (Recommended)**

You can easily upgrade over the network with the following procedure. 

Start System/Administration/Update Manager   
Click the Check button to check for new updates. 

If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete. 

A message will appear informing you of the availability of the new release. 
 

Click Upgrade. 


**Upgrading Using the Alternate CD/DVD**

Use this method if the system being upgraded is not connected to the Internet. 

Download the alternate installation CD 

Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded. 

If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like: 

sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0A dialog will be displayed offering you the opportunity to upgrade using that CD. 
Follow the on-screen instructions. 
If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 

gksu "sh /cdrom/cdromupgrade"
Or in Kubuntu run the following command using Alt+F2: 

kdesudo "sh /cdrom/cdromupgrade"
Follow the on-screen instructions.

---

### Post by niket_a on 2009-05-01
Well i have tried that option as well but it takes lot of time and also since my Internet connection is very unpredictable i cant use that option
could you please tell me where I am going wrong in my previous post
or should i burn the image n then try to upgrade it

regards 
niket

---

### Post by blazemore on 2009-05-01
Basically, you didn't read the upgrade notes.
You HAVE to use the alternate CD for an upgrade.

Now, it is quicker and easier to do a network upgrade, because you are downloading less than the size of the alternate CD.

---

### Post by niket_a on 2009-05-01
Hey I got my mistake
I was trying the upgrade thing with the live cd image instead of alternate cd image
thanks for all your replies

I'll try the network upgrade now

regards
niket

---

### Post by blazemore on 2009-05-01
Okay let me know if you run into any problems.

---

### Post by wersdaluv on 2009-05-01
For mounting isos, I recommend apps like gmountiso.

Good luck with upgrading. I suggest a reformat, though, so your system will be cleaner. Just preserve important configuration files and documents.

---

### Post by niket_a on 2009-05-01
hey guys i am back and back with a good news
I am done with upgrading my ubuntu to 9.04 and guess what it went smooth as butter  ...:)
The only thing which is not working is my appearence - visual effects tab.
Before upgrading the visual effects was set to no effects.
I tried to change it to normal but it did not work out and so did for extra. 

I am running ubuntu 9.04 on dell inspiron 1525

regards
niket

---

### Post by mahela007 on 2009-05-03
Hi.......
I'm having problems with upgrading using the alternate CD. The installation proceeds for about two steps as indicated in the progress window that pops up. Then I get a message saying something like 
"Impossible to locate package KDE-Desktop. Please report this as a bug".
upgrading via network is really not an option for me. I'd love to know how to get around this problem and complete my upgrade.
(I'm using kubuntu 8.10)

---

