---
title: "Linksys Help"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by sindri829 on 2010-01-25
I have recently purchased an Acer Aspire One netbook running Windows 7 starter. I have just set it up to dualboot with Ubuntu 9.10. I have a Linksys Wireless-G Broadband Router Model: WRT54G. I have two other computers using a wired connection from this router, one using Windows XP and the other using Windows 7 Ultimate. I have also in the past connected to this router on this netbook using Windows 7 starter, as well as a Nintendo Wii and an Appli iPod Touch (first Gen). 
However, for some reason, Ubunto 9.10 refuses to recognise this router's signal. I cant find it, and aparently I have no idea how to set it up because its not working. What do I have to do to make it work? And why is there no simple step-by-step anywhere to be found?

---

### Post by sindri829 on 2010-01-25
And its very frustrating btw...

---

### Post by MaindotC on 2010-01-25
The first thing you need to do is make sure your notebook's wireless adapter is properly recognized by Ubuntu.  There are step-by-step instructions in the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  Please follow the directions and let us know precisely where you are having difficulty.  If a term seems foreign to you - like "module", then please google it and if you are still have difficulty understanding it please let us know which part of your googling you do not understand.  Thanks!

---

### Post by sindri829 on 2010-01-25
Nothing on that page helped. Ubuntu obviously knows there is a built in wi-fi card, but is not prepared to use it. I set up my wi-fi connection like 10 times, but even when I highlight over "network connections" at the top, it only recognizes a wired connection, that I dont have. 
And the ubuntu manuals are incredibly complicated, and I dont understand what is going on. Windows 7 just automatically said "there is a connection here, what's the password" and just worked. It just worked. Why wont Ubuntu just work? Should I just uninstall it, because I cant figure this out...

---

### Post by halitech on 2010-01-25
can you open a terminal and post the output of
```
lspci
```and```
lsusb
```
and ```
sudo ifconfig
```

---

### Post by sindri829 on 2010-01-25
```

[FONT=Times New Roman][SIZE=3]devon@ubuntu:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)[/SIZE][/FONT]

```
 
 
and 
 
```

[FONT=Times New Roman][SIZE=3]devon@ubuntu:~$ lsusb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]

```
 
finally
 
```

[FONT=Times New Roman][SIZE=3]devon@ubuntu:~$ sudo ifconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password for devon: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:26:22:74:49:e4  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          Interrupt:29 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/FONT][/SIZE]

```
 
 
that should be it I hope...

---

### Post by sindri829 on 2010-01-25
had to copy it into open office, save it to a drive, bring it to my xp computer, and paste it here...

---

### Post by halitech on 2010-01-25
ok, so you have a Broadcom wireless chip

[color="red"]01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) [/color]

Have you checked the Hardware Drivers (Admin - System - Hardware drivers) to see if you can enable it there? This will be easier if you can connect to a wired connection until you get the wireless working.

This may help if you can't activate the drivers
[http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)

---

### Post by atomic0x on 2010-01-25
Hi sindri,

You have a Broadcom wireless card. Broadcom doesn't have a good history of providing opensource drivers, so they are not included by default with ubuntu.

You can install the drivers though. Please see this thread for instructions.
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Cheers.

---

### Post by cprofitt on 2010-01-25
With a similar model I had to hook to Ethernet -- run the system update -- then reboot -- then look under System | Hardware for restricted drivers.  Prior to the update there were no restricted drivers listed, but after the system update they were there and once activated the wireless system worked as expected.

---

### Post by MaindotC on 2010-01-25
> **halitech said:**
> can you open a terminal and post the output of
```
lspci
```and```
lsusb
```
and ```
sudo ifconfig
```

There's no point in doing that because those commands are included in directions I gave him.  Here is his response:

> **sindri829 said:**
> Nothing on that page helped. 

I guess the community-maintained documentation for the entire Ubuntu operating system with respect to troubleshooting wireless issues won't work for him.  Go back to Windows because everything there just works.

---

### Post by CharlesA on 2010-01-25
Am I the only one who twitched when I saw "broadcom" ?

Check out the thread that atomic0x linked to.

---

### Post by halitech on 2010-01-25
> **strAlan said:**
> There's no point in doing that because those commands are included in directions I gave him.  Here is his response:



I guess the community-maintained documentation for the entire Ubuntu operating system with respect to troubleshooting wireless issues won't work for him.  Go back to Windows because everything there just works.

and how often do people actually follow through on following a troubleshooting guide without having them post the info back to us on the board?

---

### Post by aeiah on 2010-01-25
looks like your wireless chipset is: BCM4312

[http://ubuntuforums.org/showthread.php?t=1309760](http://ubuntuforums.org/showthread.php?t=1309760)

when on your quest to get this working you should try searching using your wireless card. i have an acer aspire one, but mine is obviously older than yours and my wireless card is an atheros, so be weary of assuming all acer aspire ones have the same hardware as yours. good luck :o

---

### Post by MaindotC on 2010-01-25
> **halitech said:**
> and how often do people actually follow through on following a troubleshooting guide without having them post the info back to us on the board?

They don't. Who's fault is that?

---

### Post by halitech on 2010-01-25
> **strAlan said:**
> They don't. Who's fault is that?

theirs but that doesn't mean we should make snide remarks about going back to Windows because everything works there.

---

### Post by Greenwidth on 2010-01-25
I have the same card, the STA driver works fine. See this for how to:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by MaindotC on 2010-01-25
Give me a break!  This whole post was a snide remark and I reported it to a moderator:

> **sindri829 said:**
> Nothing on that page helped. Ubuntu obviously knows there is a built in wi-fi card, but is not prepared to use it. I set up my wi-fi connection like 10 times, but even when I highlight over "network connections" at the top, it only recognizes a wired connection, that I dont have. 
And the ubuntu manuals are incredibly complicated, and I dont understand what is going on. Windows 7 just automatically said "there is a connection here, what's the password" and just worked. It just worked. Why wont Ubuntu just work? Should I just uninstall it, because I cant figure this out...

I can't believe you are a member of this forum and a user, and you support this garbage.  "And the Ubuntu manuals are incredibly complicated".  Oh, you mean the mean the manuals that are maintained by the users of the operating system?  The manuals that have loads of links and helpful wikis to explain how to best utilise Ubuntu? 

Hey look at this way.  I posted that link at 11:07 AM EST.  That means OP was emailed of a reply no later than 11:10 am.  You're telling me in 30 minutes OP went to that page, obviously with NO understand of what each command does (otherwise he wouldn't have originated such a weak post) and thus would have to click on the explanations and read the man pages (or parts of but maybe I'm assuming too much) and followed ALL those troubleshooting steps?  He's lying his butt off and wasting our time because he doesn't want to RTFM.

Whatever - have fun basically regurgitating to this user basically everything that is on that page I linked to him in the first place.

---

### Post by halitech on 2010-01-25
Yes I am a member here and I remember what it was like when I first started using ubuntu. How many other people have we helped where we gave them a link and they continued getting help in a thread? Sometimes people need a little more handholding then just simply being given a link and told to "RTFM"

---

### Post by sindri829 on 2010-01-25
Wonderful... followed these instructions:
Solution:

1. Get wired internet access

2. Update:

Code:
 sudo apt-get updatesudo apt-get upgrade
3. Reboot
 
 
From here [http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)
And now ubuntu wont boot
This is not my day

---

### Post by halitech on 2010-01-25
what happened after you rebooted? what screen do you get to? what is the last thing you see on the screen?

---

### Post by sindri829 on 2010-01-25
Its stuck at the usual:
 
[Linux-bzImage, setup=0x3400, sixe=0x3b2700]
[Initrd, addr=0x2f0ce000, size=0x789920]
 
That i see every time, but its stuck there. It still is.

---

### Post by halitech on 2010-01-25
sounds like you have more then just a wireless issue but I have no idea what would cause it to stick at that point. How did you install Ubuntu on this system?

---

### Post by sindri829 on 2010-01-25
I have no cd drive, so I put the Ubuntu installer for windows on an sd card, but it in its built in sd slot, and installed it through Windows 7, using all the default settings it gave.

---

### Post by halitech on 2010-01-25
So you used WUBI to do the install?

---

### Post by sindri829 on 2010-01-25
Yes I did, and it seemed to work just fine. But after the updates when I tried to boot Ubunto back up, it got stuck there.
I ran the exact commands it gave in that help forum.

---

### Post by halitech on 2010-01-25
WUBI isn't the best way to install Ubuntu IMO. You could try uninstalling it from your windows control panel (Add/Remove) and trying it again but I'm not sure how well it will work.

---

### Post by sindri829 on 2010-01-25
Actually, I got it to work... Using Windows.
I turned it off, and tried booting linux again, still nothing
I turned it off and booted windows, that worked fine.
Then i tried ubuntu again, and it booted just fine.

---

### Post by sindri829 on 2010-01-25
I managed to follow this [http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603) and do another restart. This time it worked great. And, the problem is fixed :)

---

### Post by halitech on 2010-01-25
thats great, is your wireless working now?

---

### Post by sindri829 on 2010-01-25
Yeep...
To connect to the internet, I had to connect to the internet... lol... Wouldnt have been my first thought...
 
Thank you :):KS

---

### Post by halitech on 2010-01-25
glad to hear you got it working. Please mark the thread solved so others will know.

---

