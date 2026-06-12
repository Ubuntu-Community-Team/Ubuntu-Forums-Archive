---
title: "Ubuntu 10.10 upgrade from 10.04 dpkg error"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by FatalisVester on 2011-02-25
Hello,
I am not a ubuntu n3wb, I've had it as my main OS for over 2 years now but I decided to post here because I'm a n3wb @ posting forums.

So I upgraded from 09.04 to 10.04 then to 10.10. As the upgrade was happening it gave me a dpkg error similar to the one I will show below. Then as I try to upgrade/update/install/remove anything, I get:

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  adobe-flashplugin xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
The following packages will be upgraded:
  aptdaemon bash-completion bind9-host brasero brasero-cdrkit brasero-common
  dnsutils libbind9-60 libbrasero-media1 libdns66 libglib2.0-0 libglib2.0-bin
  libglib2.0-data libglib2.0-dev libisc60 libisccc60 libisccfg60 liblwres60
  phpmyadmin python-aptdaemon python-aptdaemon-gtk rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins tar tzdata tzdata-java
  xkb-data
28 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
Need to get 0B/13.4MB of archives.
After this operation, 16.4kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `lftp': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```...help? 

I NEED this to be fixed 'cause I need to install chroot on this box. 

BY THE WAY- When I first tried to upgrade it would not let me, then I read around and I came to a post that told me to:
```
sudo apt-get remove xserver-xorg-video-all xserver-xorg-video-intel xserver-xorg-video-nouveau
```before I ran the upgrade to 10.10 ... In which I did.

I also did the SAME thing to my other box (which was stolen three days ago)  and it worked like a CHARM. However the only difference I can think of is that I FIRST installed 10.04 in the 2nd box (and it's been tweaked a lot less since I had it basically as a backup)

Thank you for your help in advance!

---

### Post by thefasterblueone on 2011-02-25
try running:


```
sudo apt-get -f install
```

then try:

```
sudo dpkg --configure -a
```

then:

```
sudo apt-get update
```


[https://help.ubuntu.com/community/MaverickUpgrades]("https://help.ubuntu.com/community/MaverickUpgrades")

---

### Post by FatalisVester on 2011-02-25
I did that many times... not sure that I used the >  -f  option. So I just followed your instruction... no dice:

```
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `lftp': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by NightwishFan on 2011-02-25
Try:
```
sudo dpkg --force-all -r lftp && sudo apt-get install lftp && sudo apt-get -f install
```

That is a strange bug, are you sure your disk is not failing?

---

### Post by FatalisVester on 2011-02-25
Tried your code... same error.

No I have no idea whether or not the disk is failing. How would I rule that out?

---

### Post by NightwishFan on 2011-02-25
You can check the disk utility under System -> Administration. There should be a tab for smart data.

If that command did not work, perhaps it might be best to back up and reinstall. If you want me to help you try to fix this I will do so though.

---

### Post by FatalisVester on 2011-02-25
Interesting result...

There is a failure on the disk (?)

...but why did it only happen during the install?

More important: is there ANY way I can salvage this without re-installing?

---

### Post by NightwishFan on 2011-02-25
No, it seems likely you will need to replace the hard disk. I would get all of your data off of it as soon as possible. You should start another thread if you need help doing that.

---

### Post by FatalisVester on 2011-02-25
Wow... I have the worst luck evar!!! Well thank you so much for the quick responses, though. I think this was my very first post. :)

---

### Post by NightwishFan on 2011-02-25
I should explain that nothing you did on Ubuntu was the cause of this. The disk is likely just at the end of its lifespan.

I have little experience with this, so the disk may work for a longer period and not immediately fail, but a reinstall will likely be needed to get the system working regardless.

As I said, you should start as new thread about the disk issue, since I am fairly convinced it is the source of this problem.

---

