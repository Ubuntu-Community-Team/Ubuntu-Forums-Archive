---
title: "Wireless Configuration Problem"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by jdc8890 on 2006-08-13
Hello,
I have a Belkin FD58000 Wireless Network Card which I am trying to configure with Ubuntu.  It is not natively linux-supported, so I had to use ndiswrapper to install the driver which seemed to work fine.  However, I cannot seem to get the network card to connect to my network.  It uses a PCI to PCMCIA adapter and then the network card plugs into the PCMCIA adapter.  Maybe the PCMCIA adapter is causing some issues?  The following are the outputs of ifconfig and iwconfig:

**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Auto  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**ifconfig:**
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:60847 (59.4 KiB)  TX bytes:60847 (59.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:2E:57:51
          inet6 addr: fe80::211:50ff:fe2e:5751/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:52000000-52080000

Thanks for the help!

-Josh

---

### Post by jdc8890 on 2006-08-13
Help ASAP is greatly appreciated! Thanks!

---

### Post by JDAAINOKI on 2006-08-13
josh,

I'm trying to track down a similar problem I'm having. What kind of computer are you using? Also, do you know if you are sharing memory for your video card? Can you post the following:

```
cat /proc/interrupts
```
and 

```
dmesg | grep Dis 
```

and

```
lspci | grep VGA 
```

It looks like your card is powered off too. Try:
```
iwconfig wlan0 power on
```

Good Luck,
Jay

---

### Post by jdc8890 on 2006-08-13
Hi Jay,
Thanks for all the help.  I tried turning on the wireless card like you suggested, but it didn't seem to help at all.  In addition, I am not sharing my on-board memory for video.  I am running Ubuntu 6.06 on an external USB hard drive on a Dell XPS desktop.  Here is the output you requested:
```

cohen@JDC-Computer:~$ **cat /proc/interrupts**
           CPU0
  0:     143626    IO-APIC-edge  timer
  7:          0    IO-APIC-edge  parport0
  8:          4    IO-APIC-edge  rtc
  9:          1   IO-APIC-level  acpi
 14:        116    IO-APIC-edge  ide0
 15:      16577    IO-APIC-edge  ide1
169:      33371   IO-APIC-level  yenta, ndiswrapper
177:         33   IO-APIC-level  libata, uhci_hcd:usb3
185:      63074   IO-APIC-level  uhci_hcd:usb1, uhci_hcd:usb4, radeon@pci:0000:01:00.0
193:         32   IO-APIC-level  uhci_hcd:usb2
201:          3   IO-APIC-level  ohci1394
209:      44757   IO-APIC-level  ehci_hcd:usb5
225:       1966   IO-APIC-level  EMU10K1
NMI:          0
LOC:     143468
ERR:          0
MIS:          0

cohen@JDC-Computer:~$ **dmesg | grep Dis**
[17179572.240000] SELinux:  Disabled at boot.
[17179573.128000] PnPBIOS: Disabled by ACPI PNP
[17179573.144000] VFS: Disk quotas dquot_6.5.1
[17179681.448000] lo: Disabled Privacy Extensions

cohen@JDC-Computer:~$ **lspci | grep VGA**
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]

```

Again, thanks for all of your assistance!

-Josh

---

### Post by JDAAINOKI on 2006-08-13
Josh,
Im going to do some tests on my laptop to see what I can come up with.  Change the USB devices around and see how works.  Also, try booting with the recovery mode (cli only) and bring up your interface there. Ping your AP and google to see if you can get a return.  While there post your cat /proc/interrupts again.  I'll be back shortly.

Jay

---

### Post by stupidkid on 2006-08-13
iwlist wlan0 scan

If it doesn't detect any wireless networks then your card is probably not installed correctly.

---

### Post by jdc8890 on 2006-08-16
I think my card is installed and working properly; I just think there is a configuration problem as it cannot connect to my network. iwlist wlan0 scan does indicate that my netowrk is avaliable.  I'm going to try it in recovery mode and see what happens.  I'll post back later.  Thanks for all the help.

-Josh

P.S.-Any other suggestions would be very helpful. Thanks!

---

### Post by jdc8890 on 2006-08-19
Some help please!!! Thanks.

-Josh

---

### Post by mikecar52 on 2006-08-19
did you add any info to kwifimanager.  I think there is an add to boot command

---

### Post by nidontknow on 2006-08-19
Hello all, 

I'm having the exact same problem. I have both wifi-radar and network-manager installed. My computer detects my atheros network card but I recieve the "Access Point: Not-Associated" as well.

Interestingly, when I initially installed Ubuntu I got an immediate connection. Suddenly one day my connection timed out and I have been unable to connect since. My eth0 is operable, however. 

Any ideas?
Nathanial

---

### Post by jdc8890 on 2006-08-21
Anyone out there have any suggestions??? Any help would be great. Thanks!

-Josh

---

