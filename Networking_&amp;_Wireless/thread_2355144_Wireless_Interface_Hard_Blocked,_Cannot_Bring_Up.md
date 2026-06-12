---
title: "Wireless Interface Hard Blocked, Cannot Bring Up"
date: 2017-03-09
forum: Networking &amp; Wireless
---

### Post by ph423 on 2017-03-09
[This is a sister post to [this post]("http://askubuntu.com/questions/891394/wireless-interface-hard-blocked-cannot-bring-up") on Ask Ubuntu]

Hi! Recently my networking has been acting up, and since yesterday I have lost all ability to use my wifi network adapter.

As to describe the way the networking was acting up, the network-manager would sometime lose connection of wifi and connect on the ethernet iface (without any viable connection). This has happened in the past, but I noticed it happened more frequently over the past few days (3-4 days or so) and was most noticeable when bringing the computer up from sleep.
I started investigating after I lost connection to the internet this morning, and I found out that the wlan interface (listed as wlp3s0) wasn't present in ifconfig. Trying to bring it up via `sudo ifconfig wlp3s0 up` resulted in `SIOCSIFFLAGS: Operation not possible due to RF-kill`.


`sudo rfkill list all` results in the following:
```

0: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes

```
Thus showing that the lock is hardware based, not software based. Consequently I:
- ensured that my airplane mode switch wasn't turned on (tbh, I have no idea which side of it is airplane on, but I rebooted for both states of the switch, so that shouldn't be a problem)
- have attempted to use the network function key on the laptop (Fn + F5), to no avail
- have ensured the lock wasn't from the BIOS options (checked the I/O Security as well as Network options)
- have attempted to boot from an older image of my OS
- have attempted to boot from a live Ubuntu ISO (16.04) ; did not result in any change network-wise
- have attempted to do a soft unblock via `sudo rfkill unblock all` 


**So time to bring the big guns.**


Laptop model name: 
```
LENOVO Thinkpad T430s 2352CT0/2352CT0, BIOS G7ET99WW (2.59 ) 03/18/2014
```
`uname -a` resulted in the following output:
```
Linux 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
``` 
`lspci` resulted in the following output:
```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)

```
`lshw -c network` resulted in the following output:
```

*-network
description: Ethernet interface
product: 82579LM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: enp0s25
version: 04
serial: 3c:97:0e:95:07:f6
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
resources: irq:28 memory:f3500000-f351ffff memory:f353b000-f353bfff ioport:6080(size=32)
*-network DISABLED
description: Wireless interface
product: Centrino Ultimate-N 6300
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlp3s0
version: 3e
serial: 3c:a9:f4:38:36:ac
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-66-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
resources: irq:33 memory:f2c00000-f2c01fff

```
`ifconfig -a` resulted in the following output (eth0 => enp0s25, wlan0 => wlp3s0):
```

br-5683354b17cb Link encap:Ethernet HWaddr 02:42:e8:3c:ec:f5 
inet addr:172.18.0.1 Bcast:0.0.0.0 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
docker0 Link encap:Ethernet HWaddr 02:42:c1:3b:54:07 
inet addr:172.17.0.1 Bcast:0.0.0.0 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
enp0s25 Link encap:Ethernet HWaddr 3c:97:0e:95:07:f6 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Memory:f3500000-f3520000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:11358 errors:0 dropped:0 overruns:0 frame:0
TX packets:11358 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1 
RX bytes:834988 (834.9 KB) TX bytes:834988 (834.9 KB)
wlp3s0 Link encap:Ethernet HWaddr 3c:a9:f4:38:36:ac 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```
`iwconfig` resulted in the following output:
```

wlp3s0 IEEE 802.11abgn ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=off 
Retry short limit:7 RTS thrff Fragment thrff
Encryption keyff
Power Managementff

```
`iw dev` resulted in the following output:
```

phy#0
    Interface wlp3s0
        ifindex 3
        wdev 0x1
        addr 3c:a9:f4:38:36:ac
        type managed

```


`dmesg` resulted in the following output. The most interesting part is at 3.695787s through 3.74s: 

[See Pastebin]("http://pastebin.com/qAcfkJRL")

`apt-cache policy linux-firmware` resulted in the following output:
```

linux-firmware:
Installed: 1.157.8
Candidate: 1.157.8
Version table:
*** 1.157.8 500
500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
100 /var/lib/dpkg/status
1.157 500
500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
500 http://ca.archive.ubuntu.com/ubuntu xenial/main i386 Packages

```


I also took other prints, most notably recent `/var/log/apt/history.log`, as well as `journalctl -b`, `modinfo iwlwifi`, `modinfo iwldev`, and `modinfo mac80211`. Let me know if you would like any of those, I'll add them to this post.
At this point I am quite out of solutions. I have searched through archlinux, gentoo and ubuntu forums without any success. **Any help would be greatly appreciated!!!!** :) :) :)  
Cheers

---

### Post by jeremy31 on 2017-03-09
I think you have a plausible answer at askubuntu as it appears that your Lenovo has a hardware switch to disable wireless

---

### Post by ph423 on 2017-03-10
Hi Jeremy! Thanks for the answer. I have checked the switch already (as stated in the OP). I will however check the hardware directly cause I did have some issues with that switch 3 years ago when I was under warranty. Maybe there's something I can figure out.

---

### Post by ph423 on 2017-03-11
[COLOR=#111111][FONT=Ubuntu]After dismantling the computer, I removed a large ball of dust that got stuck in the airplane switch due to one of the corner of my computer being slightly broken. The switch is now nice and clicky, but still no changes whatsoever. 

As an alternative, I bought a Netgear AC1200 A6210 and installed [/FONT][/COLOR][jurobystricky's driver]("https://github.com/jurobystricky/Netgear-A6210")[COLOR=#111111][FONT=Ubuntu], without any success. In the end all it did was crash my entire computer due to some segfault.

Ethernet works fine, so at least there's that. Any suggestions would be greatly appreciated :)[/FONT][/COLOR]

---

### Post by ph423 on 2017-03-12
**[UPDATE]:**[COLOR=#111111][FONT=Ubuntu] I have installed a D-Link AC1200 DWA-182 Wireless USB adapter using [/FONT][/COLOR][this tutorial]("http://cfyves.com/2015/03/17/how-to-install-d-link-dwa-182-wireless-ac1200-dual-band-usb-adapter-on-linux-ubuntu/")[COLOR=#111111][FONT=Ubuntu], and unfortunately this one doesn't work either. However printing [/FONT][/COLOR]lshw -c network[COLOR=#111111][FONT=Ubuntu] returns the device as [/FONT][/COLOR]**DISABLED**[COLOR=#111111][FONT=Ubuntu], while [/FONT][/COLOR]rfkill list all[COLOR=#111111][FONT=Ubuntu] returns the device as [/FONT][/COLOR]**neither hard or soft blocked**[COLOR=#111111][FONT=Ubuntu]. I'm sure that this information can provide a crucial piece to the puzzle.[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-03-12
Can you post the lshw -c net results?
Also see what happens with ```
sudo ifconfig wlp3s0 up
```

---

### Post by ph423 on 2017-03-13
There you go:

```

  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: 3c:97:0e:95:07:f6
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-3 ip=192.168.1.138 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:33 memory:f3500000-f351ffff memory:f353b000-f353bfff ioport:6080(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 3e
       serial: 3c:a9:f4:38:36:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-66-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f2c00000-f2c01fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@3:2
       logical name: wlxa0ab1bf2aaf9
       serial: a0:ab:1b:f2:aa:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au multicast=yes wireless=unassociated

```

sudo ifconfig wlp3s0 up : SIOCSIFFLAGS: Operation not possible due to RF-kill


sudo ifconfig wlxa0ab1bf2aaf9 up: No output, but no change in the System Settings > Network window either. Interesting note here is that by default in that window the Airplane Mode is ON, can be turned off, but the Wireless cannot be turned ON on both interfaces (clicking the ON switch resets back to OFF).

---

### Post by jeremy31 on 2017-03-13
See the wireless script link in my signature and post results

---

### Post by ph423 on 2017-03-13
Hi! You can find the output [here]("http://paste.ubuntu.com/24172743/"). Pretty impressive of a diagnostic script imo :O

---

### Post by jeremy31 on 2017-03-14
See if you can do what is in this video [https://www.youtube.com/watch?v=yzAKcmlaH1M&t=3s](https://www.youtube.com/watch?v=yzAKcmlaH1M&t=3s) as it should fix the switch issue

---

### Post by ph423 on 2017-03-15
Hi Jeremy,

I'm looking into it. Turns out the pinout is quite different on this chip, so finding the schematics turned out to be problematic. I'm in contact with Intel to get more info on the chip.

Cheers,
Philippe

---

### Post by jeremy31 on 2017-03-15
The pinout should be standard among all chips it just that some chips don't use all the pins so there will not be a contact point in every position
If the back of your card looks like [https://www.fdgate.com/photo-3/dual-band-450mbps-802-11a-g-n-half-size-mini-pci-e-for-ibm-intel-6300-agn-pcie-wireless-hotspot-wifi-card-60y3233-2-4ghz-5ghz.jpg](https://www.fdgate.com/photo-3/dual-band-450mbps-802-11a-g-n-half-size-mini-pci-e-for-ibm-intel-6300-agn-pcie-wireless-hotspot-wifi-card-60y3233-2-4ghz-5ghz.jpg) I would put the tape on the middle pin in the group of 3

---

### Post by ph423 on 2017-03-17
Hi Jeremy,

Thanks again for your help, you are the only one that sheds light on the problem. It is much appreciated :3

Indeed the card looks like the photo you provided. the exact chip is the [following]("https://ae01.alicdn.com/kf/HTB11Ig9HVXXXXXvXpXXq6xXFXXXY/Int-Centrino-Ultimate-N-6300-633ANHMW-For-Lenovo-Thinkpad-X200-X201-X220-X230-T410-L410-T420.jpg"). 

Are you sure that the middle pin of the group of 3 is the one of interest here? Also, what are the potential consequences of taping the wrong pin? Could it short the chip or the motherboard?

Cheers

---

### Post by jeremy31 on 2017-03-17
I am sure it is the correct one after seeing this picture [http://ecx.images-amazon.com/images/I/51M3tLs4r%2BL.jpg](http://ecx.images-amazon.com/images/I/51M3tLs4r%2BL.jpg)

---

### Post by praseodym on 2017-03-17
Tried this:

[https://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](https://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by ph423 on 2017-03-19
Hi all,

Jeremy: I'll attempt your solution tomorrow - Want to do some work before starting to play with my hardware.
praseodym: Thanks for your help :) I have attempted all of these solutions already via the BIOS. Glad to see that there is a similar solution detailed online.

[UPDATE]: I mistakenly did Ctrl+Alt+F4 and then I kept getting some message about being unable to load ucode with error -5 and -132. I tried to reboot via sudo shutdown, but it caused a segfault and I had to force shut down using the power button. When I booted back up, I was able to get wifi out of the blue, but only intermittently. Looking at the [dmesg]("http://pastebin.com/4dWH2JTD") printout I believe we have found confirmation that the switch is indeed the source of the problem - the rfkill hardware switch keeps flickering on and off. More evidence for me to do Jeremy's solution.

---

### Post by ph423 on 2017-03-19
Alright, so I have done Jeremy's solution.
I am now able to get a wireless signal and connect to access points. Using rfkill list all, the interface shows up as neither hard or soft blocked.
However the wireless keeps turning on and off. Using rfkill list all shows that the interface becomes intermittently soft-blocked. I have rerun the wireless-info script: [http://paste.ubuntu.com/24213142/](http://paste.ubuntu.com/24213142/)

---

### Post by ph423 on 2017-03-24
Since I have access to a wired connection at home, I didn't really get the time to look more into it.
Now I have decided to look into it. For the time being, I wrote a little script that I have put in rc.local to run at boot.
The said script is meant to catch any soft block event and programmatically unblock the affected interfaces. This allows a nigh seemless experience, but is far from being elegant.
Here is the script:
```

rfkill event | grep --line-buffered "soft 1" | while read line ; do id=`echo $line | grep -o "idx [[:digit:]]*" | grep -o "[[:digit:]]"`; rfkill unblock "$id"; done;

```

I'll be digging more to see if there is a permanent, less bodged solution. Let me know if you find anything.

---

