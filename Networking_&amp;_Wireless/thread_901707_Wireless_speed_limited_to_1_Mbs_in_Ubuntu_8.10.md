---
title: "Wireless speed limited to 1 Mb/s in Ubuntu 8.10"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by BBirdtree on 2008-08-26
Hi

after installing ubuntu 8.1 (due to new disk), wireless works but limited to 1 Mb/s which is very slow for downloads/file transfer.

> driver --rt2500pci
speed 1 Mb/s

This is from connection information.

from lshw -C network --
 *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wmaster0
       version: 01
       serial: 00:90:4b:c5:8a:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.3 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g


Previously with 7.1 the wan worked at normal speed.
Don't no what to do and other posts don't help at all.
thanks.

---

### Post by hacksaw1340 on 2008-09-17
I see the speed listed as 1mb in the utility.  1mb.  but if I do a iwconfig I actually see a higher speed as seen below. I can transfer files much faster than the 1mb rate.  

wlan0     IEEE 802.11g  ESSID:"GS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:7C:7B:73:C1   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=80/100  Signal level=-48 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by terrypen on 2008-09-18
I'm seeing 2Mbps in the information and 1Mbps using iwconfig. How can I speed this up?

---

### Post by BBirdtree on 2008-09-19
I followed the solution on [768301]("http://ubuntuforums.org/showthread.php?t=768301") and it worked. good luck.

---

### Post by freek_zero on 2008-10-19
The "iwconfig rate 54M" solution linked to above did not work for me. It did not seem to work "except temporarily in some cases" with 8.04 either.

The serialmonkey rt2x00 driver worked beautifully for me under 8.04 but it wouldn't do WPA2 for me. I tried ndiswrapper with 8.10 and it also won't work with WPA2 (sits there in "acquiring network address" until it times out). The built-in driver does WPA2 beautifully, but sits at ~100kB. Which is better than the ~70kB it did under 8.04 mind you.

Any other ideas?

Why of why is this still a problem? Given the amount of discussion of this exact problem I've seen, and the fact that it's been ongoing for well over a year (I've seen posts going back to ubuntu 6) it strikes me as unconscionable that this is still a bug. I desperately wish I could submit a fix myself but sadly the LAMP skillset doesn't apply well to fixing drivers.

---

### Post by kmb101 on 2008-10-20
I am having the same problem in 8.04. Mine connected at 54Mb/s before the kernel upgrade on Oct 14 now it only connect at 1Mb/s which is very slow to me now. I have the broadcom 4318 card with the b43 driver. Nothing I have done so far has worked. I have used iwconfig wlan0 rate 54M command but it doesn't work it makes me loose my connection and network. I hope someone has and answer soon. I believe this is a bug in the update.

---

### Post by freek_zero on 2008-10-22
I don't know if it's the specific way of setting the rate that did it, or the dozen combinations of drivers (stock, legacy serialmonkey, ndiswrapper) and network setup methods (wpa_supplicant, alternate wpa, network manager, rautil), but it works for me now with the stock (rt2x00) driver and network manager. "It works" meaning WPA2 and proper speed.

The trick seemed to be setting the rate to 2MB, then to auto. On auto it moves itself to 54M pretty quick. Previously setting 54M directly did not work.

Now if i could just get bluetooth audio to work well...

---

### Post by Hexagoon on 2008-10-22
Has anyone tried a reliable bandwidth test? The numbers in iwconfig etc. is far from always the fact.

---

### Post by nrune on 2008-10-26
My solution to all this was to use this command

```
sudo iwconfig xxxxxx rate 54M
```

long term fix 


```
pre-up iwconfig wlan0 rate 54M
```

to /etc/network/interfaces then run

```
sudo /etc/init.d/networking restart
```

Also install wicd and get rid of network manager. 

Good luck to all.

---

