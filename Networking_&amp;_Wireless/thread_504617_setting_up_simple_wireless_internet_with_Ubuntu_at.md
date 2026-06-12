---
title: "setting up simple wireless internet with Ubuntu at my home!"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by kamsmart on 2007-07-19
Hi all,

I have the 7.04 32-bit PC version of the live Ubuntu CD with me and I am trying to install it on my Opteron 170 CPU desktop with 3 GB of RAM. I have NVIDIA GE-FORCE 6600 Video card and I have a PCI 802.11g card.  The live CD gave me a good live install except that I failed to configure the wireless internet.

Please see the pics of my attempt to configure the wireless internet below:

[http://picasaweb.google.com/kamsmart...ey=z2iHPts7e5k](http://picasaweb.google.com/kamsmart...ey=z2iHPts7e5k)

Please read the captions to my photos in the link above to get the story of trying to install wireless internet.

Folks, I am stuck. Please help me out!!! I would really appreciate your help. I have been reading about Linux a lot and I rally want a Linux system at home to try it out ... and configuring wireless networking is holding me back!

Thanks a lot!

---

### Post by loserboy on 2007-07-19
your link is broken

i guess the place to start would be to identify your wireless card, go to a terminal and type:
> lspci

then post the contents

---

### Post by ubanchaos on 2007-07-19
give me the specs of your card

---

### Post by kamsmart on 2007-07-19
I am trying to paste the link again:

[http://picasaweb.google.com/kamsmart/UbuntuOnOpteronDesktopConfiguringWirelessInternet?authkey=z2iHPts7e5k](http://picasaweb.google.com/kamsmart/UbuntuOnOpteronDesktopConfiguringWirelessInternet?authkey=z2iHPts7e5k)

I will post the results of the command lspci in a little while ...

Thank you so much for your help!!!

Regards.

---

### Post by loserboy on 2007-07-19
1st thing to do is to take all security off the network just temporarily (if you can)

sometimes WPA or WEP doesn't work properly, once you get connected then we can worry about that

still waitin on the lspci will tell us more

---

### Post by psyburn on 2007-07-19
Biggest thing is the fact that you are using 128-bit Hexadecimal
I don't know if this is a known bug or otherwise.
When I would place my hex key in the box and left it ASCII the network would never work unless I deleted the SSID profile as I described below, then logged out and logged back in and  set the connection back up fresh in Network Manager

OKay, I fixed my wep connection by deleting the network profile.
```
Here's how I do it:
Click Places->Home
on the menu bar click "View" and click "Show hidden files"
the full path is /.gconf/system/networking/wireless/networks
delete the entire folder that is named after your network.
OPTIONAL: on the menu bar click "View" and click "Show hidden files" to uncheck and hide previously hidden files.
Now logout and log back in.
Try connecting again, but make sure to choose 64/128-bit Hex when putting in your key.
```

Should work now.

---

### Post by kamsmart on 2007-07-19
> **loserboy said:**
> 1st thing to do is to take all security off the network just temporarily (if you can)

sometimes WPA or WEP doesn't work properly, once you get connected then we can worry about that

still waitin on the lspci will tell us more

Hi, this is the output from quoting lspci on the terminal.
[COLOR="Red"]
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
02:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
ubuntu@ubuntu:~$ [/COLOR]

How do I turn off the security from the network?  Please note that I am in the "live" mode of the Linux system and haven't installed it on my desktop yet ...

Thanks!

---

### Post by kamsmart on 2007-07-19
> **psyburn said:**
> Biggest thing is the fact that you are using 128-bit Hexadecimal
I don't know if this is a known bug or otherwise.
When I would place my hex key in the box and left it ASCII the network would never work unless I deleted the SSID profile as I described below, then logged out and logged back in and  set the connection back up fresh in Network Manager

OKay, I fixed my wep connection by deleting the network profile.
```
Here's how I do it:
Click Places->Home
on the menu bar click "View" and click "Show hidden files"
the full path is /.gconf/system/networking/wireless/networks
delete the entire folder that is named after your network.
OPTIONAL: on the menu bar click "View" and click "Show hidden files" to uncheck and hide previously hidden files.
Now logout and log back in.
Try connecting again, but make sure to choose 64/128-bit Hex when putting in your key.
```

Should work now.

Hi,

From the Macbook pictures that I showed you, does it show that I have a HEX key?  I do not see anything on the wireless network's configuration window on Mac that has any bearing to this "hex" stuff.  How do I find out what kind of key am I using on my wireless network?

I went into ~/.gconf.  I could not see the folder called system at all.  It might be because this is a "LIVE" install of Linux, and Linux has not been installed on the Harddisk on my desktop yet ... does this information help you at all?

thanks for all your replies .. let me know what should be my next step ..!!

thanks!

---

### Post by loserboy on 2007-07-19
the security is handled by your router, you need to login to it from a computer that has a network connection using your browser (for linksys i think the default address is 192.168.1.1)

I'm not familiar with psyburns method, but by all means give it a shot, I don't know if being in the Livecd makes a difference for his way or not

now I'm gonna go check your wireless card and see if there are any known issues with it
for future reference this is your wireless card  
> 02:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by kamsmart on 2007-07-19
I am going ahead and installing Linux from the Live CD on the desktop, in an attempt to see whether having a locally installed Linux makes any difference with respect to the wireless connectivity...

loserboy, please see my reply to psyburn, about his method, where he suggested deleting a configuration hidden folder in the home directory.  I don't see such a folder in my install. May be, that's another difference between a live system and a local Linux install.

I am giving it a shot as I type.  I will let you know what happens.

Just some heads up .. when Ubuntu starts up, does it give me a choice to start it in safe graphics mode?  I am asking this because the full-fledged Ubuntu install from its CD does not work on my computer and the screen resolution is screws up .. but when I try to do the live install with the second option "start Ubuntu in safe graphics mode"

Thanks!

---

### Post by loserboy on 2007-07-19
when you have it actually installed, it does not offer safe graphics mode, but if you made the install from safe graphics mode it should write the current working settings to your Xorg (a settings file). If not, there is a simple workaround we can do, althoug it's much easier if you actually have internet

---

### Post by kamsmart on 2007-07-19
OK sounds good.  I am installing the system now.  Hopefully, I will be able to bot into a local install of Ubuntu with the graphics working fine, and then, I will attempt to try cranking up the wireless internet ...

Thanks Loserboy for your help and guidance ... 

I will report back in a short while on the installation going on my desktop ..

Regards

---

### Post by loserboy on 2007-07-19
I'll be leaving my computer for a while, but I'll be back, hopefully someone will have stepped in for me

---

### Post by kamsmart on 2007-07-19
I have two HDDs on my desktop, one is dedicated completely to Windows that my wife uses.  The other one is for me to play with the various Linux installations.  I had recently tinkered along with Mandriva and I had that installed on my sdb (the second hard disk).  When I tried installing Ubuntu on it, I re-partitioned one of the big partitions dedicated for Mandriva, and used that for Ubuntu.  When the installation finished, the computer would not boot into any of thwo systems (Mandriva and Ubuntu).  Sigh!

I am attempting to reinstall Ubuntu on the SDB  and will report the results here .. thanks!

---

### Post by kamsmart on 2007-07-19
Ok, I have a local install of Ubuntu now and it still gives me the same problem.

I still do not have ~/.gconf/system folder.

Any ideas, folks??

---

### Post by loserboy on 2007-07-19
did you turn off the security like I mentioned?

---

### Post by kamsmart on 2007-07-20
> **loserboy said:**
> did you turn off the security like I mentioned?

I havent done that yet.  I will do that first thing tomorrow morning and I will report it tomorrow.  SO, I take out the WEP and other kinds of security, and make my wireless network fre for anyone to connect on to .. is that what you meant, loserboy?

Thank you for your help.  I have some other problems with the Ubuntu's bootloader, but I will leave that stuff for tomorrow.  Lets take care of the internet first.

Regards .. and sleep well!  We got to fix this desktop baby of mine tomorrow :)

---

### Post by loserboy on 2007-07-20
yes take off all the security....but like you said this does give everyone access to the network so you only want to do it for testing purposes

---

### Post by kamsmart on 2007-07-27
> **loserboy said:**
> yes take off all the security....but like you said this does give everyone access to the network so you only want to do it for testing purposes

OK, I am back.  Sorry for not being in the scene here.  I was busy with so many other things.  Ultimately, I got time now to try out Linux with the start of the weekend ..:)

I took off all the security from my network.  I have an airport setup at home, and I used the Airport Admin utility on my MacBook to take out the WEP security.  After I did that, I had to reconnect to my wireless home network on my MacBook, and I could successfully do that and I was able to be online.

But unfortunately, I could still NOT connect to the unprotected home wireless network on the Ubuntu Desktop.  When I attempt to join the wireless network, the blue dot keeps flying off on the top right corner of the Ubuntu desktop, and it says that "attempting to join the network ..:, and after sometime, it comes back and says that it could not join the network.

Any ideas as to what might be going wrong?  Any help appreciated .. Thanks!

Regards.

---

