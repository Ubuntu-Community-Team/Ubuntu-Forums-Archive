---
title: "MSI GT72S 6QE - WiFi adapter"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by fabbari on 2015-11-19
This is the first of a set of posts about having a working Ubuntu on a MSI GT72S 6QE laptop. All of the devices are currently working, with the occasional issues with daisy chained monitors using the integrated Display Port. I hope this posts will help others. The first recommendation is to use at least Ubuntu 15.10 for this laptop and - sadly - you will have to use the Server Edition and then install the desktop if you want to take advantage of the Software RAID devices -- the two SSD drives this laptop has. But that's another story.

Before following this instructions, make sure you have the correct WiFi adapter. ```
lspci
``` should show a device like this one:

```

Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

```

  This adapter is supported by the ath10k module, but the board file that's distributed with it will not work. The interface won't come up and the system will have an odd behavior: it will freeze up occasionally, take a long time to execute command and launch applications and other such things. In the logs you will see something that looks like this:

```

[ 1156.471033] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[ 1156.707471] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[ 1156.707491] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-pci-168c:003e:1a56:1535.bin failed with error -2
[ 1156.707495] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[ 1156.707827] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[ 1156.707835] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[ 1158.827488] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff, 168c:003e:1a56:1535 fallback) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 1158.827491] ath10k_pci 0000:03:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 1161.827721] ath10k_pci 0000:03:00.0: could not suspend target (-11)
[ 1161.894663] ath: EEPROM regdomain: 0x6c
[ 1161.894665] ath: EEPROM indicates we should expect a direct regpair map
[ 1161.894666] ath: Country alpha2 being used: 00
[ 1161.894667] ath: Regpair used: 0x6c
[ 1161.896307] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[ 1167.169732] ath10k_pci 0000:03:00.0: failed to set arp ac override parameter: -11
[ 1173.176440] ath10k_pci 0000:03:00.0: could not suspend target (-11)
[ 1173.254330] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 1178.498340] ath10k_pci 0000:03:00.0: failed to enable dynamic BW: -11
[ 1184.505015] ath10k_pci 0000:03:00.0: could not suspend target (-11)
[ 1184.582776] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

```


Removing the module:

```
sudo rmmod ath10k_pci
```

 will make the system work again, but you get no WiFi.

  The solution to this issue - and to get the WiFi on this laptop working - is currently a pull request on the kvalo ath development branch: [https://github.com/kvalo/ath10k-firmware/pull/3/files](https://github.com/kvalo/ath10k-firmware/pull/3/files)

  If you download the file, save it in ```
/lib/firmware/ath10k/QCA6174/hw3.0/board.bin
``` and reboot your WiFi will be working happily ever after. This may be impairing your ability to use another ath10k based adapter -- you never know - so you can also be very specific and place the file where the driver expects it to be for this specific card. If you look at the output of the logs you can see that the driver is searching for a specific board firmware file: 

```

[ 1156.707491] ath10k_pci 0000:03:00.0: Direct firmware load for **ath10k/QCA6174/hw3.0/board-pci-168c:003e:1a56:1535.bin** failed with error -2

```

You can copy the board file you downloaded from the commit to /lib/firmware/**ath10k/QCA6174/hw3.0/board-pci-168c:003e:1a56:1535.bin **and be sure that only your internal card will read it and use it.


  Fabio

---

### Post by simone22 on 2015-11-26
I tried your guide on my new laptop acer aspire v15 black edition, I tried to boot the live (before reading your guide the sistem used to freeze without apparently any reason: the mouse cursor stops and is impossible to use the keyboard, the only thing to do is to power off the system) after reading your guide immediately after booting the live I unloaded the modules of the wireless card (obviously the same of your laptop: qca6174) what happened after that is that I could use the live system for more or less 15 minutes before experiencing the same problem.. Freezing whitout particular reason.
Is it something else that I could try? I tested the system with the live before because if it doesn't work properly in this conditions I could even install because one time the system freezes while I was installing it.

---

### Post by fabbari on 2015-11-30
Hi Simone,

  it could be that the modules are being probed again after a while - did you try to add the modules to the blacklist? This way you would be sure that the modules will never be loaded again.

  Did you try to start the live with 'acpi=off' as a boot parameter?

  Fabio

---

### Post by Bucky Ball on 2015-12-03
*Thread moved to **Networking & Wireless**.*

Ok. You have not mentioned the wireless card you are using. Be aware that the same model of laptop in another country or later (or earlier) in the run may use a different wireless card. Consequently, if someone with a different wireless card follows your instructions and they have a different card they are likely to fall in a (deep) hole. Users are following your instructions on this thread without even knowing whether they have the same card. :|

Your fix is not necessarily 'generic', so please state clearly, in full, at the top of your post, the details of your wireless card, please. Adding it to the title would be good, too. Thanks.

```
sudo lshw -C network
```

... will do it. Thanks.

@simone22: Please post a new thread regarding your issues. You are not using the same laptop as the original poster and we have no idea which wireless card you're using. These instructions could put you in a worse place than you started (which looks to be the case). Good luck.

---

### Post by simone22 on 2015-12-04
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless**.*

Ok. You have not mentioned the wireless card you are using. Be aware that the same model of laptop in another country or later (or earlier) in the run may use a different wireless card. Consequently, if someone with a different wireless card follows your instructions and they have a different card they are likely to fall in a (deep) hole. Users are following your instructions on this thread without even knowing whether they have the same card. :|

Your fix is not necessarily 'generic', so please state clearly, in full, at the top of your post, the details of your wireless card, please. Adding it to the title would be good, too. Thanks.

```
sudo lshw -C network
```

... will do it. Thanks.

@simone22: Please post a new thread regarding your issues. You are not using the same laptop as the original poster and we have no idea which wireless card you're using. These instructions could put you in a worse place than you started (which looks to be the case). Good luck.

Thank you both of you for your reply,
finally I solved the problem, the wireless card is identical as the one inside the MSI laptop : 
```

07:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

```

The problem related to the random system crash were the neuveau video drivers, so after I changed the drivers from the open source to the Nvidia proprietary the system stopped to crash, then I applied exatly the procedure described by fabbari and the wireless of my laptop started working. :)
So my computer is an Acer Aspire V15 Nitro Black edition: vn7-592g.

---

