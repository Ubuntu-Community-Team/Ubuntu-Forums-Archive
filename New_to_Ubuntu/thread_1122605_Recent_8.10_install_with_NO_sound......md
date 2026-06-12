---
title: "Recent 8.10 install with NO sound....."
date: 2009-04-11
forum: New to Ubuntu
---

### Post by baconn on 2009-04-11
I just bought a Dell mini 9 and dumped the dell version adn installed Ubuntu 8.10 from a bootable USB drive I created.  The problem is that I can't hear ANY sound, not at start up and not on any websites.  The good news is that I can now view videos in Youtube and other sites where i couldn
t before but now can't hear  them.  Here is a list of my PCI:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
**[B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**[/B]
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Any thoughts on how to get audio working?????

---

### Post by zvacet on 2009-04-11
System>preferences>sound and select automatic detect or anything else (ALSA for example).Check sound there.Under **system>preferences** you will find **volume control**.Be sure to choose from preferences master,PCM and front and that they are not mute and push buttons up.

---

### Post by baconn on 2009-04-11
Thanks for responding. 
Tried that and set to autodetect.  Double clicked on volume control and nearest selection is Alda  Mixer for HDA Intel so chose that.  Set  Master and the other two to full blast, tested  it on both websites and on music and still nothing.  Was working before removed Dell's junk so I would like to make it work with just Ubuntu on it's own, not associated with Dell adn the extra  stuff they make you take.  

I think there must be a driver somewhere that I need but where?  

Thanks.

---

### Post by baconn on 2009-04-12
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

this is a link that i found that worked to restore the sound to my Dell mini 9 after I reinstalled Ubuntu 8.10.  In fact, the sound is louder AND clearer than on the original Dell pre-installed Ubuntu.

For all those with a Dell mini 9, please refer to the link above.

Thanks!

Baconn    :p

---

