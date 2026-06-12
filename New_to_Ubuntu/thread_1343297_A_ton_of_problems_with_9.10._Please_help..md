---
title: "A ton of problems with 9.10. Please help."
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Bakudan00 on 2009-12-01
Hello, folks.

I am having a lot of problems with Ubuntu 9.10 on my brand new Gateway NV5207u. They may or may not be related, but instead of spamming the forum with multiple threads I thought it might be better to detail each in one, in order of frequency and importance. If not, I sincerely apologize and will spam away.

1) Wireless is fine, then out of the blue it dies. The applet signal indicator says I am still connected with a good signal, but nothing loads. I "disconnect" and try to connect again, but all it does is ask me for my security passphrase every few minutes or so. I have to reboot to get online again.

2) Occasionally, the active window will fade to black and white. I cannot close it. I tried to open System Monitor to close Firefox, the offending program the last time this happened, and then the same thing happened to System Monitor. I then open the terminal to force a reboot, but my keystrokes do not register on the screen. Sometimes I am able to reboot with the GUI, and the last time I was able to, I got this message (1st jpeg).

3) My programs will freeze momentarily, then free up, then freeze again. I managed to shutdown once after this and this is the error message I got, white-on-black:
 
[ 3262.018829] usplash:4846 forcing invalid memtype ffffffffd0000000.ffffffffd1000000

4) After I choose shutdown from the GUI, the panels and mouse pointer disappear and all I see is the desktop wallpaper. I have to shut off with the power button.

5) I play some games (Flightgear, Chromium) and the sound starts out okay for a few minutes of play, but then it sounds mangled, and then disappears altogether.

Again I don't know if this is related, but since [this problem]("http://ubuntuforums.org/showthread.php?t=1341008") was solved, I see odd text (2nd jpeg) during boot up after the white Ubuntu logo, when before I haven't.

Is it normal to have this many bugs? I'm forced to restart several times a day, and I've had each of these things happen to me at least once.

It's sad because I'm really starting to get comfortable with Ubuntu (the software center is brilliant), but my normally high threshold for patience is wearing thin. Am I to blame for going for the latest version not knowing that these kind of troubles are par for the course, or as a newbie should I have installed the LTS version instead? Or should I scrap everything and do it now? I had to write this post twice because Gnome Do disappeared for some reason (not for the first time) and when I mistakenly minimized the window I didn't know how to get it back. Downloading those two photos off my camera was a hassle, because after one photo downloaded, it wouldn't recognize the camera -- after it had already. I love open source and am committed to trying some form of linux but since I installed 9.10 nothing for me has "just worked."

I'll be eternally grateful if someone could resolve just one of these problems. But until then I can't honestly say I am satisfied.

PS, I tried booting in recovery mode and repairing broken packages, but there was no effect.

---

### Post by corncob on 2009-12-01
I'm running 9.10 on an eeebox without any problems.  However, I just ordered a Gateway NV5425u -- sounds similar to yours so I'll keep in touch if I have anything to report.

---

### Post by gordintoronto on 2009-12-01
> **Bakudan00 said:**
> Hello, folks.

I am having a lot of problems with Ubuntu 9.10 on my brand new Gateway NV5207u. They may or may not be related

I suggest you run memtest overnight....

---

### Post by Bakudan00 on 2009-12-01
I finished running memtest 86+ and it found no errors. :???:

---

### Post by rustutzman on 2009-12-01
Can you run this?
```
uname -a
```
These problems almost look like beta issues and I want to be sure you're running the latest.

Russ

---

### Post by gradinaruvasile on 2009-12-01
He has 2.6.31-15-generic kernel - see the jpgs. Also has Ati card with proprietary drivers. I would say start from that.
I think your graphical problems are related to the Ati vid card/drivers...

If you start from live cd have you got these issues?

Also, open a terminal (applications-> accessories->terminal) and type:

lspci

post the output of that command.

---

### Post by Bakudan00 on 2009-12-01
@rustutzman

```
Linux eric-admin-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
```@gradinaruvasile

In the times that I have used the live CD, I have noticed no problems at all. I may not have used it long enough for them to manifest, however.

Output of lspci:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```Thanks all for your replies.

---

### Post by sandyd on 2009-12-01
> **Bakudan00 said:**
> Hello, folks.

I am having a lot of problems with Ubuntu 9.10 on my brand new Gateway NV5207u. They may or may not be related, but instead of spamming the forum with multiple threads I thought it might be better to detail each in one, in order of frequency and importance. If not, I sincerely apologize and will spam away.

1) Wireless is fine, then out of the blue it dies. The applet signal indicator says I am still connected with a good signal, but nothing loads. I "disconnect" and try to connect again, but all it does is ask me for my security passphrase every few minutes or so. I have to reboot to get online again.

2) Occasionally, the active window will fade to black and white. I cannot close it. I tried to open System Monitor to close Firefox, the offending program the last time this happened, and then the same thing happened to System Monitor. I then open the terminal to force a reboot, but my keystrokes do not register on the screen. Sometimes I am able to reboot with the GUI, and the last time I was able to, I got this message (1st jpeg).

3) My programs will freeze momentarily, then free up, then freeze again. I managed to shutdown once after this and this is the error message I got, white-on-black:
 
[ 3262.018829] usplash:4846 forcing invalid memtype ffffffffd0000000.ffffffffd1000000

4) After I choose shutdown from the GUI, the panels and mouse pointer disappear and all I see is the desktop wallpaper. I have to shut off with the power button.

5) I play some games (Flightgear, Chromium) and the sound starts out okay for a few minutes of play, but then it sounds mangled, and then disappears altogether.

Again I don't know if this is related, but since [this problem]("http://ubuntuforums.org/showthread.php?t=1341008") was solved, I see odd text (2nd jpeg) during boot up after the white Ubuntu logo, when before I haven't.

Is it normal to have this many bugs? I'm forced to restart several times a day, and I've had each of these things happen to me at least once.

It's sad because I'm really starting to get comfortable with Ubuntu (the software center is brilliant), but my normally high threshold for patience is wearing thin. Am I to blame for going for the latest version not knowing that these kind of troubles are par for the course, or as a newbie should I have installed the LTS version instead? Or should I scrap everything and do it now? I had to write this post twice because Gnome Do disappeared for some reason (not for the first time) and when I mistakenly minimized the window I didn't know how to get it back. Downloading those two photos off my camera was a hassle, because after one photo downloaded, it wouldn't recognize the camera -- after it had already. I love open source and am committed to trying some form of linux but since I installed 9.10 nothing for me has "just worked."

I'll be eternally grateful if someone could resolve just one of these problems. But until then I can't honestly say I am satisfied.

PS, I tried booting in recovery mode and repairing broken packages, but there was no effect.
question: how hot is your computer getting?
p.s might be related to your video issues 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd/+bug/374034](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd/+bug/374034)

p.s. what does this output?
```

dmesg|grep ' fglrx '

```that will list your driver version
ati recently released catalyst 9.11 and ive found it to be a bit more stable and less buggy

p.s. disable virtual effects and see if that makes everything work better.
p.p.s. sound:
try running this and rebooting
```

sudo cat "options snd-hda-intel model=laptop" >> /etc/modprobe.d/alsa-base
```

---

### Post by Bakudan00 on 2009-12-02
I don't notice the fan running more than usual, (especially during the fading window color one, which just happened) and aside from the gaming issues cpu usage is between 10-20%.

Output of dmesg|grep ' fglrx ':

```
[   15.279802] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
```"Virtual effects..." Do you mean all that Compiz eye candy stuff? I tried to disable as much as I know how to.

I ran that suggestion about the sound and got this:

```
bash: /etc/modprobe.d/alsa-base: Permission denied
```

Edit: I played Chromium for 20 min. (longest I ever have) with no sound problems, but with Flightgear they started in under a min., and my cpu was working at 99%. This is odd. I can play games far more sophisticated than Flightgear (Prey) with no problems at all.

---

### Post by sandyd on 2009-12-02
oops. i think you have to manually add that line in instead of echoing it in

---

### Post by Bakudan00 on 2009-12-02
Do you mean write this in the terminal or in run application (alt+f2)? Run app did nothing, and I got the same message when I typed it into the terminal manually.

---

### Post by Bakudan00 on 2009-12-02
Bump.

And by the way, [this fellow]("http://jake.wasdin.net/blog/archives/84") has pretty much the same model computer as I do, and he's running 32 bit 9.04 with virtually no problems. If no one can find any solutions for me I'm very willing to downgrade from 64 bit 9.10. Is it possible to do this without a total reinstall? Is my filesystem being formatted to ext3 instead of the default ext4 contributing to any of these problems? I think it's unlikely but I'm desperate.

---

