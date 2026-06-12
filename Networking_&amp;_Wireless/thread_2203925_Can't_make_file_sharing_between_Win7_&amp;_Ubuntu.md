---
title: "Can't make file sharing between Win7 &amp; Ubuntu"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by kate3 on 2014-02-05
Hi,
First I'm new to this forum & to entite Linux, so I'm little noob in this & I've got a few problems, & I hope someone will help me :)
Well, there are 2 computers in our house - one my personal rig, which there is Windows 7 64-bit installed & which I use it mainly for gaming & second for my mom, which there was also Windows installed, but I decided to install Linux - Ubuntu, as she doesn't game at all & uses PC only for Internet browsing & Skype. So I thought it would be good idea to install Linux there. At first I downloaded ubuntu iso image 12.04 [last version] & installed in usb (I found the guide how to install linux on usb) sucessfully. But problem was, my mom's PC didn't boot it, I don't know why. Maybe I should change something in bios? I don't know. The only thing I did, I made it's boot priority at first, but nothing. This PC has P7H55 motherboard. However my PC boots that usb with no problems, which has Z77 motherboard. So, then I decided to use another method & I ran that iso image through daemon tools (windows virtual cd/dvd rom software) to install it, because there wasn't dvd rom to burn the image. Everything went like a charm, I setup & customized everything I wanted here & most important thing for me - made file sharing succesfully, so I could watch movies from my personal rig, but daemon tools allowed me to install linux only alongside with windows 7, so there was 2 OS-es which I didn't want & then I decided to made again clean install. So I just removed dvd/rom from my personal rig & installed it on this machine, lol. on my CD I had old version of Ubuntu, but as Ubuntu updates itself to the last version with no problem I didn't see any issue, not to install it. So I installed it & now there's only Ubuntu, which also updated itself to the latest version 12-04. But my pain now is, that I can't share files anymore. I tried everything. Installed samba, but in vain. I mean file sharing is on now, & Ubuntu can see my windows PC, but my windows PC can't see Ubuntu in network. I don't know what is the problem. I used [this guide]("http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/"), but doesn't work for me.
So, my problems are:
[LIST]
[*]How to make my PC see this PC
[*]How to boot from usb in this PC
[/LIST]

---

### Post by Michael_A_Garner on 2014-02-05
I am finding it difficult to understand what you mean by 'boot from usb'. Do you mean that you want to boot the Ubuntu 12.04 OS from a USB device like a thumbdrive or external hard drive? Or do you mean that you would like to install the Ubuntu 12.04 LTS OS from a USB device? If it is the latter there is a nice utility which is recommended by Ubuntu for USB installation. It is Pen Drive's Universal USB installer. You can read more about how that is done here:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

If you have already followed that and are still experiencing problems there may be certain USB ports that are enabled for USB booting and I would try the drive in multiple slots. If you have managed to install, but the OS is not booting then this is likely caused by a BIOS setting. If you have UEFI boot settings etc. you will probably need to turn those off and boot in legacy mode etc. If that is the problem perhaps someone else can give a more detailed answer for your specific motherboard.

As for creating a visible network share for your Windows 7 machine to be able to see and interact with on your Ubuntu machine I would recommend samba as you already mentioned. Installing samba is not enough on its own to create a samba share. Especially if it is to use Windows authentication. There is a GUI included with the samba install for regular implementations of Ubuntu and through this GUI you can configure and setup a samba share/s. If you don't have a the GUI utility then it must be done by editing the samba configuration file located: /etc/samba/smb.conf
You can use any editor you desire. I suggest using one like gedit because it is much more user friendly and runs similar to notepad on Windows. Use a command in the terminal like
```
sudo gedit /etc/samba/smb.conf
``` to edit the file, but I strongly recommend backing it up first in case you mess the file up you can recover it. You may back it up first by running:
```
sudo cp /etc/samba/smb.conf /etc/samba/backupsmb.conf
``` or similar.

Once inside you can scroll to the bottom of the file and insert something like this:
```
[samba_share_name_goes_here][INDENT]browsable = yes

[/INDENT]
[INDENT]read only = yes[/INDENT]
[INDENT]    path = /PATHGOESHERE
[/INDENT]

```[INDENT]

This is an EXTREMELY basic samba configuration and you would likely want to configure file masks and authentication modes, but let's get this working first. :)[/INDENT]

---

### Post by kate3 on 2014-02-06
> **Michael_A_Garner said:**
> I am finding it difficult to understand what you mean by 'boot from usb'. Do you mean that you want to boot the Ubuntu 12.04 OS from a USB device like a thumbdrive or external hard drive? Or do you mean that you would like to install the Ubuntu 12.04 LTS OS from a USB device? If it is the latter there is a nice utility which is recommended by Ubuntu for USB installation. It is Pen Drive's Universal USB installer. You can read more about how that is done here:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

If you have already followed that and are still experiencing problems there may be certain USB ports that are enabled for USB booting and I would try the drive in multiple slots. If you have managed to install, but the OS is not booting then this is likely caused by a BIOS setting. If you have UEFI boot settings etc. you will probably need to turn those off and boot in legacy mode etc. If that is the problem perhaps someone else can give a more detailed answer for your specific motherboard.

As for creating a visible network share for your Windows 7 machine to be able to see and interact with on your Ubuntu machine I would recommend samba as you already mentioned. Installing samba is not enough on its own to create a samba share. Especially if it is to use Windows authentication. There is a GUI included with the samba install for regular implementations of Ubuntu and through this GUI you can configure and setup a samba share/s. If you don't have a the GUI utility then it must be done by editing the samba configuration file located: /etc/samba/smb.conf
You can use any editor you desire. I suggest using one like gedit because it is much more user friendly and runs similar to notepad on Windows. Use a command in the terminal like
```
sudo gedit /etc/samba/smb.conf
``` to edit the file, but I strongly recommend backing it up first in case you mess the file up you can recover it. You may back it up first by running:
```
sudo cp /etc/samba/smb.conf /etc/samba/backupsmb.conf
``` or similar.

Once inside you can scroll to the bottom of the file and insert something like this:
```
[samba_share_name_goes_here][INDENT]browsable = yes

[/INDENT]
[INDENT]read only = yes[/INDENT]
[INDENT]    path = /PATHGOESHERE
[/INDENT]

```[INDENT]

This is an EXTREMELY basic samba configuration and you would likely want to configure file masks and authentication modes, but let's get this working first. :)[/INDENT]


Yes, I meant to install the Ubuntu 12.04 LTS OS from a USB device. [That's the guide]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") I created with, that usb install. I solved that problem now (there was something to change in bios). :)

About sharing... I tried as you said, but still windows 7 can't detect this computer. Did I write these things right?

[IMG]http://i.imgur.com/McY78wk.png[/IMG]

Also I noticed, smbusers file is empty, however there is user in Samba itself. Is this normal?

[IMG]http://i.imgur.com/VvtlcsB.png[/IMG]

And thx for reply :)

---

### Post by kate3 on 2014-02-06
I installed Linux Mint now & file sharing works without any problems. I will keep this OS now.

---

