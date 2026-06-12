---
title: "KDE Bluetooth mobile phone - able to send but not receive"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by gtdaqua on 2007-11-13
I am using Kubuntu 7.10 Gutsy 32-bit. I simply plugged my Belkin bluetooth dongle and was able to send files from my desktop to my nokia n90. But cant send n90 files to desktop!! 

When i send, the blue icon lits on desktop and the phone says 'unable to connect'. 

Can anyone help?

---

### Post by 2ig2ag on 2007-11-13
Dunno
To receive file, You gotta turn on something called &#8220;Bluetooth File Sharing&#8221; in accessories if you have installed it.

---

### Post by gtdaqua on 2007-11-13
I am using kubuntu - not ubuntu. I use the KDE Bluetooth Framework. The thing u have mentioned is available in gnome only (ubuntu)

---

### Post by MickS on 2007-11-13
I have the same problem on KDE Gutsy, worked fine with Feisty.

Mick

---

### Post by ivomans on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145/](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145/) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Same problem overhere.
Just noticed these related bugs in launchpad: 146145 and 157746.

---

### Post by niteblind on 2007-11-16
hi,

really do not know if this is relevant or not. I have just wrutched from Dapper to Gutsy so this may no longer hold true. Using my Belkin dongle on Dapper I always  had to use the following command before I could pair bluetooth:

xhost +

this turns off an ACL of some sort so may be worth a go.

niteblind

---

### Post by gtdaqua on 2007-11-17
> 
hi,

really do not know if this is relevant or not. I have just wrutched from Dapper to Gutsy so this may no longer hold true. Using my Belkin dongle on Dapper I always had to use the following command before I could pair bluetooth:

xhost +

this turns off an ACL of some sort so may be worth a go.


No. No good. Still the same message on phone - "unable to connect".

Actually I am able to pair the devices. Just cant send a photo from the mobile to the PC. Also there is no KBTOBEXSRV which is supposed to act OBEX Server and transfer files from Mobile to PC.

---

### Post by ivomans on 2007-12-10
In Launchpad Peppelorum published an easy workaround, see [https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145/comments/28](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145/comments/28)

Short instruction:[LIST]
[*]Download the package from this link: [http://peppesbodega.nu/files/Packages/kdebluetooth_1.0-beta8-0quickpackage_i386.deb](http://peppesbodega.nu/files/Packages/kdebluetooth_1.0-beta8-0quickpackage_i386.deb)
[*]In a konsole give commands:[LIST]
[*]sudo apt-get remove libkbluetooth0
[*]cd *your-download-directory*[/LIST][LIST]
[*]sudo dpkg -i kdebluetooth_1.0-beta8-0quickpackage_i386.deb[/LIST] [/LIST]No guarantees, but it worked for me!

---

### Post by akwatve on 2008-04-16
I have kubuntu for x86_64. Is there a 64 bit version of this package ?

thanks,

---

### Post by gtdaqua on 2008-04-25
After upgrading to Hardy, this works. 

Although it seems two of the phones in this whole big world has been blacklisted by my Hardy!

---

