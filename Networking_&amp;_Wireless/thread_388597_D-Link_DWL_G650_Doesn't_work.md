---
title: "D-Link DWL G650 Doesn't work"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by Tex-Twil on 2007-03-19
Hello,
I just installed K Ubuntu and I can't get my G650 (Rev. C) work on my laptop (VAIO FE 31Z). This card has an Atheros Chipset. One of the 2 lights of the card is blinking every 4 seconds but I can"t find ant wifi interface.Here is what I've done:

> 
root@laptop-jan:~# iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.


> 
root@laptop-jan:~# uname -r
2.6.17-11-generic

I have restricted packages installed for this kernel: linux-restricted-modules-2.6.17-11-generic. Synaptic also installed the same for X86_64 as a dependency.

> 
root@laptop-jan:~# dmesg | grep ath
[17179592.020000] ath_hal: module license 'Proprietary' taints kernel.
[17179592.020000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179592.056000] ath_rate_sample: 1.2 (0.9.2.1)
[17179592.064000] ath_pci: 0.9.4.5 (0.9.2.1)


> 
root@laptop-jan:~# lspci | grep Network
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)

This is my integrated wifi card.

The pcmcia card works fine on my old laptop.

Thank you for your help.

---

### Post by Tex-Twil on 2007-03-20
Hello,
I'm desperate.
I tried a manual compilation of madwifi drivers as explained on 
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
and 
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
But it doesn"t work. I just can't see ath wifi interface.

---

### Post by Tex-Twil on 2007-03-20
Halleluja !

I disabled the madwifi module from restricted modules to load as explained here:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

+ manual install of madwifi drivers and it workds now !

---

