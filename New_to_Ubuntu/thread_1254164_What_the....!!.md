---
title: "What the....?!!"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by humphreybc on 2009-08-31
Hi there,

So I just installed Ubuntu 9.04 onto a friends desktop Acer Aspire SA80 computer because his Windows XP was running ridiculously slow so I suggested Ubuntu for him. I have used ndiswrapper with the Windows XP drivers for his Asus WL-138G R1.22 inbuilt PCI wireless card, and it seems to work as it picks up the signal, connects and will browse a page or two... this is where things get nasty.

I tried browsing the internet for a bit and after loading google and then navigating to another site, the network will drop but the icon still says it's connected. When I go to click on the icon to reconnect, it freezes all of ubuntu, ctrl+alt+F2 works, I login, but when I type a command (such as 'top' or 'sudo reboot') nothing will happen... the cursor just flickers on the next line.

So I rebooted the computer using the button, and then when I logged back in I tried to update apt-get in the terminal - once again, it hits about two dozen times and then it'll get stuck on one, stop responding, same as above.

In short - it seems somehow ndiswrapper/network manager or something is locking up either the X server or the kernel itself. I'm taking it home to plug into our ethernet so I can update it to see if that works, but any ideas why this could be happening?

It's a pain in the *** after I've been touting how good Ubuntu is and now it freezes whenever one tries to do anything with the network....


Help!

---

### Post by hal10000 on 2009-08-31
First we have to know something more about the card. So, you should use the following two commands (in a terminal window)  to get some info.
1.) [COLOR="Red"]lspci[/COLOR]
2.) [COLOR="Red"]lspci -n[/COLOR]

Post the output here, so we can determine the chipset (I suppose it' a broadcom driver). With a little luck we can get it work without ndiswrapper.

---

### Post by humphreybc on 2009-08-31
Hi, 

thanks for replying. I had managed to get the drivers working properly with ndiswrapper after reinstalling it and finding some other drivers. They worked well and were reliable, so I installed some programs, including AWN dock etc for my friend and set up his ubuntu so it'll be nice for him. Then I restarted the computer, and everything went to hell - after logging in takes an unusual amount of time to load the desktop, then when it does the network manager icon does not appear in the notification tray - there is just a blank space. AWN loads properly, but then as soon as I click anywhere the system freezes up completely, and even ctrl+alt+F2 "sudo reboot" does nothing - no commands work in virtual terminal or in the GUI. I have to hard reset - this happens everytime I boot up now.

I'm trying to fix it using the liveCD but i'm not sure how. Please advise.

---

### Post by Liolikas on 2009-08-31
>...so I installed some programs...
How? I question this because ppl find so many strange ways to install programs, that may be your problem too.

---

### Post by wojox on 2009-08-31
Here's the Acer help section:

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=Acer+Aspire&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=Acer+Aspire&sa=Search)

---

### Post by humphreybc on 2009-08-31
All of the applications were installed through repositories, apart from two - Skype and Google Earth, which were downloaded from the websites. Skype was a .deb package and I doubt that's the problem, but Google Earth was installed following these instructions: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

A note: After installing Google Earth, it didn't work well with the desktop effects, so I uninstalled it using the instructions on that same page - maybe it removed something it shouldn't have?

I'm typing this from the problem computer using the LiveCD - here is the .xsession-errors file:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_NZ.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Failure: Timeout
GNOME_KEYRING_SOCKET=/tmp/keyring-4s2Jsi/socket
SSH_AUTH_SOCK=/tmp/keyring-4s2Jsi/socket.ssh

(gnome-settings-daemon:2876): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2876): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
** (gnome-panel:2944): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2944): DEBUG: Adding applet 0.
I/O warning : failed to load external entity "/home/cam/.compiz/session/1040d01d20316c8263125170825729996600000026500020"
Starting gtk-window-decorator

(gnome-panel:2944): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:2944): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:2944): DEBUG: Adding applet 1.

** (nautilus:2945): WARNING **: Unable to add monitor: Not supported
** (gnome-panel:2944): DEBUG: Adding applet 2.

(awn-applets-migration:2996): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/skype.desktop
LOADED : /usr/share/applications/brasero-nautilus.desktop
LOADED : /usr/share/applications/rhythmbox.desktop
LOADED : /usr/share/applications/totem.desktop
LOADED : /usr/share/applications/openoffice.org-writer.desktop
LOADED : /usr/share/applications/f-spot.desktop
LOADED : /usr/share/applications/gcalctool.desktop
LOADED : /usr/share/applications/gnome-dictionary.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop

** (nm-applet:2963): WARNING **: _nm_object_get_property: Error getting 'WirelessHardwareEnabled' for /org/freedesktop/NetworkManager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Timeout

Failed to play sound: IO error
evolution-alarm-notify-Message: Setting timeout for 54908 1251763200 1251708292
evolution-alarm-notify-Message:  Tue Sep  1 12:00:00 2009

evolution-alarm-notify-Message:  Mon Aug 31 20:44:52 2009


** (nm-applet:2963): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


** (nm-applet:2963): WARNING **: nm_client_get_devices: error getting devices: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


** (nm-applet:2963): WARNING **: _nm_object_get_property: Error getting 'ActiveConnections' for /org/freedesktop/NetworkManager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

It mentions two problems - AWN with compositing on shutdown, and the network manager. How can I solve these problems using the liveCD?

---

### Post by Liolikas on 2009-08-31
You have:
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/384439](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/384439)
Looks like it can not be helped in simple way. Subscribe to this page. 
All you can do is try compile other versions.

---

### Post by humphreybc on 2009-08-31
So that's it, I can't do anything about it? Do I have to reinstall Ubuntu?

---

### Post by Liolikas on 2009-08-31
But I am not sure if that bug created this all you describe...
a) wait until update will appear.
b) create even bigger mess get other gnome-settings-daemon not 2.27.1, or remove it (waa crazy).
c) try kubuntu (xubuntu) (they do not have gnome-* things at all).
...

---

### Post by humphreybc on 2009-08-31
I think I'll do a quick re-format and re-install and see if I can just get the wireless working with ndiswrapper and not worry about the fancy dock etc

Bloody pain in the ***, i've been at this all night!

---

### Post by humphreybc on 2009-08-31
I think I'll do a quick re-format and re-install and see if I can just get the wireless working with ndiswrapper and not worry about the fancy dock etc

Bloody pain in the ***, i've been at this all night!

---

### Post by Liolikas on 2009-08-31
Yes: good idea. 
Sleep first. ;)

---

### Post by humphreybc on 2009-08-31
Well I just did a fresh re-install and everything was going great, updated everything, installed ndiswrapper with the wireless drivers etc etc, it all worked fine... until I rebooted after I installed the ndiswrapper drivers and then same problem as before, it takes forever to load the desktop after login, then the panel will look all weird, nothing works except desktop icons for a few seconds before nautilus locks up and they disappear.... it's completely useless.

---

### Post by zipperback on 2009-08-31
I have an ACER Apsire laptop and I don't need ndiswrapper for wifi.

Please post the output of the following command.

```

lspci

```

If you have the same chipset as my acer aspire, I can help you get the wifi running correctly and then we can help you get the other stuff taken care of.

- zipperback
:popcorn:

---

### Post by matthewbpt on 2009-08-31
It sounds like ndiswrapper is causing the problems. If you post exactly what wireless card he has witch lspci we might be able to see if it can work without ndiswrapper.

---

### Post by humphreybc on 2009-08-31
The wireless card is an Asus WL-138G R1.22 PCI card with a Marvell W8300 chipset. I highly doubt your laptop will have the same wireless card as this desktop.

@matthewbpt - yes it seems that ndiswrapper is definitely causing the computer to choke as everything seemed fine before I installed it with the drivers from the ndiswrapper sourceforge website. When using just "eth0" to update ubuntu etc, it was running fine. If there was a way to use the wireless card without using ndiswrapper, that'd be splendid.

Thanks

---

### Post by hal10000 on 2009-08-31
If you don't post the outputs of [COLOR="Red"]lspci[/COLOR] and [COLOR="Red"]lspci -n[/COLOR] commands we can't help!!!!!

---

### Post by humphreybc on 2009-08-31
> **hal10000 said:**
> If you don't post the outputs of [COLOR="Red"]lspci[/COLOR] and [COLOR="Red"]lspci -n[/COLOR] commands we can't help!!!!!

I would post the outputs but as soon as I login to the computer it freezes up and nothing works. Ideas? Could I somehow post them using the liveCD? Or can I login to Ubuntu virtual terminal without even starting the X server?

I'll have another look tomorrow, it's midnight here so bed time!

---

### Post by matthewbpt on 2009-08-31
In this site [http://www.atlink.it/~conti/articles/asus-wl-138g-54mbps-and-linux/](http://www.atlink.it/~conti/articles/asus-wl-138g-54mbps-and-linux/) it says the included drivers with the card don't play well with ndiswrapper and gives a link to a different driver for the card. Maybe this will help, unless of course you are already using the different driver this guy is refering to.

---

### Post by hal10000 on 2009-08-31
> Could I somehow post them using the liveCD?

Yes you can.

---

### Post by humphreybc on 2009-08-31
> **matthewbpt said:**
> In this site [http://www.atlink.it/~conti/articles/asus-wl-138g-54mbps-and-linux/](http://www.atlink.it/~conti/articles/asus-wl-138g-54mbps-and-linux/) it says the included drivers with the card don't play well with ndiswrapper and gives a link to a different driver for the card. Maybe this will help, unless of course you are already using the different driver this guy is refering to.

Thanks for that, but yes, that is the exact driver I have been using with still no luck. What I have not tried is the Windows 98 drivers which is what he is using... I've been using the XP drivers.

@ hal10000:

Okay that's great... maybe you could tell me *how* I could go about doing that, or at least link to somewhere that does?

---

### Post by matthewbpt on 2009-08-31
> **humphreybc said:**
> 
@ hal10000:

Okay that's great... maybe you could tell me *how* I could go about doing that, or at least link to somewhere that does?

Just simply boot the live cd and run and commands 'lspci' and 'lspci -n' from the live cd.

---

### Post by hal10000 on 2009-08-31
You have to open a terminal window to run the commands.

---

### Post by humphreybc on 2009-08-31
Hope this helps, because I'm about to install Windows XP instead.

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
00:0b.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
ubuntu@ubuntu:~$ lspci -n
00:00.0 0600: 1039:0661 (rev 11)
00:01.0 0604: 1039:0003
00:02.0 0601: 1039:0964 (rev 36)
00:02.5 0101: 1039:5513 (rev 01)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 91)
00:05.0 0101: 1039:0180 (rev 01)
00:0a.0 0200: 11ab:1fa6 (rev 07)
00:0b.0 0703: 1057:3052 (rev 04)
01:00.0 0300: 1002:5960 (rev 01)
01:00.1 0380: 1002:5940 (rev 01)
ubuntu@ubuntu:~$ 

```

---

### Post by hal10000 on 2009-08-31
There are two kinds of this wireless card, one with a broadcom BCM4318 (which works out of the box) and one with a Marvell W8300 chip, which seem to only work with ndiswrapper and causing a lot of problems to many users.

I'm afraid you have the last one and i don't know how to help further.

---

