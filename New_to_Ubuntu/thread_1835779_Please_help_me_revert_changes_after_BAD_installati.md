---
title: "Please help me revert changes after BAD installation"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by kingtz on 2011-08-29
Please help. I accidentally installed a 32bit app on my 64-bit 11.04 Ubuntu, and I'm now having a bunch of UI issues. I'm new to Ubuntu. 

What I tried to install: [WALLCH]("http://www.omgubuntu.co.uk/2011/08/wallch-wallpaper-changer-adds-unity-features/")

I didn't see until the very end of the article (after I had begun installing) that it wasn't compatible with the 64-bit Ubuntu. 

This is the README from the downloaded folder:
> Wallch (Wallpaper Changer)
by Alex Solanos(alexsol.developer@gmail.com) and Leon Vytanos(leon.check.me@gmail.com)

SEE COPYING FILE FOR LICENSE INFO PLEASE!

To build the program you'll need:
debhelper (>= 8), libqt4-dev, libnotifymm-dev, libhighgui-dev, qt4-qmake, desktop-file-utils

The program requires:
imagemagick, mpg321, libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libhighgui2.1, libnotify4 (>= 0.7.0), libqt4-dbus (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.6.2), libstdc++6 (>= 4.4.0)

You have to install all of them if you want to install Wallch through this tarball.

To install:
        qmake *.pro
	sudo make install

To unistall:
	sudo ./uninstall

To execute through terminal:
	wallch


You'll may find helpful info at Help->Contents at the Menu of Wallch or 'man wallch'.
ENJOY

I got as far as "qmake *.pro" in terminal.
It started downloading a bunch of packages and then kept going for quite a while. 

Afterwards, Ubuntu wasn't quite frozen, but I couldn't click on anything. I tried SUPER+S to see my screens and it worked, but was then stuck there. I couldn't pick any of the screens. 

I rebooted, and it seemed to be ok, until I opened something, then I lost my cursor and couldn't click or switch to anything.

Everything, however, seems fine when I log into Ubuntu Classic. 

So, yeah, could anyone please walk me through how I can go about reverting these changes or even restoring my OS to the state it was before I started installing those packages?

Thanks in advance.





P.S. I came across the command: 
```
sudo apt-get remove --purge packagename

```

If I can use this, what should I put for "packagename"? Otherwise, what can I do?

---

### Post by lkjoel on 2011-08-29
> ...
To uninstall:
	sudo ./uninstall
...
Did you miss that part, or did it not work?

---

### Post by kingtz on 2011-08-29
> **lkjoel said:**
> Did you miss that part, or did it not work?

I tried it, and this is what I got:
```
user@user-W860CU:~$ sudo ./uninstall
[sudo] password for user: 
sudo: ./uninstall: command not found

```

I tried it earlier while logged in Ubuntu Classic, so could that have been an issue? i.e. should I have been in the regular Ubuntu with which I was experiencing the issues?

---

### Post by lkjoel on 2011-08-29
Sorry, I wasn't clear! Could you go to the downloaded folder (for wallch), and run the uninstall script?

---

### Post by kingtz on 2011-08-29
> **lkjoel said:**
> Sorry, I wasn't clear! Could you go to the downloaded folder (for wallch), and run the uninstall script?

That seemed to have worked! I am now in the regular Ubuntu and everything seems to be back to normal. I shall play around with this some more to see if there are any residual issues, but I guess this issue has been solved for now.

Just to confirm, when I did that first command to install the packages, it seems like a whole lot of stuff was getting downloaded and installed. Would that single uninstall command have really removed all of that? I just don't want random stuff installed that I won't be using/needing.


Thanks so much for your help!

---

### Post by lkjoel on 2011-08-29
I don't really think that it did remove the packages.
I can help you remove them if you want.

Could you attach the file: /var/log/apt/history.log
And could you tell me approximately when you started installing it?

---

### Post by kingtz on 2011-08-30
> **lkjoel said:**
> I don't really think that it did remove the packages.
I can help you remove them if you want.

Could you attach the file: /var/log/apt/history.log
And could you tell me approximately when you started installing it?


I keep getting an "upload error" stating that it's an invalid file, so I just copied it to here:

[QUOTE=history.log]Start-Date: 2011-08-29  01:52:55
Commandline: apt-get install qt3-dev-tools
Install: libsm-dev:amd64 (1.2.0-1ubuntu1, automatic), libice-dev:amd64 (1.0.7-1ubuntu1, automatic), libxrandr-dev:amd64 (1.3.1-1ubuntu1, automatic), libexpat1-dev:amd64 (2.0.1-7ubuntu3, automatic), libpthread-stubs0:amd64 (0.3-2, automatic), libgpg-error-dev:amd64 (1.10-0.2ubuntu1, automatic), comerr-dev:amd64 (2.1-1.41.14-1ubuntu3, automatic), libxfixes-dev:amd64 (4.0.5-1ubuntu1, automatic), libqt3-headers:amd64 (3.3.8-b-7ubuntu3, automatic), libgl1-mesa-dev:amd64 (7.10.2-0ubuntu2, automatic), x11proto-xinerama-dev:amd64 (1.2.1-1, automatic), x11proto-render-dev:amd64 (0.11.1-1, automatic), libxi-dev:amd64 (1.4.1-1ubuntu2, automatic), libkrb5-dev:amd64 (1.8.3+dfsg-5ubuntu2.1, automatic), libfontconfig1-dev:amd64 (2.8.0-2.1ubuntu3, automatic), liblcms1-dev:amd64 (1.18.dfsg-1.2ubuntu1, automatic), x11proto-kb-dev:amd64 (1.0.5-1, automatic), x11proto-randr-dev:amd64 (1.4.0+git20101207.0d32bb07-0ubuntu1, automatic), libxinerama-dev:amd64 (1.1.1-1ubuntu1, automatic), libgssrpc4:amd64 (1.8.3+dfsg-5ubuntu2.1, automatic), mesa-common-dev:amd64 (7.10.2-0ubuntu2, automatic), xtrans-dev:amd64 (1.2.6-1, automatic), x11proto-input-dev:amd64 (2.0.1-1ubuntu1, automatic), x11proto-fixes-dev:amd64 (4.1.2-1, automatic), libglu1-mesa-dev:amd64 (7.10.2-0ubuntu2, automatic), libdrm-dev:amd64 (2.4.23-1ubuntu6, automatic), x11proto-xext-dev:amd64 (7.1.99.0~git20110111.9df8b776-0ubuntu2, automatic), libxt-dev:amd64 (1.0.9-1ubuntu1, automatic), libxmu-dev:amd64 (1.1.0-1, automatic), libxext-dev:amd64 (1.2.0-2ubuntu1, automatic), libtasn1-3-dev:amd64 (2.7-1ubuntu1, automatic), zlib1g-dev:amd64 (1.2.3.4.dfsg-3ubuntu3, automatic), libcups2-dev:amd64 (1.4.6-5ubuntu1.3, automatic), libqt3-compat-headers:amd64 (3.3.8-b-7ubuntu3, automatic), libfreetype6-dev:amd64 (2.4.4-1ubuntu2.1, automatic), qt3-dev-tools:amd64 (3.3.8-b-7ubuntu3), libxau-dev:amd64 (1.0.6-1ubuntu1, automatic), libgcrypt11-dev:amd64 (1.4.6-4ubuntu2, automatic), libkadm5clnt-mit7:amd64 (1.8.3+dfsg-5ubuntu2.1, automatic), libaudio-dev:amd64 (1.9.2-4ubuntu1, automatic), libkadm5srv-mit7:amd64 (1.8.3+dfsg-5ubuntu2.1, automatic), libxmu-headers:amd64 (1.1.0-1, automatic), libxrender-dev:amd64 (0.9.6-1ubuntu1, automatic), xorg-sgml-doctools:amd64 (1.6-1, automatic), libxft-dev:amd64 (2.2.0-2ubuntu2, automatic), libx11-dev:amd64 (1.4.2-1ubuntu3, automatic), libkdb5-4:amd64 (1.8.3+dfsg-5ubuntu2.1, automatic), libqt3-mt:amd64 (3.3.8-b-7ubuntu3, automatic), libgnutls-dev:amd64 (2.8.6-1ubuntu2, automatic), libkms1:amd64 (2.4.23-1ubuntu6, automatic), libqt3-mt-dev:amd64 (3.3.8-b-7ubuntu3, automatic), krb5-multidev:amd64 (1.8.3+dfsg-5ubuntu2.1, automatic), libmng-dev:amd64 (1.0.10-1, automatic), libxcb1-dev:amd64 (1.7-2ubuntu2, automatic), libjpeg62-dev:amd64 (6b1-1ubuntu1, automatic), x11proto-core-dev:amd64 (7.0.20-1, automatic), libxdmcp-dev:amd64 (1.1.0-1ubuntu1, automatic), libpthread-stubs0-dev:amd64 (0.3-2, automatic), libxcursor-dev:amd64 (1.1.11-1ubuntu1, automatic), libpng12-dev:amd64 (1.2.44-1ubuntu3.1, automatic)
End-Date: 2011-08-29  01:54:05[/QUOTE]

---

### Post by lkjoel on 2011-08-30
Not sure if this will work, but if you really want to remove those packages, try this:
```
sudo apt-get purge libsm-dev:amd64 libice-dev:amd64 libxrandr-dev:amd64 libexpat1-dev:amd64 libpthread-stubs0:amd64 libgpg-error-dev:amd64 comerr-dev:amd64 libxfixes-dev:amd64 libqt3-headers:amd64 libgl1-mesa-dev:amd64 x11proto-xinerama-dev:amd64 x11proto-render-dev:amd64 libxi-dev:amd64 libkrb5-dev:amd64 libfontconfig1-dev:amd64 liblcms1-dev:amd64 x11proto-kb-dev:amd64 x11proto-randr-dev:amd64 libxinerama-dev:amd64 libgssrpc4:amd64 mesa-common-dev:amd64 xtrans-dev:amd64 x11proto-input-dev:amd64 x11proto-fixes-dev:amd64 libglu1-mesa-dev:amd64 libdrm-dev:amd64 x11proto-xext-dev:amd64 libxt-dev:amd64 libxmu-dev:amd64 libxext-dev:amd64 libtasn1-3-dev:amd64 zlib1g-dev:amd64 libcups2-dev:amd64 libqt3-compat-headers:amd64 libfreetype6-dev:amd64 qt3-dev-tools:amd64 libxau-dev:amd64 libgcrypt11-dev:amd64 libkadm5clnt-mit7:amd64 libaudio-dev:amd64 libkadm5srv-mit7:amd64 libxmu-headers:amd64 libxrender-dev:amd64 xorg-sgml-doctools:amd64 libxft-dev:amd64 libx11-dev:amd64 libkdb5-4:amd64 libqt3-mt:amd64 libgnutls-dev:amd64 libkms1:amd64 libqt3-mt-dev:amd64 krb5-multidev:amd64 libmng-dev:amd64 libxcb1-dev:amd64 libjpeg62-dev:amd64 x11proto-core-dev:amd64 libxdmcp-dev:amd64 libpthread-stubs0-dev:amd64 libxcursor-dev:amd64 libpng12-dev:amd64

```

---

### Post by kingtz on 2011-08-30
> **lkjoel said:**
> Not sure if this will work, but if you really want to remove those packages, try this:
```
sudo apt-get purge libsm-dev:amd64 libice-dev:amd64 libxrandr-dev:amd64 libexpat1-dev:amd64 libpthread-stubs0:amd64 libgpg-error-dev:amd64 comerr-dev:amd64 libxfixes-dev:amd64 libqt3-headers:amd64 libgl1-mesa-dev:amd64 x11proto-xinerama-dev:amd64 x11proto-render-dev:amd64 libxi-dev:amd64 libkrb5-dev:amd64 libfontconfig1-dev:amd64 liblcms1-dev:amd64 x11proto-kb-dev:amd64 x11proto-randr-dev:amd64 libxinerama-dev:amd64 libgssrpc4:amd64 mesa-common-dev:amd64 xtrans-dev:amd64 x11proto-input-dev:amd64 x11proto-fixes-dev:amd64 libglu1-mesa-dev:amd64 libdrm-dev:amd64 x11proto-xext-dev:amd64 libxt-dev:amd64 libxmu-dev:amd64 libxext-dev:amd64 libtasn1-3-dev:amd64 zlib1g-dev:amd64 libcups2-dev:amd64 libqt3-compat-headers:amd64 libfreetype6-dev:amd64 qt3-dev-tools:amd64 libxau-dev:amd64 libgcrypt11-dev:amd64 libkadm5clnt-mit7:amd64 libaudio-dev:amd64 libkadm5srv-mit7:amd64 libxmu-headers:amd64 libxrender-dev:amd64 xorg-sgml-doctools:amd64 libxft-dev:amd64 libx11-dev:amd64 libkdb5-4:amd64 libqt3-mt:amd64 libgnutls-dev:amd64 libkms1:amd64 libqt3-mt-dev:amd64 krb5-multidev:amd64 libmng-dev:amd64 libxcb1-dev:amd64 libjpeg62-dev:amd64 x11proto-core-dev:amd64 libxdmcp-dev:amd64 libpthread-stubs0-dev:amd64 libxcursor-dev:amd64 libpng12-dev:amd64

```

Thank you! According to terminal, all of that stuff was removed. :)

---

### Post by lkjoel on 2011-08-30
Great! Could you mark this thread as solved? (Thread Tools->Mark this thread as solved)

---

### Post by bodhi.zazen on 2011-08-30
Although I posted it in another thread, [This post](http://ubuntuforums.org/showpost.php?p=11202190&postcount=9) applies here as well.

---

