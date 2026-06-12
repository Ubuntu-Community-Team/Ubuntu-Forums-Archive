---
title: "Athros AR5006X not working in Feisty Kubuntu"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by Tuxan1 on 2007-06-02
I have followed several posts describing the installation and configuring of the MadWifi modules. Here is the status of my project to date:

1. lsmod listing - 
ath_pci                97184  0
wlan                  204100  1 ath_pci
ath_hal               192592  1 ath_pci

2. lspci listing - 
 02:03.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)

3. ifconfig  ath, ath0 or waln up listing - (all return the same result)
ath: ERROR while getting interface flags: No such device

It seems like the interface should appear in the Network manager, but only the wired ethernet devices appear. 

I have seen that Feisty should recognize this card without issue, I installed the latest driver from the Madwifi site (madwifi-0.9.3.1.tar.gz), and I followed these instructions to install by ([http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)).

Any assistance would be deeply appreciated. 
TIA,
phil

---

### Post by Bouncelot on 2007-06-04
I am getting the same thing. What is odd is it worked for the install (I had to do a fresh install the upgrade crashed mid way) and continued to work until I shut it down for the first time (dual boot) when I booted it back up the ath0 was gone.

I noticed there is some error on boot-up I went through the logs (dmesg, kern, messages) and can't find the error.

---

### Post by blaamann on 2007-07-28
I got the same chip and also experience problems after the install. It is more unstable and hardly connects now. 

It worked great under Debian.

---

### Post by tyster on 2008-04-17
Would the type of CPU be an issue?  I have also spent quite some time trying to get the madwifi to work.  Same wireless network card, but I am using AMD 64 X2, which doesn't seem to like it at all.

---

### Post by moore.bryan on 2008-04-17
do all of you have linux-restricted-modules installed? madwifi is already in that package. if so, i've found simply using [wicd]("http://wicd.sourceforge.net/") instead of network-manager solved many of my problems.

---

