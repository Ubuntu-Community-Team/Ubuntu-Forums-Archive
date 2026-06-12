---
title: "Aircrack-ng Killing me!!!!!"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by ni_ko on 2009-12-09
Hi im new to linux, and im trying to get aircrack-ng up and running on my netbook. Im using a Asus eeepc 10005hab, and im pretty sure my wirless chipset is atheros. Iv downloaded the mad wifi drivers and did the make and make install command, but i dont know what to do after that! i dont even know if they installed correctly...im totally lost. Any help would be appreciated!

---

### Post by ukripper on 2009-12-09
try this if you are running ubuntu 9.10:

Administration --> Software Sources --> Updates and check/enable “Unsupported Updates (karmic-backports)”.

Then then in terminal type this:


```
sudo apt-get update && sudo apt-get install linux-backports-modules-karmic
```

this will install required modules for you.

Just reboot and it should be working.

---

### Post by Sylslay on 2009-12-09
try : those commmad:

airmon-ng start wlan0
airmon-ng stop wlan0

iwconfig wlan0 up 
iwconfig wlan0 channel 11 /switch to channel11
run airodump-ng channel 11 -i wlan0 -w wpa.cap //
aireplay-ng -2 30 -a <target> -h <mymac> wlan0
aireplay-ng -1 30 -e linksys -a <target> -h <mymac> wlan0
aireplay-ng -0 5 -a <ap mac> -c <klientmac> wlan 0 / deauth atack 

wesside-ng -i wlan0

tested some time ago, it works with ra2500 chip.

pattern was:

ifconfig wlan0 up
iwlist wlan0 scanning >network.txt
iwconfig wlan0 channel 11
airodump-ng channel 11 -i wlan0 -w wpa.cap
wesside-ng k 2 -i wlan0 -v <target>

---

### Post by ni_ko on 2009-12-09
> **ukripper said:**
> try this if you are running ubuntu 9.10:

Administration --> Software Sources --> Updates and check/enable “Unsupported Updates (karmic-backports)”.

Then then in terminal type this:


```
sudo apt-get update && sudo apt-get install linux-backports-modules-karmic
```this will install required modules for you.

Just reboot and it should be working.

I followed your steps and installed thos modules, but whenever i run "sudo airmon-ng stop ath0" i get this:

Interface    Chipset        Driver

wlan0        Atheros     ath9k - [phy0]

and im pretty sure i need to see this:

Interface       Chipset         Driver
 
 wifi0           Atheros         madwifi-ng
 ath0            Atheros         madwifi-ng VAP (parent: wifi0) (VAP destroyed)

---

### Post by ni_ko on 2009-12-09
also to get the madwifi drivers working do i have to remove the driver ubuntu netbook remix came with?

---

### Post by KIAaze on 2009-12-09
I have an atheros based card too.
While wireless always worked without any problems, I always have to figure out how to get aircrack-ng to work everytime I want to try it again (with changes depending on the kernel version... :/ ).

But generally, you find most, if not all, of the info you need on [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

If I remember correctly (and after rereading the wiki), here's a summary:
Supported drivers: Madwifi, ath5k or ath9k
Two possible stacks: mac80211 or ieee80211

I think what I had to do was patch a driver (either madwifi or ath*k) somehow and blacklist the other drivers.

Some important remarks from the wiki:
> Mac80211 is the new wireless stack of the Linux kernel. It is included in the kernel since 2.6.22, but drivers are only included since 2.6.24. 
> Although it is not very &#8220;scientific&#8221;, sometimes simply unloading then reloading the driver will get it working. This is done with the rmmod and modprobe commands. 

> A common problem on newer kernels is that the new mac80211 version of the driver gets loaded instead of the older legacy driver, or vice versa. If that is the case, then you need to blacklist the wrong modules by editing /etc/modprobe.d/blacklist. First, determine the broken module names and add them to the blacklist file as &#8220;blacklist <module name>&#8221;.

Specifically for madwifi-ng, do a locate or find for ath5k.ko. If ath5k.ko exists then add &#8220;blacklist ath5k&#8221; to /etc/modprobe.d/blacklist and reboot. Same for the other way around: if you want to load ath5k, but madwifi-ng gets loaded instead, add &#8220;blacklist ath_pci&#8221; to /etc/modprobe.d/blacklist.


I hope this helps even if it isn't a complete solution. :oops:
I could try getting aircrack to work again with my atheros card and post the results here, but I'm giving no guarantee.

> also to get the madwifi drivers working do i have to remove the driver ubuntu netbook remix came with?
You should definitely do that or at least blacklist them!

---

### Post by ni_ko on 2009-12-09
> **KIAaze said:**
> I have an atheros based card too.
While wireless always worked without any problems, I always have to figure out how to get aircrack-ng to work everytime I want to try it again (with changes depending on the kernel version... :/ ).

But generally, you find most, if not all, of the info you need on [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

If I remember correctly (and after rereading the wiki), here's a summary:
Supported drivers: Madwifi, ath5k or ath9k
Two possible stacks: mac80211 or ieee80211

I think what I had to do was patch a driver (either madwifi or ath*k) somehow and blacklist the other drivers.

Some important remarks from the wiki:





I hope this helps even if it isn't a complete solution. :oops:
I could try getting aircrack to work again with my atheros card and post the results here, but I'm giving no guarantee.


You should definitely do that or at least blacklist them!
 
ok so i dont undertand most of what you said because im totally new...but i DID blacklist my ath9k and rebooted but the madwifi driver i installed (not sure if it was corectly installed because it never said so) did not kick in...i had to un blacklist the ath9k and the reboot to get my wofo working again.

---

### Post by KIAaze on 2009-12-09
Did you install madwifi from source?
(if it goes through "./configure && make && make install" successfully, it is probably correctly installed.)

Patching them is apparently only necessary for fragmentation attack support, but just in case and if you find anything mentioning a patch for your card:
[http://www.aircrack-ng.org/doku.php?id=patching](http://www.aircrack-ng.org/doku.php?id=patching)

Fragmentation attack patches:
[http://www.aircrack-ng.org/doku.php?id=mac80211#fragmentation_attack_support](http://www.aircrack-ng.org/doku.php?id=mac80211#fragmentation_attack_support)

---

### Post by ni_ko on 2009-12-09
ok so i didnt install it from scource but im getting the scource now....how do i delete the old madwifi drivers i have?

---

### Post by KIAaze on 2009-12-09
I think it will just overwrite the old ones, once you run make install.

Otherwise, just locate the corresponding .ko files and remove (or just move) them.
They should be somewhere in "/lib/modules/KERNEL_VERSION-generic/kernel/drivers/net/wireless/".

---

