---
title: "5g not showing up"
date: 2015-03-30
forum: Networking &amp; Wireless
---

### Post by jmelton on 2015-03-30
My hard drive recently died and, when the new HD was put in and Ubuntu 14.04 and Windows 8 were reinstalled, I was no longer able to see the 5g from my wireless in either OS. I know the router is not the issue, though, because I can still connect to 5g on both my Mac and my Android without any problem. What could be going on? Could it be a wireless card driver issue? My machine is a Dell Inspiron 3520, and the router is a Netgear WNDR3400v3. I've never had a problem before and I've had this computer and these OS's for a couple of years now.

---

### Post by ajgreeny on 2015-03-30
What exactly is this 5g that you can not see?

I don't understand your problem at the moment.

---

### Post by kurt18947 on 2015-03-30
> **ajgreeny said:**
> What exactly is this 5g that you can not see?

I don't understand your problem at the moment.

Just guessing here - 5g**hz**?

---

### Post by rigged 00 on 2015-03-31
Hi
Just a guess, but if it is affecting both the Windows and Linux partitions then it might be that what ever caused your HDD to die could have damaged the WiFi Nic. 
Or maybe if it is a onboard NIC it might be a BIOS setting that is missed.

---

### Post by Vladlenin5000 on 2015-03-31
Or maybe you haven't installed the correct driver even in Windows. I would first confirm that by downloading and installing the recommended Dell driver (for Windows). Then reboot and test. Is it working now? If so, proceed to troubleshoot Linux.

---

### Post by Vladlenin5000 on 2015-03-31
In a closer look, unless you upgraded the original WiFi you **shouldn't **have 5GHz anyway...

[http://www.dell.com/us/dfh/p/inspiron-15-3520/pd](http://www.dell.com/us/dfh/p/inspiron-15-3520/pd) -> *Dell Wireless card 802.11 b/g/n (**2.4G**), BT4.0+HS*

---

### Post by jmelton on 2015-04-07
How would it have worked before if it wasn't supposed to be technically possible? The card is definitely supposed to get the 5 ghz band and did until my new drive was installed. 

I guess it's possible that the network card got damaged when the hard drive got trashed, as rigged 00 said above? Or the driver just happens to have something wrong with it in both Windows and Linux. 

I can't even use Windows very well right now because when I upgraded to 8.1 yet another problem developed--the windows are flashing on and off and I'm barely able to type anything. Not sure what's up with that, I guess maybe another driver issue.

---

### Post by Vladlenin5000 on 2015-04-07
I just told what I found. Have you read the product's page? There's no mention of other cards (many notebook models from all vendors, under the same model reference, usually have optional components such as a discreet graphics, different panels and different WiFi cards but not yours, according to Dell).
so... -Again-, *unless you upgraded the original WiFi you **shouldn't **have 5GHz anyway... *But there's no point in speculating.Please check which one you have simply by ```
sudo lshw -C network
``` and post the results.
Or, even better, follow the instructions to download and run the wireless script and post the results[I].
[/I]

---

### Post by jmelton on 2015-04-07
Clearly I'm not speculating if I've had 5GHz before. What you googled was just a brief snippet about the card, not a full list of specs. I forget where, but I did actually find a fuller specification sheet that listed 5ghz capabilities. I also found a way to show the supported channels by running a command I found at [http://unix.stackexchange.com/questions/137894/how-do-i-find-out-if-my-wireless-card-supports-5ghz:](http://unix.stackexchange.com/questions/137894/how-do-i-find-out-if-my-wireless-card-supports-5ghz:)

iwlist wlan0 freq

Output was:

wlan0     26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.442 GHz (Channel 7)

So, my wireless card should pick up whichever 5ghz frequency my router is sending out, which it did before and which my Mac still does. But for some reason it isn't showing up.


> **Vladlenin5000 said:**
> I just told what I found. Have you read the product's page? There's no mention of other cards (many notebook models from all vendors, under the same model reference, usually have optional components such as a discreet graphics, different panels and different WiFi cards but not yours, according to Dell).
so... -Again-, *unless you upgraded the original WiFi you **shouldn't **have 5GHz anyway... *But there's no point in speculating.Please check which one you have simply by ```
sudo lshw -C network
``` and post the results.
Or, even better, follow the instructions to download and run the wireless script and post the results[I].
[/I]

---

### Post by Vladlenin5000 on 2015-04-07
Nice, but where are the results of ```
sudo lshw -C network
```???


(EDIT)

Oops... Deja vu -> [http://ubuntuforums.org/showthread.php?t=2027925](http://ubuntuforums.org/showthread.php?t=2027925)
I hope you honor us with your reply this time around.

---

### Post by jmelton on 2015-04-18
jeff@jeff-PC:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: c0:18:85:c6:c3:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:f7c00000-f7c07fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: e0:db:55:84:33:9b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


> **Vladlenin5000 said:**
> Nice, but where are the results of ```
sudo lshw -C network
```???


(EDIT)

Oops... Deja vu -> [http://ubuntuforums.org/showthread.php?t=2027925](http://ubuntuforums.org/showthread.php?t=2027925)
I hope you honor us with your reply this time around.

---

### Post by Vladlenin5000 on 2015-04-18
```
product: BCM43142 802.11b/g/n
```

2.4GHz only, as expected.

---

### Post by jmelton on 2015-04-27
n is capable of either 2.4 or 5. If my card weren't capable of 5ghz, I wouldn't have ever seen 5ghz channels or been able to connect to them. I've told you already that I had previously been able to.

> **Vladlenin5000 said:**
> ```
product: BCM43142 802.11b/g/n
```

2.4GHz only, as expected.

---

### Post by Vladlenin5000 on 2015-04-27
802.11n specification does indeed include 5GHz but such implementation isn't mandatory. As a matter of fact, the majority of the chips designated by "b/g/n" still support 2.4GHz only. Generally speaking, the only ones supporting dual band are those of the "**a**/b/g/n" or the newer "**a**/g/n/**ac**" classes.

Broadcom's BCM43142 is 2.4GHz, _according to the manufacturer_. Here you can see a list of Broadcom's WiFi chips and I hope you notice that _all dual band are explicitly mentioned as such_.
Also, FYI, here's the same chip, the same "issue" and, not surprisingly, the [EXACT same answer]("https://social.technet.microsoft.com/Forums/windows/en-US/8779c9e2-8708-4bdf-8a58-b8c504183bb6/unable-to-detect-5ghz-band-in-my-windows-81-pc?forum=w8itpronetworking") but this time from a Microsoft TechNet moderator.[URL="https://social.technet.microsoft.com/Forums/windows/en-US/8779c9e2-8708-4bdf-8a58-b8c504183bb6/unable-to-detect-5ghz-band-in-my-windows-81-pc?forum=w8itpronetworking"]


[/URL]

---

### Post by Vladlenin5000 on 2015-04-27
[http://www.eightforums.com/network-sharing/53113-unable-detect-5ghz-band-my-sony-vaio-pc.html](http://www.eightforums.com/network-sharing/53113-unable-detect-5ghz-band-my-sony-vaio-pc.html)
Also from another manufacturer - HP - [http://h30434.www3.hp.com/t5/Wireless-Internet-Home-Networking/How-to-Find-if-the-notebook-has-a-Singleband-or-Dual-band/td-p/860601](http://h30434.www3.hp.com/t5/Wireless-Internet-Home-Networking/How-to-Find-if-the-notebook-has-a-Singleband-or-Dual-band/td-p/860601) (posts #6 and #7)


So...
What is more likely? Are we all wrong - me, the TechNet Mod, the HP Expert, ... - or are you mistaken?
Couldn't it be that you had another (dual band) WiFi device connected and the 5G network were "seen" by this one? Or a different internal card altogether? You tell us...

---

