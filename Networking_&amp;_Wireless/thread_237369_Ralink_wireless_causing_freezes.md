---
title: "Ralink wireless causing freezes"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by jas20 on 2006-08-16
Note:
I have tried searching and now I'm very confused about what I could do.

My Setup:
I have a Compaq Armada e500 (p3 447mhz) with Ubuntu Dapper on it (almost a fresh install).
I also have a PCMCIA Ralink card (rt2500). The network is protected by WEP. It uses the built in driver (no ndiswrapper or rt2x000)
It gets it's internet from the network. The internet can also be access through this computer I'm using now.

The freezes:
I have read some some peoples computers freeze on boot-up, some randomly. Mine is more of a random one. It freezes after connecting to the network (it takes a few minutes, sometimes an hour).

Kernel:
I have read that SMP kernels cause problems with the rt2500. I'm not sure if mine has this.
Using "uname -a" I get:
```
Linux Jason 2.6.15-23-386 #1 PREEMPT *DATE/TIME* i686 GNU/Linux
```
I don't see SMP there, I see 386 which I read isn't SMP (but I could be wrong).

Does anyone have anyone ideas on what I could do to try and get it working well?

Final notes:
Downloads can be done through this PC (zip type files), but packages have to be small to get through quick enough.
I'm not very experienced with Ubuntu, and my install is very basic.

---

### Post by JDAAINOKI on 2006-08-16
Jas, 
Your kernel is good and not SMP.  I've had problems with my Ralink mini-pci on every new install, but fortunately I've always been able to work around it.  Have you tried an other PCMCIA devices in the same slot? What is the output of cardctl ident (w/ card inserted, but not up) Try booting with the recovery mode (cli) kernel image and see if you can bring up the interface manually.  My most recent problem involved some kind of conflict with my video adapter and wifi card.  Can you post the output of the following:

cat /var/log/syslog
dmesg | grep Ralink 
dmesg | grep pcmcia
iwconfig 
ifconfig -a

Thanks I'll be on later to check for your posts.
Good Luck,
Jay

---

### Post by jas20 on 2006-08-16
I can't get "cardctl ident" to work (I tried adding "socket 0" onto the end and trying various numbers and words such as "ra0"). I understand how to make it "not up".

Neither of the "dmesg" work. Are they suppost to?
The cat thing is very long and it has been a long time since it has froze (I pull it out when I'm not using it, just to stay 'alive').

I'll do a reset and try and crash it (it probably won't now that I want it to).

iwconfig:
> lo        no wireless extensions.

sit0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"EDITED"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:E9:04:00:FC
          Bit Rate:54 Mb/s
          RTS thr: off   Fragment thr: off
          Link Quality=88/100  Signal level=-48 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

* The RTS line was edited to prevent a smilie from appearing, remove the space between "thr:" and "off".

ifconfig -a:
> lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:125883 (122.9 KiB)  TX bytes:125883 (122.9 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:4D:EB:20
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe4d:eb20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:48 txqueuelen:1000
          RX bytes:2009576 (1.9 MiB)  TX bytes:595984 (582.0 KiB)
          Interrupt:11 Base address:0xc000

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---

### Post by lupine_nickt on 2006-08-16
I'm using the rt2570 (USB, that's the only real difference) driver; my experience (with older versions of the driver) has always been that it crashed the system when the USB stick was removed; it's possible that something similar is happening with your PCMCIA card - maybe it's being switched off by power management or something?

Anyway, driver updates are the order of the day. Firstly, you can do a full system upgrade - "apt-get update" followed by "apt-get upgrade" (or do it in Synaptic/Adept). That'll update your kernel to the latest version (-26), which might solve the problem.

If not, then you could try downloading and compiling the most recent driver from the rt2x00 website -- not the rt2x00 driver itself! (because it's still mondo unstable), but the rt2500 driver.

Two options - the [fourth beta](http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download) or the [nightly CVS](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz) -- try the second one first. The driver that ships with the Ubuntu kernel is only the beta 3, so it's missing ~ a year of development work ('strings rt2500.ko' gives 'description=Ralink RT2500 802.11g WLAN driver 1.1.0 BETA3 2005/07/31'). 

To build and install them, you'll need to install the linux-source package. You'll also need to remove the current rt2500.ko file (which is located at /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/rt2500 for the newest kernel). To keep it as a backup, your best bet is to move the file to your Desktop, until you're sure that the newest version is working :)

Good luck with it!

xF,

...Nick

---

### Post by jas20 on 2006-08-16
Just crashed... Here is my dmesg results:
[http://jas2o.forthworks.com/dmesg.txt](http://jas2o.forthworks.com/dmesg.txt)

Turns out I was using the ident thing wrong.,.. But it has nothing to display.

There is no freeze on: a) bootup b) on connect c) on pull out
But the signal bar always drops when it freezes...

I'm using dialup (across wireless, yes it sounds insane but works well) so I'll do that stuff tomorrow when I have the time (goto leave soon).

Thanks, I'll try those tomorrow :)

Edit: Quick check, "apt-get upgrade" is 102 mb, I'm not doing that. Going through Synaptic... Linux-386 ? That it? That's 30mb for me (includes 2 other things)...

---

### Post by lupine_nickt on 2006-08-16
linux-386 is the kernel upgrade, yes.

The kernel sources (for compilation of the newer drivers) are linux-source-2.6.15

xF,

...Nick

---

### Post by JDAAINOKI on 2006-08-16
Jason,
I would think you could change something in your /etc/pcmcia/config.opts file or give a reserve=XXXXXX, XXXXX (where X = a memory range) added to boot in order to fix this problem; however, I will need to do some research to offer any advice on that.  Go ahead read the bug report below and try some of the suggested fixes. I know my Dapper/RT2500 problem stemmed from some sort of video driver/rt2500 conflict when they were sharing the same IRQ. A few others have had the same problem. 

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34902]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34902")

Good Luck, 

Jay

---

### Post by jas20 on 2006-08-17
Ok I have managed to get this winmodem connected to the internet (lucky the driver is included now) so I can do some work without the card.

Thanks for the suggestions, will try them now...

---

### Post by jas20 on 2006-08-17
(Sorry for double post)

I've disable IRQ through the GRUB menu, it's working nicely. But I'll keep testing.

Edit later: Damn :( It crashed twice within 10min.

I'll try the kernel and driver stuff when I get the internet back on here.

---

### Post by JDAAINOKI on 2006-08-17
Jas,
What's your output for cat /proc/interrupts? Try changing your video driver to vesa under the /etc/X11/xorg.conf file.  Just scroll down until you see your video adapter and test it out.  This is the section I changed in mine:
```
 Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "vesa" 
        BusID           "PCI:1:0:0"

```

I changed to vesa from via and my card worked like a champ.

Good Luck,
Jason

---

### Post by jas20 on 2006-08-17
Here is the cat /proc/interrupts :
```
           CPU0
  0:   12052631          XT-PIC  timer
  1:      17357          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          2          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:         33          XT-PIC  acpi
 11:     685045          XT-PIC  uhci_hcd:usb1, yenta, yenta, ltserial, ESS Maes tro, ohci_hcd:usb2, ohci_hcd:usb3, ehci_hcd:usb4, ra0
 12:    2258688          XT-PIC  i8042
 14:     269148          XT-PIC  ide0
NMI:          0
LOC:          0
ERR:          0
MIS:          0

```

The driver already is vesa.

---

### Post by lupine_nickt on 2006-08-17
Jas,

Present for you :)

I've attached on here two rt2500 modules that I just compiled for the -23 kernel ( V down there V ). One is the b4, the other is the current CVS.

Just a standard 'make', no dodgy extras, I promise :). They're ~90KB each, so easily downloadable over dialup. You don't need a kernel update or kernel sources to make them work.

Feel free to give them a try - as I said before, just backup your current module, copy this one in, and see what happens. If it goes badly (can't see why it would, though) you can always restore your current version over the top of it.

Your current module will probably be in one of (or a subdir of):-
/lib/modules/2.6.15-23-386/kernel/drivers/usb/net
/lib/modules/2.6.15-23-386/extra

---

### Post by jas20 on 2006-08-18
Ok I have put it in... Will be testing from now.

Thanks!

Edit: It seem to have froze, but not a total freeze (could reset gnome). Maybe it was something else that caused that one.

---

### Post by jas20 on 2006-08-18
Hmmm... It unlocks when I pull out my PCMCIA usb card. This wasn't the case before (it would freeze completely).

So what to do about that card?

---

