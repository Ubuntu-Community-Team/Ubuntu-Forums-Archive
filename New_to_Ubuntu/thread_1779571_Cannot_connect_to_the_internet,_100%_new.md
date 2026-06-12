---
title: "Cannot connect to the internet, 100% new"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by Sinruroku on 2011-06-10
I'm pretty much 100% new to this and know nothing of VPS or stuff like that. I run a 11.04 Ubuntu and a Windows 7. Windows 7 finds my network just fine but Ubuntu struggles to find it. I use an Actiontec wireless card, for my wireless connection. Apparently Ubuntu can't find it. The Setup thingy for wireless exists in a F:/ CD drive CuteZD_E, that only comes up when I have it inserted and disappears when successfully connected. But Ubuntu can't find the driver, thus, no internet, at least from my observations but that probably isn't it. I know nothing about Ubuntu (or Mac, for that matter), but I have experimented with Terminal trying to work it. Please, I have no idea what is up. The things it does find is eth0 and lo, or whatever lo is. It has never been able to connect since I installed Ubuntu. I don't wanna crawl back to Windows Fail. :( :( :(

Something on the side of the wireless card says this:
S/N: ZWBA03211411
MAC: 00247BF19D02
Don't think that'll help though. :( :( :(

---

### Post by jtarin on 2011-06-10
In a terminal enter ```
lspci 
```then copy and paste here.Your post of the _output_ should be in the code"#" brackets when you post. Dialogue does not need to be in code "#".

---

### Post by Sinruroku on 2011-06-10
> **jtarin said:**
> In a terminal enter ```
lspci 
```then copy and paste here.Your post of the _output_ should be in the code"#" brackets when you post. Dialogue does not need to be in code "#".

I don't exactly know what you're talking about as far as the brackets and such but this is what came up when I used Terminal of Ubuntu:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 HOST Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 Multimedia audio controller: Creative Labs CAO106 Soundblaster
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: VIA Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
```

---

### Post by amauk on 2011-06-10
have you tried connecting via wired ethernet and seeing if it prompts you to download wireless drivers?

---

### Post by jtarin on 2011-06-10
I see a Modem and Ethernet card but no wireless device. Could it be USB then? Use this command if it is ```
lsusb
``` and post.

---

### Post by jtarin on 2011-06-10
> **amauk said:**
> have you tried connecting via wired ethernet and seeing if it prompts you to download wireless drivers?
That's a very good thought,and I would advise that, but it's not detected yet, but it wouldn't hurt to try.

---

### Post by Sinruroku on 2011-06-11
Here is the Terminal when I used that command:
```
Bus 005 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.
0 <---- "What the heck is with the zero here?"
Bus 004 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID ld6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by jtarin on 2011-06-11
I still don't see it. Unplug it then plug it back in and run the command again.

---

### Post by grahammechanical on 2011-06-11
What is this?

> 00:11.6 Communication controller: VIA Technologies, Inc. AC' 97 Modem Controller (rev 80)

Here is a link

[http://ubuntuforums.org/archive/index.php/t-35028.html](http://ubuntuforums.org/archive/index.php/t-35028.html)

It is a Winmodem. And the best of luck.

Regards.

---

### Post by DirtyPC on 2011-06-11
Go to System> administration> Hardware drivers and see if there is anything there.
Also 'ws 7 finds my network just fine but Ubuntu struggles to find it. I use an Actiontec wireless card, for my wireless connection. Apparently Ubuntu can't find it. The Setup thingy for wireless exists in a F:/ CD drive CuteZD_E'
Is that an exe file? extract the .exe with archive manager and then get ndiswrapper and try installing the driver that way.
Also see: [http://ubuntuforums.org/showthread.php?t=338737](http://ubuntuforums.org/showthread.php?t=338737)
and post the results of iwconfig here.

---

### Post by Sinruroku on 2011-06-11
> **jtarin said:**
> I still don't see it. Unplug it then plug it back in and run the command again.

Did that, same results. Give me answers here! Nice, ENGLISH answers.

---

### Post by Sinruroku on 2011-06-11
C'mon, I need help! Bumpin'.

---

### Post by VOT Productions on 2011-06-11
Eating... :popcorn:

Well... I guess you should try the linux-firmware-nonfree at [http://packages.ubuntu.com/natty/all/linux-firmware-nonfree/download]("http://packages.ubuntu.com/natty/all/linux-firmware-nonfree/download") or in Synaptic.

---

### Post by Sinruroku on 2011-06-11
Guide me through that little process.

---

### Post by DirtyPC on 2011-06-11
Arrogance is not needed. People are trying to help. If you don't understand then make it clear.

---

### Post by jtarin on 2011-06-11
[This guy claims to have found the solution.]("http://ubuntuforums.org/showthread.php?t=527641")
Post results from command "lsmod" and we'll check to see what drivers are running now before you do this suggestion.

---

### Post by Sinruroku on 2011-06-15
I've found some more information on my problem. It appears it HAS found my wireless thing, but it simply has problems with the default gateway, or something. Here is some information I got from System Testing:

```
Detecting your network controllers(s):

VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
```

```
Testing your connection to the Internet:

ERROR:root:Could not find def gateway info in /proc
ERROR:root:Could not find default gateway by running route
```

---

### Post by crispy_420 on 2011-06-15
That is your wired LAN card.

Did you review jtarin's link?

---

### Post by jtarin on 2011-06-15
The OP has difficulty reading and following instructions. If he/she wants to diagnose their problem that is great. I have other people to help.:P

---

