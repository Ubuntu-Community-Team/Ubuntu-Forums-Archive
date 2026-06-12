---
title: "Inconsistent wifi"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by HJQG3wT on 2013-12-11
--- 192.168.1.1 ping statistics ---20 packets transmitted, 12 received, 40% packet loss, time 19073ms
rtt min/avg/max/mdev = 318.882/806.300/1320.009/313.207 ms, pipe 2

I have a very inconsistent wifi. My most recent ping is above. This is a desktop with Ubuntu 13.10. I was having wifi problems with a card, so I switched it out for another one. It worked fine for a while, but now I'm having these problems again. 

[This]("http://www.amazon.com/dp/B008L2PREI/ref=pe_385040_30332190_pe_175190_21431760_M3T1_ST1_dp_1") is my wireless card.

Any help would be great!

---

### Post by chili555 on 2013-12-11
Please confirm the exact details of your card:```
lspci -nn | grep 0280
```And is the driver I suspect loaded now?```
lsmod | grep rt2
```If so, are there any interesting clues here?```
dmesg | grep rt2
```

---

### Post by HJQG3wT on 2013-12-12
Here goes: 
> [FONT=courier new]lspci -nn | grep 0280[/FONT]
[FONT=courier new]04:00.0 Network controller [0280]: Ralink corp. Device [1814:5392]

[/FONT][FONT=courier new]$ lsmod | grep rt2[/FONT]
[FONT=courier new]rt2800pci              18690  0 [/FONT]
[FONT=courier new]rt2800lib              79963  1 rt2800pci[/FONT]
[FONT=courier new]rt2x00pci              13287  1 rt2800pci[/FONT]
[FONT=courier new]rt2x00mmio             13603  1 rt2800pci[/FONT]
[FONT=courier new]rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio[/FONT]
[FONT=courier new]mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib[/FONT]
[FONT=courier new]cfg80211              479757  2 mac80211,rt2x00lib[/FONT]
[FONT=courier new]eeprom_93cx6           13344  1 rt2800pci[/FONT]
[FONT=courier new]crc_ccitt              12707  1 rt2800lib[/FONT]
[FONT=courier new]

[/FONT][FONT=courier new]dmesg | grep rt2[/FONT]
[FONT=courier new][   10.683159] rt2800pci 0000:04:00.0: enabling device (0000 -> 0002)[/FONT]
[FONT=courier new][   10.683672] rt2800pci 0000:04:00.0: irq 60 for MSI/MSI-X[/FONT]
[FONT=courier new][   10.683718] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected[/FONT]
[FONT=courier new][   10.687392] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5392 detected[/FONT]
[FONT=courier new][   11.199701] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'[/FONT]
[FONT=courier new][   11.200034] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34[/FONT]
[FONT=courier new]
[/FONT]


[FONT=courier new]
[/FONT]



---

### Post by HJQG3wT on 2013-12-12
Here's the output from the wifi script varun suggested for me. [http://paste.ubuntu.com/6559829/](http://paste.ubuntu.com/6559829/)

---

### Post by varunendra on 2013-12-12
I would wait for Dr. chili's advice, but I think in the meanwhile you may try disabling N-channel in the router (it will reduce the connection speed to 54 Mbps, but may help stability). It is easy to revert back if didn't help.

If the router's settings provide the option to set the band, try setting it to **g-only** or **b/g only** mode. It currently seems to be in **b/g/[COLOR="#FF0000"]n[/COLOR]** mode. Save the settings and reboot both the router and your computer to make sure the change properly takes effect.

Oh, and before trying above, even easier to try is the "nohwcrypt" parameter. In a terminal, please do -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot or after an unload --> reload of the driver without the parameter. You may try this before or after (with or without) the change suggested about the router.

---

### Post by chili555 on 2013-12-12
Awesome suggestions, Varun! Pretty much exactly what I'd suggest. I did notice this:> # PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.6/0000:06:00.0/0000:07:00.0 ([COLOR="#FF0000"]ath9k[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"Did you remove and replace an internal Atheros wireless device? Is ath9k loading?```
lsmod | grep ath
```Are there any interesting clues here?```
cat /var/log/syslog | grep -i dns | tail -n10
```

---

### Post by HJQG3wT on 2013-12-12
[This]("http://www.amazon.com/dp/B0034CL2ZI/ref=pe_385040_30332190_pe_175190_21431760_M3T1_ST1_dp_1") is the card I had in before. You guys helped me and it worked for a while, but then it broke enough times that I got fed up, so I replaced it.

No results from 
> [COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep ath
[/FONT][/COLOR]

Then I tried
> 
$ cat /var/log/syslog | grep -i dns | tail -n10
Dec 12 15:15:24 fornax avahi-daemon[626]: Joining mDNS multicast group on interface wlan1.IPv6 with address fd09:a47d:7a29:0:1919:fc90:27a4:27f0.
Dec 12 15:15:25 fornax avahi-daemon[626]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.122.
Dec 12 15:15:25 fornax avahi-daemon[626]: New relevant interface wlan1.IPv4 for mDNS.
Dec 12 15:15:25 fornax NetworkManager[890]: <info> Policy set 'kahnboche 1' (wlan1) as default for IPv4 routing and DNS.
Dec 12 15:15:25 fornax NetworkManager[890]: <info> Writing DNS information to /sbin/resolvconf
Dec 12 15:15:25 fornax dnsmasq[2762]: setting upstream servers from DBus
Dec 12 15:15:25 fornax dnsmasq[2762]: using nameserver 192.168.1.1#53
Dec 12 15:15:25 fornax dnsmasq[2762]: using nameserver 209.18.47.62#53
Dec 12 15:15:25 fornax dnsmasq[2762]: using nameserver 209.18.47.61#53
Dec 12 15:15:26 fornax NetworkManager[890]: <info> Policy set 'kahnboche 1' (wlan1) as default for IPv6 routing and DNS.



Part of the difficulty with this problem is that the connection isn't usually broken -- it's just inconsistent (breaks maybe 4-5 times per day). So it's not immediately obvious if I've fixed something. 

One aspect is: when it breaks, if I just click reconnect to the network (in the wifi-indicator dropdown menu), it works again. 

I'll try varun's suggestion and see what happens:
> [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rv rt2800pci[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v rt2800pci nohwcrypt=Y[/FONT][/COLOR]

If I "Suspend" the computer, will I revert the settings?

---

### Post by chili555 on 2013-12-12
> **HJQG3wT said:**
> If I "Suspend" the computer, will I revert the settings?No, but if you reboot it will. If it helps, we can write a file to make it persistent.

Your syslog looks fine; no clues there.

---

### Post by HJQG3wT on 2013-12-16
I ran varun's modprobes. What exactly do they do?

I also changed my wifi to 802.11G. 

The connection is still inconsistent. What's next?

---

### Post by slooksterpsv on 2013-12-17
Try this: 
```

sudo iw dev wlan0 get power_save

```

If it says on run:

```

sudo iw dev wlan0 set power_save off

```

---

### Post by varunendra on 2013-12-17
> **HJQG3wT said:**
> I ran varun's modprobes. What exactly do they do?
The first one unloads the driver rt2800pci. The second one reloads it with a parameter "nohwcrypt=Y", which shifts the workload of encrypting packets from the card's hardware to the software (driver and/or the OS). It helps when the card's internal hardware based encryption can't keep up with the speed due to high data rate or inefficient encryption protocol.

> I also changed my wifi to 802.11G. 

The connection is still inconsistent. What's next?

What slooksterpsv suggested was to turn the **power management** off on your card. Your previously uploaded wireless_script report shows it already off, so that shouldn't be needed (unless it has been turned on in the meanwhile).

My experience tells me that Dr. chili555's next suggestion may be compiling the latest backported driver which you can download from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

Another tested solution (although with a slightly different card) is here : [http://ubuntuforums.org/showthread.php?p=12790346](http://ubuntuforums.org/showthread.php?p=12790346)

I would suggest to wait to see which one he approves, or maybe suggests an entirely different solution. :)

---

### Post by chili555 on 2013-12-17
> My experience tells me that Dr. chili555's next suggestion may be compiling the latest backported driverCorrect! That Varun is good, isn't he?

Please get a temporary wired ethernet connection and open a terminal:```
sudo apt-get install build-essential linux-headers-generic
```Download this file to your desktop:  [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2)  Right-click it and select 'Extract Here.' Now back to the teminal:```
cd ~/Desktop/backports-3.12-1
make defconfig-wifi
make
```Make takes a while depending on memory, CPU cores, et al. I generally refresh my beverage and check emails.```
sudo make install
```Detach the ethernet, reboot and let us hear your success!

---

### Post by HJQG3wT on 2013-12-24
Here's the output from my "sudo make install". To my untrained eye, it looks like something went wrong -- no? Either way, I've done what you suggested, and I'll post again soon with an update on the connection.

> adam@fornax:~/backports-3.12.2-1$ sudo make install[sudo] password for adam: 
  Building modules, stage 2.
  MODPOST 104 modules
  INSTALL /home/adam/backports-3.12.2-1/compat/compat.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/compat/cordic.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/compat/crc8.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/bcma/bcma.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/usb/cdc_ncm.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/usb/rndis_host.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/usb/usbnet.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/adm8211.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/at76c50x-usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ar5523/ar5523.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath5k/ath5k.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath9k/ath9k.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath9k/ath9k_common.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/carl9170/carl9170.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ath/wil6210/wil6210.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/b43/b43.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/b43legacy/b43legacy.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/cw1200/cw1200_core.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/cw1200/cw1200_wlan_sdio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/cw1200/cw1200_wlan_spi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ipw2x00/ipw2100.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ipw2x00/ipw2200.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ipw2x00/libipw.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/iwlegacy/iwl3945.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/iwlegacy/iwl4965.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/iwlegacy/iwlegacy.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/iwlwifi/iwlwifi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas/libertas.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas/libertas_cs.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas/libertas_sdio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas/libertas_spi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas/usb8xxx.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas_tf/libertas_tf.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/mac80211_hwsim.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/mwifiex/mwifiex.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/mwifiex/mwifiex_pcie.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/mwifiex/mwifiex_sdio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/mwifiex/mwifiex_usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/mwl8k.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco_cs.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco_nortel.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco_pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco_plx.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco_tmd.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/orinoco_usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/orinoco/spectrum_cs.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/p54/p54common.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/p54/p54pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/p54/p54spi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/p54/p54usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rndis_wlan.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2400pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2500pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2500usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2800lib.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2800pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2800usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2x00lib.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2x00mmio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2x00pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt2x00usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt61pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rt2x00/rt73usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl_pci.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtl_usb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wl1251/wl1251.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wl1251/wl1251_sdio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wl1251/wl1251_spi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wl12xx/wl12xx.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wl18xx/wl18xx.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wlcore/wlcore.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wlcore/wlcore_sdio.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/ti/wlcore/wlcore_spi.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/net/wireless/zd1211rw/zd1211rw.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/drivers/ssb/ssb.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/net/wireless/cfg80211.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/net/wireless/lib80211.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/net/wireless/lib80211_crypt_ccmp.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/net/wireless/lib80211_crypt_tkip.ko
Can't read private key
  INSTALL /home/adam/backports-3.12.2-1/net/wireless/lib80211_crypt_wep.ko
Can't read private key
  DEPMOD  3.11.0-14-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.


Your backported driver modules should be installed now.
Reboot.




---

### Post by chili555 on 2013-12-24
> **HJQG3wT said:**
> Here's the output from my "sudo make install". To my untrained eye, it looks like something went wrong -- no? Either way, I've done what you suggested, and I'll post again soon with an update on the connection.No. You got a harmless warning that you may safely ignore, followed by:> Your backported driver modules should be installed now.
Reboot.
So, did you reboot? Any improvement?

---

### Post by HJQG3wT on 2013-12-26
--- 192.168.1.1 ping statistics ---
43 packets transmitted, 40 received, 6% packet loss, time 42071ms
rtt min/avg/max/mdev = 1.742/6.348/150.684/23.199 ms

Substantially better than before! So far, it's been working very consistently. 

What did those changes do?

Thanks for all your help!

---

### Post by HJQG3wT on 2014-01-10
It actually is a lot better than before, but it still breaks every day or two. I just reconnect to the network and it works again. Are there any next steps?

---

### Post by chili555 on 2014-01-11
> **HJQG3wT said:**
> It actually is a lot better than before, but it still breaks every day or two. I just reconnect to the network and it works again. Are there any next steps?Aside from Varun's suggestion in post #3  or a different card, I have no further suggestions.

---

### Post by HJQG3wT on 2014-01-11
Alright, I'll keep messing around. Thanks for the tips!

---

### Post by Ro0oTs on 2014-06-30
Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
make[1]: *** [modules] Error 1
make: *** [default] Error 2



this msg was come .. what i can do?

---

### Post by varunendra on 2014-06-30
Welcome to the forums Ro0oTs!

You should have started a new thread, providing some background information and details of the problem (OS version, type of machine fresh install or upgraded etc.).

We can request the mods to move your post (and replies to it) to its own thread, but please provide the above details so it can be moved with a suitable title. Your current description tells me almost nothing.

---

