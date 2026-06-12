---
title: "Edimax 7318UG wireless problem"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by geezerone on 2008-08-24
Having used the above RT73 based device for many months the computer had problems booting and after fsck fixed the issues after a few hours I lose the wireless connection. If I reboot it is fine. I get the dredded SIOCFFLAGGS error message.

I added the network monitor applet to  a panel and when trying to 'configure' the wlan0 connection the window appears saying the interface doesn't exist. I have removed and reinstalled network manager and nm gnome with Synaptic but no joy. 

I have had to manually configure the interface file and insert a networking restart command in the /etc/rc.local boot script to get the wireless to automatically connect.

Below is the output from my lsmod working in the past and not working properly now::

Before :

```
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
cfg80211               15112  1 mac80211
```After 

```
rt73usb                27776  0 
crc_itu_t               3072  1 rt73usb
rt2x00usb              14080  1 rt73usb
rt2x00lib              26752  2 rt73usb,rt2x00usb
snd_ac97_codec        101028  1 snd_via82xx
joydev                 13120  0 
rfkill                  8592  1 rt2x00lib
ac97_bus                3072  1 snd_ac97_codec
rt2x_mac80211         177944  2 rt2x00usb,rt2x00lib
snd_mpu401_uart         9728  1 snd_via82xx
input_polldev           5896  1 rt2x00lib
rt2x_cfg80211          29704  2 rt2x00lib,rt2x_mac80211

```

Thanks in advance.

---

### Post by geezerone on 2008-08-24
System was up for well over 7 hrs and then added the network monitor applet and a little over an hour the wlan0 I/F isn't shown anymore in iwconfig or if config???

*lsmod* output after failure which occurs approx. 1hr after adding network monitor applet to panel:

```
[   52.665446] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.792832] padlock: VIA PadLock not detected.
[   63.002097] wlan0: no IPv6 routers present
[23427.968610] wlan0: CTS protection enabled (BSSID=00:14:4f:33:53:52)
[23442.287710] wlan0: CTS protection disabled (BSSID=00:14:4f:33:53:52)
[33924.001653] usb 5-7: USB disconnect, address 3
[33924.012410] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[33924.012419] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[33924.012424] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[33924.012428] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[33924.012432] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[33924.379341] usb 5-7: new high speed USB device using ehci_hcd and address 4
[33939.700209] usb 5-7: new high speed USB device using ehci_hcd and address 5
[34447.094559] eth0: link down
[34447.094695] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

