---
title: "Netgear WG111USv2 - ndiswrapper required?"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by sgentry6 on 2007-03-05
[Netgear WG111US Wifi Doc Page]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111")

[B]I realize that there is a lot of information below.  Here is the quick summary:

iwconfig recognizes my card.  dmesg recognizes the card, including removing / replacing card.  dhclient doesn't give me an ip address.  ndiswrapper is not installed.  lshw -C network shows no driver for the wireless device.[/B]


I am ignoring non-relevant output (i.e. the on-board ethernet card).

lshw -C network (NOTE: NO DRIVER IS SHOWN)

*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: MAC address
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=802.11b/b

lsmod | grep rtl
ieee8021_rtl  85640 2 r8187

lsmod | grep 8187
r8187            46596   0
ieee8021_rtl  85640    2  r8187
usbcore         134912  5  r8187,usbhid,ohci_hcd,ehci_hcd

dmesg | grep -C7 8187
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
ACPI: PCI Interupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 201
rtl_ieee80211_crypt: registered algorithm 'NULL'
rtl_ieee80211_crypt: registered algorithm 'TKIP'
rtl_ieee80211_crypt: registered algorithm 'WEP'
rtl_ieee80211_crypt: registered algorithm 'CCMP'

Linux kernel driver for RTL8187 based WLAN cards
Copyright(c) 2004-2005, Andrea Merello
rt8187: Initializing module
rt8187: Wireless extensions version 20
rt8187: Initializing proc filesstem
rt8187: Reported EEPROM chip is a 93c46 (1Kbit)
ts: Compaq touchscreen protocol output
rt8187: Card MAC address is XX:XX:XX:XX:XX:XX
NET: Registered protocol family 17
rt8187: Card reports RF frontend Realtek 8225
rt8187: WW:This driver has EXPERIMENTAL support for this chipset.
rt8187: WW:use it with care and at your own risk and
rt8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO XXXXX
rt8187: This seems a legacy 1st version radio
rt8187: PAPE from CONFIG2: 0
rt8187: Driver probe completed

usbcore: registered new driver rt8187
rt8187: Setting SW wep key
rt8187: Card Successfully reset



iwconfig wlan0
802.11b/g ESSID:"MY SSID"
Mode:Managed Channel=Wrong Chanel Access Point: Not-Associated
Bit Rate=11 Mb/s  Sensitivity=4/6
Retry:on Fragment thr:off
Encryption key:"MY WEP key" Security mode:open
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0  Missed beacon:0

ifconfig wlan0
Link encap:Ethernet HWaddr XX:XX:XX:XX:XX:XX
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
TXbytes:0 (0.0 b) TX bytes:0 (0.0 b)


ndiswrapper is not installed -- The refrenced document above makes it unclear (to me at least) whether or not I need to use ndiswrapper.  The driver is inserted into the kernel.  Plug and play works (ie, I see in dmesg if I unplug and plug the dongle back in).  I can set my ap with iwconfig, but I still can't pull an ip from the router.  DHCP hits the wrong server as well:

i.e.

dhclient wlan0
For some reason all of the DHCPDISCOVER goes to 255.255.255.255 even though I have set my netmask to 255.255.255.0.

It seems that I am forced to use ndiswrapper, which I really don't want to believe.  I was hoping that I could completely avoid this step, as I don't want a windows driver on this box...  I even went so far as to download the driver and such from the realtek site and attempt to build and insert it, but that worked to no avail as well.

Is there hope for the Feisty Fawn?  I'm obviously not going to wait that long for the thing to work, what about a new kernel?  Would updating to 2.6.20 be useful?  I don't care to compile one, just don't want to "waste" the time to compile and then have it not work.

Thanks all.

---

### Post by RomeReactor on 2007-03-05
Hi. from the output of iwconfig that you posted:

> Mode:Managed **Channel=Wrong Chanel** Access Point: Not-Associated

seems like the channel is incorrect. Try

```
iwlist wlan0 scanning
```

to see the actual channel you must use; then assign it with iwconfig

```
sudo iwconfig wlan0 channel YOUR_CHANNEL
```

or manually editing your interfaces file

```
gksudo gedit /etc/network/interfaces
```

scroll down to wlan0, and add **wireless-channel YOUR_CHANNEL**.

Also:

> rt8187: WW:This driver has **EXPERIMENTAL** support for this chipset.

suggests you may be better off trying the NdisWrapper solution.

---

### Post by sgentry6 on 2007-03-05
Even when properly set in /etc/network/interfaces it doesn't connect properly (although my dmesg is flooded with "Linking to "MYSSID""

iwlist wlan0 scanning returns no results.  Thanks for reminding me about that, as I forgot to put that in the original post.

I understand that the driver is experimental, but I am really hoping to get around ndiswrapper.


Thanks for the post though.  I am going to keep trying.

---

### Post by sgentry6 on 2007-03-08
Attempted ndiswrapper on that install, it didn't like it one bit.  I am going to try this again on a fresh install.  

After modprobing ndiswrapper iwconfig did not show a wireless device.  (Yes I tried the win98/Me driver).

---

