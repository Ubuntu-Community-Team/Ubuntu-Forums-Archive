---
title: "IBM R61e - only problems - bluetooth and wireless don't work!!!!!"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by grybi on 2008-04-28
I have just installed Ubuntu 8.04 and I am completly disappointed.....

Bluetooth don't work.....wifi don't work......


Intel Corporation PRO/Wireless 3945ABG Network Connection.
Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express.

Any suggestion?:(

---

### Post by superprash2003 on 2008-04-28
have you tried enabling restricted drivers(if shown) in system->administration

---

### Post by adjua on 2008-04-28
Same with me in a IBM r60e.
Have tried 
- to completely uninstall bluetooth und reinstall
- hcitool scan --> no such device
- lsusb, lspci - nothing looks like bluetooth any more
- no restricted drivers any more (Gutsy: wireless driver)
- wireless no longer present in network mananger

All worked nicely in Gutsy

tnx fort all hints, can I report bug anywhere?



> **grybi said:**
> I have just installed Ubuntu 8.04 and I am completly disappointed.....

Bluetooth don't work.....wifi don't work......


Intel Corporation PRO/Wireless 3945ABG Network Connection.
Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express.

Any suggestion?:(

---

### Post by grybi on 2008-04-28
I have tried enabling restricted drivers but in system->administration 
I don't have any driver.........

iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

:(

Any suggestion?

---

### Post by grybi on 2008-05-02
I solved problem with driver to Intel Wireless 3945ABG

----------------------------------------------
Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.

   1.Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2.Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).
   3.Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).
   4.Select Install new driver.
   5.Choose the location of your Windows .inf file and click Install.
   6.Click OK.

But I have got another problem driver work fine but I cant connect to network


dmesg | grep wlan0
[ 24.002678] wlan0: ethernet device 00:1c:bf:6e:94:23 using NDIS driver: netw4x32, version: 0x1000f, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 3945ABG Driver', 8086:4227.5.conf
[ 24.002764] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 31.050021] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1111.833749] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1349.160229] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1423.068884] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1470.876515] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by adjua on 2008-05-04
> **superprash2003 said:**
> have you tried enabling restricted drivers(if shown) in system->administration

There are no drivers shown - in gutsy there were ....

Edit: There Should not be any more anyway ...

Hardy obvisously ships a new wireless driver for Wireless 3945ABG --> module ipw3945 must be blacklisted, 

Thinkwiki is useful as always: 

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61)  and 

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T60)

On the driver issue there is a Documentation:

[https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy)

I did all of these, with no resuolt, until I realized, that my wireless was simply switched off by hardware switch.

BUT: I seem never to have enable this switch, maybe gutsy ignored it ??

---

### Post by grybi on 2008-05-04
In Gutsy there were but not working  Hardy Heron use i iwl3945 but still don't working


PCI: Setting latency timer of device 0000:03:00.0 to 64
129.814554] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c4]
iwl3945: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.
iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

---

