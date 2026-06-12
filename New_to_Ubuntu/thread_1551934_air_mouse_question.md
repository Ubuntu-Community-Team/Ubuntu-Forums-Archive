---
title: "air mouse question"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-08-12
does anyone know how to get the air mouse iphone app to work with ubuntu?

---

### Post by scorp123 on 2010-08-13
> **ornothaloapq said:**
> does anyone know how to get the air mouse iphone app to work with ubuntu?

I doubt you can do that. The best thing you can do is go to the [http://www.mobileairmouse.com](http://www.mobileairmouse.com) web site, their forum and their Facebook page and ask them to produce a Linux version. If enough people keep asking about Linux support chances are they will wake up and really produce one.

In the meantime you could use this: RemotePad. This program is free but by far does not even remotely have the same features like AirMouse ... but at least it will work with Linux. Just like with "AirMouse" you need the iPhone program and the PC-side server program. The iPhone program is available from the iTunes AppStore and you should be able to find it via the "AppStore" application on your iPhone. Here is the direct link (e.g. for Safari on your iPhone):

[http://itunes.apple.com/WebObjects/MZStore.woa/wa/viewSoftware?id=291741057&mt=8](http://itunes.apple.com/WebObjects/MZStore.woa/wa/viewSoftware?id=291741057&mt=8)

The PC side can be downloaded from here:

[http://www.tenjin.org/RemotePad/](http://www.tenjin.org/RemotePad/)

The Linux version unfortunately needs to be compiled from source code. I did that myself a while back and I still have the *.deb packages. You can try my packages if you want ... not sure if they will work with Ubuntu 10.04 though. When I compiled those packages I was still using Ubuntu 9.10 ... if there were no drastic changes then they should work OK.

Source code (should be the same package as from the tenjin.org web site ... as I am not a programmer I definitely didn't change or modify anything):
[http://dl.dropbox.com/u/1614648/RemotePad_iPhone/remotepadserver-1.10-X11-Source.tgz](http://dl.dropbox.com/u/1614648/RemotePad_iPhone/remotepadserver-1.10-X11-Source.tgz)

Debian/Ubuntu installation package for 32-bit (i386) OS:
[http://dl.dropbox.com/u/1614648/RemotePad_iPhone/remotepad-server_1.10-1_i386.deb](http://dl.dropbox.com/u/1614648/RemotePad_iPhone/remotepad-server_1.10-1_i386.deb)

Debian/Ubuntu installation package for 64-bit OS:
[http://dl.dropbox.com/u/1614648/RemotePad_iPhone/remotepad-server_1.10-1_amd64.deb](http://dl.dropbox.com/u/1614648/RemotePad_iPhone/remotepad-server_1.10-1_amd64.deb)


Hope this helps? :)

---

### Post by scorp123 on 2011-07-12
EPIC BUMP!!

they have released a Linux version ... and it's for Ubuntu too! 32-bit only for the moment it seems ... but oh well, I am not complaining.

this is epic :D

So there _IS_ a big enough userbase or why would they produce a version for our OS? :)

[http://mobilemouse.com/](http://mobilemouse.com/)

Direct link to the *.deb file:

[http://sourceforge.net/projects/mmlinuxserver/files/mmlinuxserver-1.0.0-lucid-i686.deb/download](http://sourceforge.net/projects/mmlinuxserver/files/mmlinuxserver-1.0.0-lucid-i686.deb/download)

---

### Post by scorp123 on 2011-07-20
BUMP:

For anyone who is interested and who might find this thread via Google:

There is an alternative for "Mobile*AirMouse". It's called HippoRemote and you will easily find it in Apple's AppStore. The cool thing is this:*the only thing you need on the Linux side to make this work is a VNC*server, e.g. "vino" (for GNOME)*or "krfb" (for KDE) or any other VNC-type server that is available for Linux (e.g. tightvnc-server, vnc4server, etc.)

Here are the instructions to get it working:
[http://www.hackourlife.com/free-cross-platform-mobile-air-mouse-for-linux-using-iphone-or-ipod-touch/](http://www.hackourlife.com/free-cross-platform-mobile-air-mouse-for-linux-using-iphone-or-ipod-touch/)

I just tried it and it works tip top!

So if anyone out there is searching for a Linux alternative for "Mobile AirMouse"*(especially if you're on 64-bit Linux, as right now their official *.deb file is 32-bit only!) you should give "Hippo Remote"*and the instructions above a try :)

I hope this post may be useful for someone out there... :)

---

### Post by hayhursm on 2011-07-22
> **scorp123 said:**
> EPIC BUMP!!

they have released a Linux version ... and it's for Ubuntu too! 32-bit only for the moment it seems ... but oh well, I am not complaining.

this is epic :D

So there _IS_ a big enough userbase or why would they produce a version for our OS? :)

[http://mobilemouse.com/](http://mobilemouse.com/)

Direct link to the *.deb file:

[http://sourceforge.net/projects/mmlinuxserver/files/mmlinuxserver-1.0.0-lucid-i686.deb/download](http://sourceforge.net/projects/mmlinuxserver/files/mmlinuxserver-1.0.0-lucid-i686.deb/download)


Hello, I'm not trying to hijack here but I was so thrilled about Mobile Mouse for Ubuntu that I decided to install the **mmlinuxserver-1.0.0-lucid-i686.deb** package on Lucid x64 by using the command: **sudo dpkg -i --force-architecture mmlinuxserver-1.0.0-lucid-i686.deb**.  Everything installed fine (all dependencies were met) but when I issue the command: **mmserver** (which I assume is the correct command to start the server bc there is no documentation) in the terminal I get: **mmserver: error while loading shared libraries: libpcrecpp.so.0: cannot open shared object file: No such file or directory**.  Not sure if this is a result of using the **--force-architecture** option but it appears I just need a symbolic link?  Any ideas on what I might need to do?  Any help is always appreciated!

---

### Post by hayhursm on 2011-08-01
Bump

---

### Post by mwahal on 2012-10-01
I compiled the program on 12.04 i386 from the source. Only keyboard works fine, any mouse movements gives error messages such as

mmserver[13475]: [192.168.123.11] unhandled packet: size(27)

---

### Post by oldos2er on 2012-10-01
Old thread closed.

---

