---
title: "Screen goes blank during VLC playback and after switching to virtual console and back"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by bolucpap on 2009-04-06
Hello, I just got an Acer aspire one and ran into a problem I also had with my wife's Aspire 5710. I boot up 8.10, and everything is fine until I hit ctrl-alt-f1 to access console. When I hit ctrl-alt-f7 to get back to the X screen (gnome desktop), I get a blank screen. The X system is working fine, if I am playing music, I can still hear it, only the display is gone. If I hit ctrl alt backspace to restart the X server, I hear the drum roll sound of the gdm, but the black screen persists. I use "sudo htop" to find and kill the X process, and 1 out of five tries I get the display back. The same thing happens when I play a movie in VLC in full screen mode. After about three or four minutes of full screen playback, the screen goes black. The movie keeps playing in the background, I can hear the sound. The same scenario I wrote about the ctrl alt f1-ctrl alt f7 plays out. This does not happen if I play a movie in windowed mode, though. Unfortunately, I have this problem both on an Acer Aspire One and an Acer 5710. Any thoughs?

Thanks in advance.

---

### Post by 24*7 on 2009-04-06
> **bolucpap said:**
> Hello, I just got an Acer aspire one and ran into a problem I also had with my wife's Aspire 5710. I boot up 8.10, and everything is fine until I hit ctrl-alt-f1 to access console. When I hit ctrl-alt-f7 to get back to the X screen (gnome desktop), I get a blank screen. The X system is working fine, if I am playing music, I can still hear it, only the display is gone. If I hit ctrl alt backspace to restart the X server, I hear the drum roll sound of the gdm, but the black screen persists. I use "sudo htop" to find and kill the X process, and 1 out of five tries I get the display back. The same thing happens when I play a movie in VLC in full screen mode. After about three or four minutes of full screen playback, the screen goes black. The movie keeps playing in the background, I can hear the sound. The same scenario I wrote about the ctrl alt f1-ctrl alt f7 plays out. This does not happen if I play a movie in windowed mode, though. Unfortunately, I have this problem both on an Acer Aspire One and an Acer 5710. Any thoughs?

Thanks in advance.
Why don't u use terminal instead of going to console each time? Isn't it a bad practice?

---

### Post by nandemonai on 2009-04-06
> **24*7 said:**
> Why don't u use terminal instead of going to console each time? Isn't it a bad practice?

Still doesn't address the issue they're having with full screen video.

My suggestion would be to paste the output from lspci so we can see what video chipset it uses and take it from there.

---

### Post by bolucpap on 2009-04-06
The lspci output is as follows:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
As for the ctrl alt f1 issue, it's something I do out of habit of when linux was older and needed such countermeasures against freezes etc. It's a feature I can stop using, but I don't want to be left in a position where I hit ctrl alt whatever accidentally (which happens if you use vmware, like me) and then I have to kill my session.

---

### Post by bolucpap on 2009-04-06
I found a documented bug that seems to fit the description of my problem. [http://bugs.freedesktop.org/show_bug.cgi?id=18032]("http://bugs.freedesktop.org/show_bug.cgi?id=18032")
However, the discussion is too technical for me, although I can see the status is resolved and there is a comment on it that I take to mean that it is a duplicate of another bug. I read the entry for that bug as well, but it doesn't mean much to me. Can anyone tell me how to resolve my issue(s) based on those pieces of information?

Thanks in advance.

---

### Post by bolucpap on 2009-04-07
bump?

---

### Post by bolucpap on 2009-04-17
This issue no longer exists as of Jaunty Beta, hope there are no regressions in the future :-)

---

