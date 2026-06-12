---
title: "Madwifi compiling"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by keith2045 on 2007-04-29
I just got a proxim silver 8471-wd wireless card, i'm using it on a laptop with Ubuntu 7.04. It works fine out of the box (well it did). I need to use the madwifi drivers for it, but i need to patch them, that's why i cant use it right out of the box. So i followed the instructions at

[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)
```
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```
They also say "The same gcc version that was used to compile your kernel. At least make sure that the first two version numbers or the compiler are thesame (e.g. it’s OK to use gcc 3.4.6 to compile the driver if the kernel was compiled by gcc 3.4.2). Ignoring this rule will cause Invalid module format errors during module load." How do i figure out what version of gcc that was used? I installed ubuntu from the cd

So when i do modprobe ath_pci i get this error
```
FATAL: Error inserting ath_pci (/lib/modules/2.6.20-15-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
This is dmesg
```
[13798.532000] ath_pci: Unknown symbol ieee80211_vap_detach
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_announce
[13798.532000] ath_pci: Unknown symbol ieee80211_announce
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_mark_dfs
[13798.532000] ath_pci: Unknown symbol ieee80211_mark_dfs
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[13798.532000] ath_pci: Unknown symbol ieee80211_chan2ieee
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch
[13798.532000] ath_pci: Unknown symbol ieee80211_dturbo_switch
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[13798.532000] ath_pci: Unknown symbol ieee80211_crypto_encap
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_getrssi
[13798.532000] ath_pci: Unknown symbol ieee80211_getrssi
[13798.532000] ath_pci: disagrees about version of symbol ieee80211_find_txnode
[13798.532000] ath_pci: Unknown symbol ieee80211_find_txnode

```
There is more of similar messages, just didnt include them. So i did some research and found some links but nothing helped. 

One said to remove ath_hal and wlan, then to modprobe ath_pci when i do that it says they are in use, so i cant remove them. 

Another suggstion was to "remove the original modules from Edgy manually, or recompile Edgy kernel with in-kernel madwifi turned off" I know i dont have edgy, but it's built into feisty also. I dont want to recompile my kernel, and dont know how to remove the original modules, i dont think that would work anyway because when compiling it, it asks if i want to remove previous versions. But if i wanted to do that, how would i?

Another site said "Your ieee80211 modules are not the correct version. You'll have to check madwifi's site to find out which version you should be using." which makes sense, but i cant find anything on the madwifi's site  requiring ieee80211. How do i figure out what version i have? 

I found some things on this forum, but they didnt work, and i dont have the links to them. 

Any suggestions?

---

### Post by keith2045 on 2007-04-29
I rebooted my machine and was able to remove ath_hal and wlan, then did modprobe ath_pci and it worked. Question, how do i know if i am using my patched driver instead of the built in one?

---

### Post by GuruX on 2007-04-30
I don't think you need to remove the files after reboot. Do everything except modprobe. Restart computer, and then modprobe.
To see if you are using the patched drivers. Run sudo airmon-ng to stop ath0, then start wifi0. Now run sudo airodump-ng ath0 (or perhaps ath1, thats what I run). Voila! If you discover networks, you have the patched driver.

---

### Post by tturrisi on 2007-04-30
If you use the instructions for patching at aircrack-ng site it will prompt to rem the existing modules during the install of the new patched ones.

---

### Post by ireblue on 2007-05-30
I've gotten the same error message after running modprobe ath_pci. I'm using a D-LINK DWL-G650 card, and upon reboot the system freezes up on startup once the card is inserted with a kernel panic error. It will start normally if i remove the card but upon reinsertion the system completely freezes-up. To get my card working again I have had to reinstall the restricted modules from the repos.

I'm using a Dell Inspiron 9300 w/ built in ipw2200 card which doesnt support injection, hence the reson for the D-Link card. Ive run the injection test "aireplay-ng -9 ath0" and it claims injection is working but Ive only once gotten any arp replies from the countless times Ive tried aireplay-ng, which led me to believe I needed to patch the drivers but of course that didnt work.

Any ideas would be helpful.

---

### Post by tturrisi on 2007-05-30
If you use Ubuntu and try to patch the madwifi drivers per the aircrack-ng site, you will get compilation errors.  This is because the Ubuntu linux-restricted-modules are still installed.  Use Synaptic to remove the restricted-modules madwifi PRIOR to using the aircrack-ng patch building.

FYI, you will know if the driver got patched & is working when you run airplay.  The patch is for enabling injection, that's all the patch does.  It may take up to several minutes for injection to begin, you'll see the "data" field suddenly start climbing expoentially.

---

### Post by tturrisi on 2007-05-30
Note the filed below in #data.  It took a little over a minute for injection to begin. Be patient!

---

### Post by tturrisi on 2007-05-30
Also, there's a bug in udev where if you use an atheros chipset.  The first atheros device will be named ath0.  When you run:
1. airmon-ng stop ath0 (destroys ath0)
2. airmon-ng start wifi0 (puts card in monitor mode, but udev bug names the active virtual adapter ath1 now, and the next time you do this it will be named ath2, and the next time it will be named ath3, and so on and so on until you have ath179!)

To correct this successive renaming of virtual adapters do this:
(backup files before editing!)

1. open /etc/udev/rules.d/z25_persistent-net.rules and remove the athX lines.
2. open /etc/udev/persistent-net-generator.rules and change this:

# ignore "secondary" raw interfaces of the madwifi driver
KERNEL=="ath*", ATTRS{type}=="802",	GOTO="persistent_net_generator_end"

to this:

# ignore "secondary" raw interfaces of the madwifi driver
KERNEL=="ath*", 	GOTO="persistent_net_generator_end"

AFAIK, this udev bug is not applicable to all kernels, thus if you don't get successive renaming of virtual ath devices then ignore this post.

---

### Post by spd106 on 2007-05-30
Have any of you tried the new PTW attack? Does it work well?

I hope to have a go when I can find some free time. 

Cheers

---

### Post by tturrisi on 2007-05-30
> **spd106 said:**
> Have any of you tried the new PTW attack? Does it work well?

I hope to have a go when I can find some free time. 

Cheers

I cracked my own AP in 90 seconds!

---

### Post by wieman01 on 2007-05-31
> **ireblue said:**
> I've gotten the same error message after running modprobe ath_pci. I'm using a D-LINK DWL-G650 card, and upon reboot the system freezes up on startup once the card is inserted with a kernel panic error. It will start normally if i remove the card but upon reinsertion the system completely freezes-up. To get my card working again I have had to reinstall the restricted modules from the repos.

I'm using a Dell Inspiron 9300 w/ built in ipw2200 card which doesnt support injection, hence the reson for the D-Link card. Ive run the injection test "aireplay-ng -9 ath0" and it claims injection is working but Ive only once gotten any arp replies from the countless times Ive tried aireplay-ng, which led me to believe I needed to patch the drivers but of course that didnt work.

Any ideas would be helpful.
First off, IPW2200 does support injection. See [this thread]("http://ubuntuforums.org/showthread.php?t=242556").

You need to run a deauthentication request first (ARP request) by using "aireplay -0 5" and thus deauthenticating one of the clients. Then you run "aireplay -3" and start collecting traffic/data using "airodump". I fell into the same trap before I reliazed that I had skipped this first crucial step.

---

### Post by lyd on 2007-06-07
> **tturrisi said:**
> Use Synaptic to remove the restricted-modules madwifi PRIOR to using the aircrack-ng patch building.

FWIW, I started to to do this, but was put off by the fact that Synaptic wanted to remove the kernel-generic package as well.  This is probably no big deal, but not knowing for sure I was nervous about going ahead.

I just added "ath_hal" to "DISABLED_MODULES" in /etc/default/linux-restricted-modules-common instead, and that worked fine.

lyd

---

