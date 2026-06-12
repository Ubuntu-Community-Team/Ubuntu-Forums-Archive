---
title: "Black Berry Curve 8330"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Archie69 on 2009-03-29
Hello All,

I have been reading past posts and it seems I need "BARRY" to be able to use/sync my phone (Blackberry 8330) with ubuntu.  I am running Ubuntu 8.04 32bit and am wondering where I can get Barry?  All the links I've gone to are either dead or aren't at all clear what I need to download.  So thats my first question, where and what do i need?  Terminal or a download is cool. Is this the lone application I need to get going?

Secondly, and this may sound dumb, when I plug in the blackberry the computer recognizes it however wont "mount volume" so I have no access to it.  Is this what BARRY is for?

Any help would be awesome.  Thanks

---

### Post by Archie69 on 2009-03-29
Any takers?

---

### Post by Great Blue Heron on 2009-03-29
[QUOTE=Archie69]I have been reading past posts and it seems I need "BARRY" to be able to use/sync my phone (Blackberry 8330) with ubuntu. I am running Ubuntu 8.04 32bit and am wondering where I can get Barry? All the links I've gone to are either dead or aren't at all clear what I need to download. So thats my first question, where and what do i need? Terminal or a download is cool. Is this the lone application I need to get going?[/QUOTE]

Here's the info on the [Barry Project]("http://netdirect.ca/software/packages/barry/"). This page shows all the [dependencies]("http://netdirect.ca/software/packages/barry/dependencies.php"). The install files can be found on this [Sourceforge page]("http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564").

From the dependencies page the following code should work:
```
sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-de

```

You will need to download and install the following files from Soureforge:
libbarry0_0.14-0_ubuntu804_i386.deb
barry-util_0.14-0_ubuntu804_i386.deb
barrybackup-gui_0.14-0_ubuntu804_i386.deb
libopensync-plugin-barry_0.14-0_ubuntu804_i386.deb

Hopefully, you will now have Barry installed and working.

> Secondly, and this may sound dumb, when I plug in the blackberry the computer recognizes it however wont "mount volume" so I have no access to it. Is this what BARRY is for?


You have to set the media card on your Blackberry to Mass Storage Support Mode. On my 8320 it's located under Options > Media Card > Mass Storage Mode Support: Toggle 'On'. Ubuntu should now be able to mount your media card similar to a standard USB device.

---

### Post by LowSky on 2009-03-29
yeah when connected USB it need a MicroSD card inserted (behind the battery) It will then show up as a mass storage device (Ubuntu thinks its an iPod like device).

---

### Post by Archie69 on 2009-04-05
so when I ran the following code in terminal:

sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-de

I come up with this:

marco@marco-laptop:~$ sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-de
[sudo] password for marco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
E: Couldn't find package zlib1g-de

I have no clue what that means.  I've also downloaded all the other parts from sourforge but i'm not 100% sure how to install them.  If anyone could gimme a hand I'd appreciate it.

---

### Post by version7x on 2009-04-06
> **Archie69 said:**
> so when I ran the following code in terminal:

sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-de

I come up with this:

marco@marco-laptop:~$ sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-de
[sudo] password for marco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
E: Couldn't find package zlib1g-de

I have no clue what that means.  I've also downloaded all the other parts from sourforge but i'm not 100% sure how to install them.  If anyone could gimme a hand I'd appreciate it.

The last package dependency had a typo in it...

E: Couldn't find package zlib1g-de

Should be zliblg-dev

Good luck!

---

### Post by elboeufx on 2009-06-19
Hi,

I'm trying to get Barry on my desktop. I'm using 9.04. Here's what happens when I try to install the various components.

tamas@TamasComputer:~$ sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-de
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
libusb-dev is already the newest version.
libssl-dev is already the newest version.
libssl-dev set to manually installed.
E: Couldn't find package zlib1g-de
tamas@TamasComputer:~$ barry
bash: barry: command not found
tamas@TamasComputer:~$ barry 0.14-0
bash: barry: command not found
tamas@TamasComputer:~$ sudo -s
root@TamasComputer:~# apt-get install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto libgda3-common python-gnome2-extras libt1-5 libzvbi-common
  lesstif2 libgda3-bin libgda3-3 libgdl-1-0 xpdf-common libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
root@TamasComputer:~# apt-get install barry-util_0.14-0_ubuntu804_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package barry-util_0.14-0_ubuntu804_i386.deb
root@TamasComputer:~# apt-get install barrybackup-gui_0.14-0_ubuntu804_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package barrybackup-gui_0.14-0_ubuntu804_i386.deb
root@TamasComputer:~# libopensync-plugin-barry_0.14-0_ubuntu804_i386.deb
bash: libopensync-plugin-barry_0.14-0_ubuntu804_i386.deb: command not found
root@TamasComputer:~# apt-get install libopensync-plugin-barry_0.14-0_ubuntu804_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libopensync-plugin-barry_0.14-0_ubuntu804_i386.deb
root@TamasComputer:~# barry
bash: barry: command not found
root@TamasComputer:~# apt-get install barry-0.14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package barry-0.14

I always get this response: "couldn't find package." Can someone tell me what that's about, and how to fix it. I'm not so concerned with syncing email or anything. All I really want is to get my pictures off the Blackberry (I use an 8100).

Any help would be greatly appreciated.

Thanks,
Elboeufx

---

### Post by scprosser on 2009-06-19
@ Elboeufx-Are you using a media card in your 'Berry? If so, than make sure that "Mass Storage" (Options->Media Card->Scroll down to "Mass Storage Mode Support" and set it to "On", then scroll to "Auto Enable Mass Storage Mode When Connected" and set it to "Yes" and save your settings.
Then, when you plug your 'Berry in via USB, it should Auto Mount, and you just navigate it as you would any other removable memory device. When you're done, and want to disconnect, make SURE you unmount the device. If you don't, Linux has a nasty habit of deleting all your files.

You will also notice that Linux will automatically make a "Trash" folder on your Memory Card, just leave it there, it will be used by the computer as necessary.

Hope this helps.

---

### Post by LowSky on 2009-06-19
[QUOTE=scprosser;7484748

You will also notice that Linux will automatically make a "Trash" folder on your Memory Card, just leave it there, it will be used by the computer as necessary.

Hope this helps.[/QUOTE]


Even better use Shift+Delete to delte suff , this way it doesn't just get move to the trash folder and take up space.

---

