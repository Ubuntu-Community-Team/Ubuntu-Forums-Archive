---
title: "Wireless Driver for Thinkpad t40"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by mrbochin23 on 2007-04-14
Hi, I am new to Ubuntu, I honestly love it, I looking forward for the switch to Linux, my only issue so far is with my Thinkpad t40 2373 - 237375U with the wireless driver, it doesn't recognize my wireless, if some one could tell me where can I find a driver for it, or work a way around.

Thanks.

mrbochin

---

### Post by chili555 on 2007-04-14
The T40 came with three different wireless cards, each requiring different drivers. We need to know which you have. Please post the output of:```
sudo lshw -C network
```Omit the wired ethernet stuff. You might also install linux-restricted-modules through synaptic if it's not already there.

---

### Post by tico55 on 2007-10-31
Hello I am new to UBUNTU too I love it but I have a similar problem It did not pick up the wired network card can someone help?????

Tico

---

### Post by bliffle on 2007-11-12
Like the man says, pls post the output of:

```
sudo lshw -C network
```

I'm interested because I use this T40 regularly and it works well, but occasionally drops out, necessitating a 'restart'. 

I have the ipw2100.
```

john@JHT40UUU:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:12:34:b0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 mingnt=255 module=e1000 multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:77:af:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.3 latency=64 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
john@JHT40UUU:~$ 

```

---

### Post by jaq on 2008-02-18
I have the same problem with my thinkpad t40. Everything works except for wireless. I'm running 7.10 and would appreciate any pointers on a wireless driver for this model. Here's my output:

*****@*****-laptop:~$ sudo lshw -C network
[sudo] password for *****:
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:c9:cb:b6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
*****@*****-laptop:~$

---

### Post by vac72cov on 2008-02-19
i have a thinkpad t40 too, also my problem is with the wifi card but my one is the CISCO.

it can see wireless AP but can't authenticate to the wpa ones, asking for LEAP authentication instead of PSK.

it seems that linux kernels don't drive older cards then the intel 2200BG! 

i'm looking forward for the jump to linux but unless someone can fix this i have to stay with M$ :(

---

### Post by rach_lobster on 2008-04-03
I also have the Thinkpad T40 and PRO/Wireless Lan 2100 3B Mini PCI Adapter.  Installing Ubuntu 7.10 detected and installed driver, but connection drops randomly.  I dont have this problem with other wireless PC's in the house, only with this model wireless adapter.  Any help with getting this stable would be appreciated.

---

### Post by spawnywhippet on 2008-04-25
I have a T41 (2373-7FU) with Cisco Aironet 802.11b. I had Wireless seeing WEP networks in Ubuntu 7.10 but could not get WPA working, so today I clean-installed 8.04. I now cannot get the wireless to see any networks at all. Network Manager doesn't show a Wireless card at all, even though it appeared in 7.10.

  *-network:1
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list
       configuration: driver=airo latency=64 maxlatency=4 mingnt=4

---

### Post by yukonho on 2008-04-26
This is a reported bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398")

I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

---

### Post by chili555 on 2008-04-26
> Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aesMy Aironet works perfectly under Hardy with this change. Try it, Aironet users!

---

### Post by +Synyster on 2008-04-26
I've tried this method but it just crashes my computer

---

### Post by dan.seti on 2008-04-27
> Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes 

YES. this works for me as well.
Thank you

---

### Post by spawnywhippet on 2008-05-01
I just tried this on another newly installed Ubuntu 8.04 Thinkpad T41 with Cisco Aironet and when I try to connect to my WPA LAN, I am only offered LEAP as an encryption method, no WPA or WEP

---

### Post by jpiezo on 2008-05-01
Hey Folks,

I applied chili555's suggestion and it works like a charm. I have written directly via private messages thanking for the assistance. The blacklist suggestion definitely works.

The issue with wpa, I believe is a firmware issue with your card. I know that when I do a dmesg |grep -i airo there is a message in there that states WPA unsupported (only firmware versions 5.30.17 and greater support WPA. Detected 5.02.19)

I personally have not researched upgrading the firmware. These things usually are done with windows boot disks as the mfg's assume windows is the OS. Just like bios upgrades for mobos.

Jpiezo

---

### Post by spawnywhippet on 2008-05-01
It doesn't seem like a firmware issue:

andy@ubuntu-laptop:~$ dmesg |grep -i airo
[   20.600951] airo(): Probing for PCI adapters
[   21.100873] airo(): Found an MPI350 card
[   22.677780] airo(): WPA is supported.
[   22.679504] airo(eth0): MAC enabled 00:02:8a:5d:d3:a0
[   22.679532] airo(): Finished probing for PCI adapters

Any other suggestions gratefully received

---

### Post by chili555 on 2008-05-03
> **spawnywhippet said:**
> It doesn't seem like a firmware issue:

andy@ubuntu-laptop:~$ dmesg |grep -i airo
[   20.600951] airo(): Probing for PCI adapters
[   21.100873] airo(): Found an MPI350 card
[   22.677780] airo(): WPA is supported.
[   22.679504] airo(eth0): MAC enabled 00:02:8a:5d:d3:a0
[   22.679532] airo(): Finished probing for PCI adapters

Any other suggestions gratefully receivedHave you followed all the steps here?
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by taugust04 on 2008-05-08
> **yukonho said:**
> This is a reported bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398")

I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

This worked perfectly for me.  I have the exact same wireless card. Thank you for posting this information.

---

### Post by AlamedaDad on 2008-06-16
I have the Intel 2200BG card and I can't figure out how to turn on the card while running Ubuntu. Fn-F5 turns on the Bluetooth but not wifi. Initially wifi worked fine, but after a reboot, the radio is powered off and I can't get it back on.

Thanks...Michael

---

### Post by scoopyb on 2008-06-17
Hi,

I have a thinkpad t41 and I'd like to get my wireless working too. Problem is, since my laptop is bought used, I don't know what wireless card I have (I haven't installed windows at all, so that doesn't help either). I quess I have one since there's a MAC address for 802.11b in the bottom. 

I modified the blacklist-file but it didn't help and the "sudo lshw -C network" -command only lists my wired ethernet controller. I also tried "lspci" that I found from a guide, but it didn't find any wireless device either.

I found this list from the support pages, I suppose mine should be one of those.
# Intel 802.11b wireless LAN on selected models
# ThinkPad High Rate 802.11a/b/g Wireless on selected models
# Cisco Aironet Wireless 802.11b on selected models

Any ideas for this problem?

-scoopyb

---

### Post by spawnywhippet on 2008-06-17
If you can't figure it out in Linux, there are at least 2 more alternatives. 

The easiest way to figure it out may be to throw a copy of Windows on there and let it do the work. If no luck with native drivers, try installing each of those named drivers until one works.

The quicker method is to turn it upside down, undo about 8 small Phillips screws on the keyboard bezel and 4 holding the keyboard on, then read the label on the wifi card (located under the touchpad). Takes about 5 mins.

---

### Post by AlamedaDad on 2008-06-17
The easiest way I have found is using IBM's support web site. Just put in the exact model number and it will tell you the exact config as it left their factory. Of course the card could have been changed, but not likely.

---

