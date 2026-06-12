---
title: "A wireless card that works in 6.6 but not 7.4"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by randavance on 2007-05-04
I have been using Linux since I was little, and Ubuntu for the past few years. Thus far, I have loved the distro up until here. I'm not sure what kind of wireless card I have except that it is a netgear. It's connects to my fathers network dubbed "WombatWonderland" (which you'll notice on the data I'll give you.

I have run 6.6 for a long time now and when finally installing a fresh 7.4 I realized that it does not work with my network. It turns out, 6.10 and 7.4 both do not recognise my wireless card. I'm actually typing this from my computer with a 6.6 install. I have a separate partition with a fresh 7.4 which I love, but no network connection. I have a 3rd partition that I installed a fresh 6.6 and then upgraded to 7.4. The internet worked great until the end of my upgrade when I had to restart the computer and ended up once again with an unrecognizable wireless card.

Running **lspci** in my 6.6 install I get this data...

> \0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:04.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
0000:01:05.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
0000:01:05.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
0000:01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


Running **iwconfig** on my working 6.6 install I get this...

> lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"WombatWonderland"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:09:5B:AB:76:22
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/92  Signal level=-43 dBm  Noise level=-144 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

I figured it might be a simple matter of maybe copying over a configuration file out of etc from my 6.6 to my 7.4 distro, but so far I can't figure out what that file is. There seems to be a network management change going 6.6 to 6.10.

Any help is greatly apreciated. I will post the data I pull out of those same commands output from my not working 7.4 connection in a little bit. Thank you.


**Edit:**

Running **ispci** on my 7.4 nonworking install I get this....

> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
01:05.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
01:05.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

Running **iwconfig** on my nonworking 7.4 install I get this...

> lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     no wireless extensions.

---

### Post by chili555 on 2007-05-04
> Network controller: Intersil Corporation Prism 2.5 WavelanI love my Prism card, too. However it often tries to load too many modules, prism2, orinoco and hostap. They end up fighting for domination of your computer instead of working. You can check with:```
lsmod | grep prism2
lsmod | grep hostap
lsmod | grep orinoco
```If you get a few words of text, the module is loaded. If you get nothing, it's not. If prism2_xx appears, as well as the others, we need to blacklist prism2_whatever_you_found. *sudo gedit /etc/modprobe.d/blacklist* Add:```
blacklist prism2_whatever_you_found
```Save and close gedit, reboot and let us know.

---

### Post by randavance on 2007-05-06
bump

---

### Post by kvonb on 2007-05-06
Did you try what chili555 suggested?  It's customary to report back with your findings, people can help you better then!

There are quite a few wireless cards and other things that no longer work in Feisty, hopefully they will be fixed in the coming month!

Have you searched the forum for "preism"?  I'm sure you'll find plenty of threads dealing with that particular card.

---

### Post by randavance on 2007-05-06
Sorry I didn't respond. I was working all weekend and just now got a chance to try this all. It works great. I checked with "lsmod | grep prism2", ended up with a couple of lines of info (I didn't copy them, I should have), the first of which was "prism2_pci" and just as chili555 sudgested I added "blacklist prism2_pci" to /etc/modprobe.d/blacklist. I rebooted my computer and my wireless connection works just fine. My network card is recognized just like on my 6.6 installation.

I can't thank you enough chili555!

---

### Post by yusufm on 2007-05-09
Thanks a lot for the directions. I had burnt quite a few hours trying to search for a fix and trying different things without success. Your directions worked great.

This should go up somewhere prominent on the troubleshooting page.

---

