---
title: "Ubuntu drops internet"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by jesusaves on 2007-10-10
I have a shared DSL connection using a Linksys BEFSR41 router here in our home. Two systems share the connection, the first being a Windows XP device and the other being Ubuntu 7.04 desktop distro. First problem I noticed was that when I get on the internet with the Linux box it causes a loss of internet on the Windows box. I hope that someone might be able to assist me in fixing this issue. Below I have listed the output of "/lspci" 

00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
[COLOR="DarkOrange"]00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10[/COLOR])
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)

Now when I try to run /sbin/lspci I get nothing in response. Honestly, this system is rather awesome and I love Ubuntu, I just need to resolve the internet issue.  Any help would be awesome.

Thank you
JS

---

