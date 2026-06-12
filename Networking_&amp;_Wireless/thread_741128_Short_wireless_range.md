---
title: "Short wireless range"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Marcolin on 2008-03-31
Hi all,  I am currently using 8.04 64bit version of Ubuntu and my wireless range is pretty short. It works well as long as my laptop is next to the router but I lose connection if I go into the next room. The only other helpful post I could find on this showed that he was running a Broadcom 4401 device but mine is Broadcome 4312 (link -> [http://ubuntuforums.org/showthread.php?t=649237](http://ubuntuforums.org/showthread.php?t=649237))

When I was running 7.1 x86, everything was fine. I could see my network from anywhere in the house as well as several other networks from the neighborhood. So, I assume that I am currently using the incorrect driver.

I followed instructions from this site to install my wireless driver (kernel version 2.6.24-12-generic) :
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old)

And I just tried following these instructions this morning:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

But my range is still short. When I head into the other room, I lose connection.

I guess I should state that I am new to linux but i am trying to learn as much as I can by running it on my laptop before I make a switch from windows on my desktop. I got everything working fine in 7.1 and decided to try out the latest version. (I did a clean install).

Any help would be greatly appreciated!

---

### Post by lswest on 2008-03-31
Well, looks to me like you installed the right drivers, however, i do notice that the site says a) there are patches required for the bcm4312 on a 2.6.24 system and b) 802.11a is unsupported (though your network is probably running on 802.11g) <-- 802.11a/g refer to frequencies of the signal.

Can you post the output of ```
lshw -C network
```please, so we can see what driver exactly is being used?

---

### Post by Marcolin on 2008-03-31
Sure thing, here it is
```
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:61:d4:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11g
```

I see where it says a patch is required but I dont see any instructions about what patch. Am I just overlooking it?

---

### Post by lswest on 2008-04-01
No, it doesn't name the patch, and i've tried googling it, but haven't found any answers...maybe someone on this forum knows?

---

### Post by rustybronco on 2008-04-01
Possibly because.

[http://lists.berlios.de/pipermail/bcm43xx-dev/2007-February/003919.html](http://lists.berlios.de/pipermail/bcm43xx-dev/2007-February/003919.html)

---

### Post by Marcolin on 2008-04-01
I typed in this ```
lspci -n | grep '14e4:43'
```
which gave me this:
```
03:00.0 0280: 14e4:4312 (rev 01)
```
So, I believe that I dont need the patch since that site says the patch is only required for rev 02.
Also, I found this bug report but the solution it gives is the same thing I used to install initially, so I probably have a different problem.
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/202567](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/202567)

And finally, I found this bug report which states that the b43-fwcutter provided with Hardy doesn't work right. 
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/197819](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/197819)
So, I disabled the driver in Hardware Drivers, rebooted and started again from scratch. But the only thing change that I can see is that Compiz doesn't start anymore. That's pretty retarded.

---

### Post by Marcolin on 2008-04-03
No ideas on this?

---

### Post by wtmann on 2008-04-04
I'm experiencing the same behavior and I'm using the 32-bit version of Hardy on a Fujitsu-Siemens laptop with Intel wireless - the 2200BG. The output from the 'lshw -C Network' command is:

  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth1
       version: 05
       serial: 00:15:00:00:83:ce
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

and the output from iwconfig is (sitting next to the router):

eth1      IEEE 802.11g  ESSID:"wlanMann"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:90:CD:57
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:1F78-AB54-F32C-10F5-9D4D-9521-6EAC-EF86   Security mode:open
          Power Management:off
          Link Quality=84/100  Signal level=-32 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

However, I only need to move about 4/5 meters from the router and I can no longer connect. I've tried both without encryption and with but I always get the same behavior.

I don't think the problem is with Hardy itself as this started happening after my last update to 7.10: a few days before  installing Hardy. So something happened to the wireless stuff with one of the March updates.

Thanks for any help.

---

