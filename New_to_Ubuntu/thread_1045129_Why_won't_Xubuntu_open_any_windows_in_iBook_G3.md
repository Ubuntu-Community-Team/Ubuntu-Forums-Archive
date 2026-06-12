---
title: "Why won't Xubuntu open any windows in iBook G3?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by NewsAndHistory on 2009-01-20
I just installed Xubuntu 8.10 Intrepid on my iBook G3 600 MHz. Xubuntu 8.10 is not allowing me to open Firefox & many other applications' windows.  I get the spinning gray navigator-icon whenever I click on application-icons in Xubuntu. (Note: Only 2 sets of things open up after I click on them:
1. Xubuntu's "Quit window" (the icon, which represents that option-window has a ***Door with the red arrow***-icon on the far-right side of the Xubuntu panel).
2. Anything listed in the context-menu of the "Panel" (The context-menu appears after I right-click on the Xubuntu panel).

Earlier, I noticed that whenever Xubuntu 8.10 starts up, ***3 small black squares*** appear in the Xubuntu panel/taskbar. To be specific, they're horizontally lined up with each other with an inch (or more) of space between each of them.

(This is not just happening to my screen. Others have noticed this glitch as well: If you read through this IRC-chat session [[Link]("http://irclogs.ubuntu.com/2008/08/08/%23xubuntu.txt")]: there, you'll discover someone else alerted others about the "black squares" he or she noticed on the taskbar).

 2 or more minutes went by before the ***red triangle***-icon appeared (it only appears whenever software-updates are available for Xubuntu). I attempted to install the software-updates on my machine, but it wouldn't work, so I quit and I restarted my computer. 

(Apparently, after restarting Xubuntu: the black squares have vanished from the taskbar, but many of the windows are still not opening after I click on them. However, none of the windows (besides the 2 sets I already mentioned) will not open after I click on the icons in the panel. Also, the red triangle with the exclamation point in the middle of it is still showing up in the panel, and it ***still*** won't allow me to update any of the software listed in the "update manager".

Please help me to solve these problems. Would any of you please tell me if I should downgrade to Xubuntu 8.04?

Here are the specs of my iBook G3:

**CPU:** 600 MHz PPC 750fx
**Bus:** 100 MHz
**Performance:** Geekbench 2 (Tiger): 304
       **ROM:** 4 MB, NewWorld ROM in RAM architecture
**RAM:** 128 MB of SDRAM soldered in place, expandable to 640 MB using one 1.25" 3.3V PC100 compliant SO-DIMM
**Level 2 cache:** 256 KB on-chip cache
**Video:** ATI Rage Mobility 128 with 2x AGP
**VRAM:** 8 MB
**Display:** 12.1" 24-bit SVGA (1024 x 768> color active matrix, resolution scaling for 640 x 480 and 800 x 600 modes
**Video out:** VGA and composite video
**Hard drive:** 20 GB UltraATA-66
**Media drive:** choice of CD-ROM, DVD-ROM, or CD-RW/DVD-ROM
**Floppy drive:** external USB only
**Expansions bays:** none
**USB:** 2 USB 1.1 ports
**FireWire:** 1 FW400 port
**Ethernet:** 10/100Base-T
**Modem:** v.90 56k
**WiFi:** 802.11b AirPort optional
**Microphone:** built in
**PC Card slots:** none
**Battery:** rated at 5 hours
**Size:** 11.2 x 9.1 x 1.35" (28.5 x 23.0 x 3.4 cm)
**Weight:** 4.9 pounds (2.2 kg) with battery


       _Source_:
[http://lowendmac.com/pb2/12in-ibook-g3-600-mhz.html](http://lowendmac.com/pb2/12in-ibook-g3-600-mhz.html)

---

### Post by NewsAndHistory on 2009-01-20
Please guide me.

---

### Post by ahuman on 2009-01-20
:( [bump for help] You may like to try going to the ***Apple Users*** forum-category of this website.

---

### Post by Terl on 2009-01-20
I admit I do not know much about Apple computers but it seems to me that the pc is light on specs, especially if the graphics card is sharing any of the 128 megs of ram.  Did you try xubuntu in live mode before you installed?

EDIT:  I did some checking and it seems like you could run it but if the graphics card is cutting into the ram I think you will have issues.

---

### Post by NewsAndHistory on 2009-01-20
I haven't tried that Live thing. Would you please recommend a distro that works just as well as Ubuntu on old computers like mine? I've already tried Debian Lenny on that same computer (iBook G3 600 MHz), but it wouldn't grant me access to the terminal, even though I was obviously the admin (the only user to make an account on it).

Please suggest any other Linux distros that work well on PowerPC's beside Yellow Dog Linux & Arch Linux?

If I downgraded to Xubuntu 8.04: would that distro still be able to use the same programs that are used on Xubuntu 8.10 Intrepid?

Thanks for your kindness & help.

---

### Post by Terl on 2009-01-20
You could try [Zenwalk Linux]("http://www.zenwalk.org/") or another is [Vector Linux]("http://vectorlinux.com/").  Both of these are Slackware based distributions.  They both have a package management system that will solve dependencies for you.  They do not have as many packages as Ubuntu or Debian.  I recently tried Vecor Linux version 6 release candidate 3 on my Dell laptop and it set up my ati card and broadcom wireless out of the box. 

[Distrowatch]("http://distrowatch.com/") is a great place to go to find out more information on almost every linux distro out there.  You may want to check there.

The other options is to try the live cd's whenever they have one available.  That allows you to test drive without installing.  Oh, that reminds me of another lightweight distribution you could try:  Wolvix (slackware based again)

---

### Post by NewsAndHistory on 2009-01-20
Thanks. I will try those distros on my other computers. Xubuntu won't work well on my computer, anymore. It won't allow me to open the terminal, and now it won't even allow me to open my CD-drive when I really need it to get rid of Xubuntu & reinstall a stable operating system.

Would anyone, who's reading this please tell me which command to type in my machine during booting-process so I can make the CD-drive open & put in a new Install-CD?

Thanks again for you help & kindness, Teri****

---

### Post by handydan918 on 2009-01-20
> **NewsAndHistory said:**
> 

I haven't tried that Live thing. Would you please recommend a distro that works just as well as Ubuntu on old computers like mine? I've already tried Debian Lenny on that same computer (iBook G3 600 MHz), but it wouldn't grant me access to the terminal, even though I was obviously the admin (the only user to make an account on it).
Debian doesn't allow root logins by default. sudo should work, however.> 
Would anyone, who's reading this please tell me which command to type in my machine during booting-process so I can make the CD-drive open & put in a new Install-CD?
Try ```
eject
```
Thanks again for you help & kindness, Teri****

I wouldn't give up too quickly on lenny. I have it running on a 733 w/ 256 megs of ram, and it does OK. 

[AntiX]("http://antix.mepis.org/index.php/Main_Page") is likely what you're looking for.

---

### Post by avtolle on 2009-01-20
OK, with 128 mb RAM, you'll have trouble with any Ubuntu or derivative Live CD; IIRC, to run the live Xubuntu CD, it requires a minimum of 192 mb RAM. 

You should take a look at the Apple Users forum here for help. On Teri's recommendations; I don't recall that any of them have a version that runs on PPC. Check with Distrowatch, as suggested. Other than Debian, Ubuntu, Yellow Dog and Arch, there is Fedora and OpenSuse as I recall which have PPC versions.

---

### Post by boof1988 on 2009-01-20
> **NewsAndHistory said:**
> Thanks. I will try those distros on my other computers. Xubuntu won't work well on my computer, anymore. It won't allow me to open the terminal, and now it won't even allow me to open my CD-drive when I really need it to get rid of Xubuntu & reinstall a stable operating system.

Would anyone, who's reading this please tell me which command to type in my machine during booting-process so I can make the CD-drive open & put in a new Install-CD?

Thanks again for you help & kindness, Teri****

There is (sometimes) a very small hole in the front of the drivebay (or somewhere nearby) that you can poke a small wire (paperclip, needle or similar) into, and the drive will eject.  This uses a mechanical latch that ejects the cd so your drive may not have this feature.  You might try googling for you computer manual and it might have the exact location of the "cd release".

Hope this helps some.

---

