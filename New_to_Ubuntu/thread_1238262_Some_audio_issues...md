---
title: "Some audio issues.."
date: 2009-08-12
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2009-08-12
Okay.. so I have a few audio issues which are all solvable, but seem to keep occurring and are really beginning to annoy me. 

First of all, every time I boot up Ubuntu my master volume is muted in Ubuntu. I can unmute it and listen to music, but as soon as I restart it would be muted again.. it's kind of annoying having to keep unmuting it. 

Secondly.. I also have a bit of a skype audio issue, although it affects my audio overall too. Basicly, whenever I'm in skype my audio switches itself off everywhere else.. for example in my music players, in youtube etc.. and if I try to play something in youtube, firefox usually stops responding. 

So... any ideas what's causing these problems? 

Thanks for any help in advance.

---

### Post by kansasnoob on 2009-08-12
Hmmmm, I thought that problem was fixed some time ago with update of alsa-utils (1.0.18-1ubuntu11).

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430)

Would you please post the output from terminal of this command:

```
apt-cache showpkg alsa-utils
```

---

### Post by MrJoeyUK on 2009-08-12
```
joe@joe-laptop:~$ apt-cache showpkg alsa-utils
Package: alsa-utils
Versions: 
1.0.18-1ubuntu11 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: 2a345a7654275a3c84c972e730569513


Reverse Depends: 
  xubuntu-desktop,alsa-utils
  xchat,alsa-utils
  ubuntustudio-desktop,alsa-utils
  ubuntu-netbook-remix,alsa-utils
  ubuntu-mid,alsa-utils
  randomsound,alsa-utils
  kvdr,alsa-utils
  isdnvboxclient,alsa-utils
  gworkspace-apps-wrappers,alsa-utils
  gmusicbrowser,alsa-utils
  eeepc-acpi-scripts,alsa-utils
  asoundconf-gtk,alsa-utils
  amsn,alsa-utils
  ubuntu-desktop,alsa-utils
  ltsp-client,alsa-utils
  kubuntu-desktop,alsa-utils
  gdm,alsa-utils
  alsa-base,alsa-utils 1.0.9a-4
  alsa-base,alsa-utils
Dependencies: 
1.0.18-1ubuntu11 - libasound2 (4 1.0.18) libc6 (2 2.4) libncurses5 (2 5.6+20071006-3) whiptail (16 (null)) dialog (0 (null)) module-init-tools (0 (null)) python (0 (null)) lsb-base (2 3.0-9) linux-sound-base (2 1.0.15-1) alsa-base (2 1.0.15-1) pciutils (0 (null)) alsa-base (3 1.0.9b-3) udev (3 0.060) udev (3 136-1) 
Provides: 
1.0.18-1ubuntu11 - audio-mixer 
Reverse Provides: 
```

---

### Post by kansasnoob on 2009-08-12
That looks fine.

I had completely forgotten that I have Luke Yelavich's PPA installed in my Jaunty until reading to the bottom of this:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)

Here's his PPA info:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

Also it may be necessary to follow Part A of this tutorial after updating with that PPA:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

The only time I have trouble with "muting" on restart now is if I'm using Martin Pitt's 'gnome-stracciatella-session' for testing purposes:

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

---

