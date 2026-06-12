---
title: "Video streaming in fullscreen issues"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by adobrakic on 2011-04-09
I have Ubuntu 10.10 64bit, and I'm having problem with playing videos in full-screen mode on websites such as Youtube. Compiz kind of lags when playing videos, and when I turn it off this happens. The playback itself is fine, Ubuntu just seems to stop recognizing that it's a video. The popup menu on the video stops coming up when you move the mouse, so you can't change the volume or exit fullscreen mode, and the ESC button isn't recognized either.  It eventually exists fullscreen if I tap ESC and click with my mouse over and over. Also, the the screensaver is still triggered after 10 minutes when playing the video, but not when playing videos in VLC or any other program. is there a way to make it temporarily deactivate the screensaver if im in fullscreen mode with flash videos?
any suggestions?

lspci:
```
ado@Ado-DESKTOP ~ $ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```

glxgears (if necessary):
```
ado@Ado-DESKTOP ~ $ glxgears
12062 frames in 5.0 seconds = 2411.712 FPS
12773 frames in 5.0 seconds = 2554.531 FPS
12577 frames in 5.0 seconds = 2515.389 FPS
12503 frames in 5.0 seconds = 2500.488 FPS
12350 frames in 5.0 seconds = 2469.622 FPS
12926 frames in 5.0 seconds = 2584.747 FPS
12696 frames in 5.0 seconds = 2539.116 FPS

```

---

### Post by adobrakic on 2011-04-10
bump

---

### Post by Perfect Storm on 2011-04-10
Have you tried with flash 64-bit? The flash that normally installed is 32-bit?
Which driver do you use open or the close driver?

---

### Post by adobrakic on 2011-04-11
I have the 64-bit flash installed, but I installed the video driver through the official Ubuntu additional drivers program, so I'm assuming it's the closed source one.

---

### Post by fooman on 2011-04-11
try this....open a terminal and run these three commands:

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true"  > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

close you browser if its open,  then start it up again.  try a youtube video,  see if its any better.

fixed the fullscreen flash video problems for me,   using 64bit 10.10.

hope that helps.

---

### Post by adobrakic on 2011-04-11
@fooman since the issue is kind of sporadic, I won't be able to immediately tell if that fixed the issue. I'll keep testing videos over the next day or so and see how it works out. Thanks for the suggestion.

---

### Post by adobrakic on 2011-04-13
seems to have fixed the problem, thanks!

---

### Post by snowguy on 2011-04-13
when you say the problem is fixed did you mean that your screensaver is no longer activated when playing flash in full screen? Or just that it fixed the other problems you reported?

I don't have the other flash problems you report, but my screensaver / power save features do activate when I am watching flash in full screen (and like you not when watching something with VLC). The workaround I use it to install the inhibit applet at the top panel so that with one click I can turn on or off the sleep mode. Then I just manually turn it off when watching flash. To install the inhibit aplet go to the top panel, right click, choose Add to Panel, then choose inhibit applet. 

Anyway, I had assumed that the fact that I had to do this was just a limitation that I had to deal with which is why I am curious if your full screen flash automatically disables the screensaver. thx

---

