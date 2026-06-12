---
title: "webcam in ubuntu, wish to have mirror image"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by wjkraymond on 2011-05-21
Good day fellow ubuntu forum users.

I have a laptop and a netbook, both Asus.
Asus k42jy-vx244 and eeepc 1005-ha
both of them dual boot with ubuntu 11.4


I am a regular user of skype video call.


In most video call program, gmail video chat, windows live messenger, etc, the image displayed by our own webcam is in mirror image.

example, there are 2 pictures when you video call, one displaying your friends camera, and the other one your own webcam's video. usually the one displaying ourself is a mirror image. (even though it is mirror image, the friend will be able to see it normal. means if i hold a book infront of my webcam, my friend can read it normally, while i will see a mirror image of the book in my own cam.)

However, my laptop displays a non-mirror image for myself.
This is very confusing for me. 
(sometimes i want to move to the center of the webcam, i move left, but the person in the image move right, even further away from the center)

I dont think its my webcam problem, it works fine in windows7 skype. 
i dont think its ubuntu11.4 version problem as well, since my netbook doesn have this problem, it displays my own video in mirror mode perfectly.

I tried download some webcam programs from the ubuntu software center, such as cheese and camorama webcam viewer but it cant help. there is also no option in skype to activate mirror mode.

can someone please help me with this?
I'll appreciate it very much.

Thank you :-)

---

### Post by silentstone on 2011-05-30
Hello, I have the EeePC 1005hab netbook on Ubuntu 10.04, and it doesn't show me a mirror image normally.  I can make it mirror with Cheese effect "Horizontal flip", or Guvcvideo video filter "Mirror", but there's nothing in Skype or other chat clients that would mirror it for me without mirroring it for the chattee, like you said.  This is just shooting in the dark, but it sounds like a driver issue (and that they've improved it since Ubuntu 10.04 :) ).  So, maybe there's an option in the driver(s) to flip the image shown to yourself without flipping the image that's sent to chat.  It's probably the uvcvideo driver, but check for sure by opening a Terminal and, as your non-root user, type in:

```
dmesg|grep -iC3 webcam
```Or, in place of 'webcam', use the name that you know your camera is called by programs.  That should give you the name of the module/driver used with your webcam.  Once you get that, use modinfo to get more technical information of that driver, including available options you may be able to use with it.

```
lsmod |grep <name of module you found in dmesg>
```Will list all associated modules loaded with your webcam's module.  One could be dependent on the other, and any of these may have options you can access and load explicitly.  With each of these modules, run modinfo:

```
modinfo <name of module you found in dmesg>
modinfo <associated module in lsmod>

```The lines you want are usually at the bottom of the description, beginning with "parm:"

If you find anything on your system, please Google more about it before making changes to the drivers, because I'm still shooting in the dark on this!  None of the preceding commands change anything on your system; they're just for gathering information.

---

### Post by wjkraymond on 2011-05-31
hi there, thanks for replying :-)

I tried the cheese program as well. like you said, it can make a mirror image, but my chattee will see my image as an mirror image as well, which is not cool. meaning if i hold a book in front of the webcam, i read it in mirror mode, but so does my chattee.

The ideal case i'm hoping is, i hold a book in front of webcam, i see a mirror image, while my chattee sees it normally. 

Anyway, i tried to input your codes into my terminal, the first command yields nothing, while the 2nd command yields some kind of error. i'll paste them bellow.

```
raymond@raymond-K42JY:~$ dmesg|grep -iC3 webcam
raymond@raymond-K42JY:~$ lsmod |grep <name of module you found in dmesg>
bash: syntax error near unexpected token `newline'

```

The first command suppose to yield the name of my webcam?
but it shows nothing.

in skype option, at the part where i need to choose the webcam input, the name of the webcam seems to be "/dev/video0"

i tried putting this into the command, but it yields nothing as well.

I know this issue is not a big deal, but it can get annoying at times. i hope the next version of ubuntu will have a fix for this.

---

### Post by silentstone on 2011-06-01
Okay, first, the good news:  I checked around a bit, and reportedly, one chat client called **Kopete** provides a 'mirror preview' video option.  Kopete is the default multi-protocol chat client for KDE, so you'll have it on your system already if KDE is installed.  I found it on **Lucid Lynx** this way: 
```
mute@mouse:~/sysadmin$ apt-cache search kopete
kopete-message-indicator - Kopete plugin for Message Indicator
ichthux-emoticons - Christian emoticons for Kopete
kepas - KDE Easy Publish and Share - Tray icon
kopete-plugin-thinklight - thinkpad flashing for kopete
plasma-runner-kopete - Start chat with your Kopete contacts using KRunner
plasma-widget-kepas - KDE Easy Publish and Share - Plasmoid
kopete - instant messenger for KDE 4
libkopete-dev - development files for the KDE 4 networking module
libkopete4 - main Kopete library
kdeartwork-emoticons - emoticon collections for KDE 4 chat clients
kopete-cryptography - OpenPGP plugin for Kopete
kopete-plugin-otr-kde4 - Transitional package
mute@mouse:~/sysadmin$ apt-cache show kopete
Package: kopete
Priority: optional
Section: kde
Installed-Size: 17560
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdenetwork
Version: 4:4.4.5-0ubuntu1.1
Replaces: kget (<< 4:4.2.0-0ubuntu2), kopete-kde4, kopete-otr
Depends: kdebase-runtime (>= 4:4.4.5), kdelibs5 (>= 4:4.4.5), kdepimlibs5 (>= 4:4.4.5), libc6 (>= 2.4), libgadu3 (>= 1:1.8.0+r592), libgif4 (>= 4.1.4), libglib2.0-0 (>= 2.12.0), libidn11 (>= 1.13), libkopete4 (>= 4:4.4.5), libmeanwhile1 (>= 1.0.2), libmsn0.3 (>= 4.0), libotr2 (>= 3.2.0), libphonon4 (>= 4:4.2.0), libqca2, libqimageblitz4, libqt4-dbus (>= 4:4.5.3), libqt4-network (>= 4:4.5.3), libqt4-qt3support (>= 4:4.5.3), libqt4-sql (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.6.1), libqtgui4 (>= 4:4.5.3), libstdc++6 (>= 4.4.0), libv4l-0 (>= 0.5.0), libx11-6 (>= 0), libxml2 (>= 2.7.4), libxslt1.1 (>= 1.1.18), phonon (>= 4:4.5.2), zlib1g (>= 1:1.1.4)
Recommends: libqca2-plugin-ossl, libqt4-sql-sqlite, kopete-message-indicator
Suggests: kdeartwork-emoticons, khelpcenter
Conflicts: kopete-kde4, kopete-otr
Filename: pool/main/k/kdenetwork/kopete_4.4.5-0ubuntu1.1_i386.deb
Size: 5182654
MD5sum: 201f8eac3ffdccafb3eab3a5b6da5e17
SHA1: b8d170d5bc8d427fa827cba10e306d768b0ef129
SHA256: 88c857b8339ea67e5c58282b7f1c090cb4955dc84ef3e5b7c100909f2911b18d
Description: instant messenger for KDE 4
 Kopete is an instant messaging and chat application with support for a wide
 variety of services, such as AIM, Yahoo, ICQ, MSN, IRC, and Jabber.  Advanced
 features and additional protocols are available as plugins.
 .
 This package is part of the KDE 4 networking module.
Homepage: http://www.kde.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: kubuntu-desktop, kubuntu-netbook, edubuntu-desktop-kde


```It looks like you can install it with or without the entire KDE desktop suite of software in Lucid!  This won't help with Skype, though.  If you want to continue poking at that...

Now, the code I suggested you run previously, *dmesg|grep -iC3 webcam*, and all subsequent commands failed because your webcam isn't being identified with the word 'webcam' in your system for whatever reason.  So, another way to isolate the webcam driver is to list all of the drivers loaded on your system.  By the way, I don't recall you mentioning if your webcam is internal or external.  Regardless, ensure that the webcam is plugged in, open up **Cheese** or **Guvcview** to make sure the webcam is turned on, and then run the following command in a virtual terminal:
```

lsmod
```and post the output.  *lsmod* lists all currently loaded drivers.

---

### Post by wjkraymond on 2011-06-01
opps, its an internal (built-in) webcam.
sorry about that, i thought its obvious, couldn't think of any laptops without webcam these day, i assumed it was obvious :-p
my bad~

---

### Post by JasonGriffee on 2011-06-18
I have a ASUS K50-IJ Laptop. When using my webcam (internal), with Skype it displays the image upside down. Does anyone know of a fix for this?

---

### Post by silentstone on 2011-06-20
Here is some information on the UVC class of webcams and Linux drivers:
[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

Regarding the "upside down" problem...there's a footnote about that problem on cameras on several Asus and Fujitsu notebooks (on that webpage).

Trying to get more info on the hardware for your system, commands like **lsmod**, **lspci**, **lsusb**, **lshw**, **dmesg|grep -i error**, and **dmesg|grep -i warning** can help you identify, pinpoint system messages and provide more material to forum-denizens who would like to help.  :D

---

