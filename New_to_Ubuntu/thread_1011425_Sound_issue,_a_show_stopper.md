---
title: "Sound issue, a show stopper"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by MidGe48 on 2008-12-14
Hi all,

I am a real ignoramus when it comes to Linux, but decided to take the plunge this weekend.

I decided on Ubuntu distro because of its popularity and seeming ease of use.  And, gee, did I find it relatively easy.

I went quite fast.  Installed Ubuntu on a memory stick first, just to see.  It was so easy I decided to go with it. I partitioned my disk, installed and wit little problem had it going. I then decided to install all software I needed to make the switch from Vista Ultimate to Linux.  It involved quite a few going back and forth between synaptic and terminal, learning basic Linux commands etc...   Anyway besides a couple of minor issues I am there, I think.  Apache is working, Subversion, Eclipse, Java (all integarted), Tomboy (as replacement for post-it), Pulse, Gimp, Amaya, MySql, PhP, Evolution (transferred all my data from Vista Thunderbird), etc... 

Only have a minor permission issue with Eclipse (not the Ubuntu one as I needed 3.4, so installed it from a tarball)), but I get around it, for the time being by running it from a terminal with sudo.

OK, I can't seem to use my TV Tuner card, but I can do without that!  :)

Now I seem to have hit a showstopper. NO SOUND!! That is something I cannot do without unfortunately.

I researched the issue and it seems to be a bug.

Here is the data from lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
0d:00.0 Multimedia controller: Philips Semiconductors Device 7160 (rev 03)

**Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04) **seems to be the problem.  My questions here are:

1. Altough I could find heaps of references on the net (Ubuntu forums, Launchpad, etc.) about the issue, I could find no fix. Is there one and was my research lacking somehow?
2. Can I continue using Linux with the understanding that such a basic issue will be fixed quickly? Within days or weeks? The research seems to indicate that it is an old issue, so I am worried it may not get fixed within a reasonable time frame!
3. If no satisfactory answer to either of the first two questions, would changing Linux distro fix the problem?

Otherwise I will, quite sadly given my experience to date, have to abandon my quest to get out of Microsoft clutches!  :(

Any help, pointers, would be greatly appreciated.


Michel

---

### Post by sneeks on 2008-12-14
what controller are u using,pulse,alsa or oss ?

---

### Post by MidGe48 on 2008-12-14
Thanks for your prompt reply, sneeks.

I started with alsa, then installed pulse (thinking alsat was the problem) and it seems to work fine, except for the sound.

---

### Post by karlr42 on 2008-12-14
If you enter alsamixer in a terminal, what do you get?

---

### Post by sneeks on 2008-12-14
silly me,didnt ask what version u are running,gutsy,hardy or ibex.
one simple thing to check is make sure the digital box in your sound preferences is unticked,but i have got this running on a clients pc with your soundcard and can not remember how i did it,will look back in logs.

---

### Post by MidGe48 on 2008-12-14
Hiya Karl,

I get a cgi level graph set to 100

Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9500;&#9472;&#9472;&#9508;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                   100<>100                                   &#9474;
&#9474;                                  < Master >                                  &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

---

### Post by MidGe48 on 2008-12-14
8.10..  for sure; Ibex, I think :)

---

### Post by karlr42 on 2008-12-14
How are you testing whether or not you have sound? I'm hardly an expert, but all your output seems fine, I have the same device in my lspci(though I suspect it is simply the system "beep" speaker)

---

### Post by MidGe48 on 2008-12-14
Hiya Karl,

No, I get no system sounds, no Internet videos sound. I haven't tried playing cd's as that is a feature I don't use anyway. 

There is no problem with my card since I made my Vista machine dual boot, and will get rid of the Vista when the transfer of all my data is complete. Under Vista I have no problems with sound.  In Linux I tried external, internal and headphones. None gives me any sound at all.

---

### Post by karlr42 on 2008-12-14
Go to System->Preferences-> Sound, you should see a few options with drop-down menus. Select each option and hit the "test" button next to it. For me, most of them work. The sound you should hear is like a telephone dial tone. If you find a setting that works, that's great, keep it set and close the window, then try play a file or an online video, etc..

---

### Post by MidGe48 on 2008-12-14
I tried thst already but did it again now, to be sure.

I tried with autodtect and every alternative offered.

No joy.  Silence only.

---

### Post by kansasnoob on 2008-12-14
Make sure your sound card is recognized by Ubuntu:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If it is then move on to here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by agathian on 2008-12-14
Dont know about your specific card. Couple of times before - i had to wade thru all the controls in alsamixer and unmute one thing or the other. This may or may not be the case with you....

---

### Post by kansasnoob on 2008-12-14
You might also look at my post #3 here:

[http://ubuntuforums.org/showthread.php?t=1011367](http://ubuntuforums.org/showthread.php?t=1011367)

---

### Post by MidGe48 on 2008-12-14
Hello Kansanoob,

Did all the steps in the two links you gave me.  Still no joy. Still no sounds.

I must say that on Launchpad forums it seems to indicate a bug, from my reading of it. But there are so many that I am a bit unclear about it.

---

### Post by markbuntu on 2008-12-14
Try this before you do anything drastic:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by abn91c on 2008-12-14
what do you get if you do aplay -l
also try sudo modprobe snd-rv635

---

### Post by MidGe48 on 2008-12-14
abn91c,

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and

FATAL: Module snd_rv635 not found.

---

### Post by MidGe48 on 2008-12-14
Also found this on Launchpad

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210865](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210865)

the bug is shown as triaged.  Does that mean it IS a bug?
Priority set to medium. Does that mean it will get fixed anytime soon? From the thread it seems to have gone on for a while already.

I would love to stay on Linux, even if using a non-Ubuntu distro, but it seems to be a core type bug.

---

### Post by MidGe48 on 2008-12-14
Unfortunately I have no sound anywhere.  No system sound, no inernet radio, no cd sound, nada!

---

### Post by abn91c on 2008-12-14
follow this guide,that's how i got my 10 yr old isa card to work on ubuntu 8.10
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by MidGe48 on 2008-12-14
I looked up the alsa matrix of supported chipsets and the_** **_**_82801H_** (ICH8 Family) is NOT supported. The list stops at ICH7. Is that the problem? Can I expected to see it supported some time?


Am I stuck with Vista and need give up on Linux?

A search on this forum show a lot of problems with the chipset, many seemingly unsolved, except on a few on different brand of computers. from mine.

My frustration is mounting. This is my second attempt at Linux (the last time was 15 years ago) and altough it looked very good indeed, it will not cut it for me if I encounter more of this type of problem (not able to install basic functionality like sound) on my work machine.

I never thought I would have to test the basic sound before I made the decision to go LInux. It really never entered my mind.  :)  I just assumed that a production rlease would have that working on a common brand of computer (Dell), with a common brand of chipset.(Intel).

Any suggestions?   Or am I better start undoing what I had already migrated to Linux and suffer Windows poor quality/performance.  Well, at least the sound works, as well as other things I didn't even think I was going to attempt installing on Linux (TV tuner cards, etc.), being non-essential to working.  But I can't imagine working without sound, regardless of the fact I enjoy silence.  :)

---

### Post by abn91c on 2008-12-14
did you try another ubuntu based distro like maybe kubuntu, gOS, ubuntu ultimate or linux Mint. Mandriva 2009(KDE4) is friendly to a lot of older hardware, I dual boot in my 10 yr old generic pc, it is 400mhz intel celeron, 448mb pc133 ram, PC100 MB sis chipset, Yamaha ISA sound, 40 gig IDE HDD regular cdrw and $10 eMachines 17" monitor i got from goodwill with ubuntu 8.10 and mandriva 2009.

---

### Post by MidGe48 on 2008-12-14
Hey abn91c,

I don't think that is the issue.  The computer is less than 3 months old.  The chipset (**_82801H_** (ICH8 Family) ) in question is not YET supported by alsa (according to their mstrix).  I doubt that an older version of the disto would be a fix here.

Thanks for your replies and your time trying to help.

Michel

---

### Post by abn91c on 2008-12-14
> **MidGe48 said:**
> Hey abn91c,

I don't think that is the issue.  The computer is less than 3 months old.  The chipset (**_82801H_** (ICH8 Family) ) in question is not YET supported by alsa (according to their mstrix).  I doubt that an older version of the disto would be a fix here.

Thanks for your replies and your time trying to help.

Michel
You're welcome, try Mandriva 2009 before you give up on Linux, also dreamlinux might work for you also, you can find them here [http://www.distrowatch.com](http://www.distrowatch.com)

---

### Post by MidGe48 on 2008-12-26
I thought I would post an update.

As of 10 minutes ago, I heard the first sound out of Ubuntu. I just did a suggested update of my Linux installation, which included, amongst others, PulseAudio and linux kernel and magically on re-booting the sound was there.

The issue with:

p, li { white-space: pre-wrap; }  [COLOR=#000000][FONT=DejaVu Sans]USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]        Subsystem: Dell Device 0256[/FONT][/COLOR]
[COLOR=#000000][FONT=DejaVu Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=DejaVu Sans]is resolved for me, and hopefully for others.  :)
[/FONT][/COLOR]


I only have liveable with Linux issues now.  So I'll keep on Linux.

Again, thanks to all that tried to help.

Compliments of the season,

Michel

---

