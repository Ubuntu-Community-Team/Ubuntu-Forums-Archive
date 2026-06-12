---
title: "Signal drop with AZIO AWU254"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by daz0001 on 2008-03-29
When I first boot up, eveything is connected:
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:<mynetworkname>
          Mode:Managed  Frequency:2.452 GHz  Access Point: <my AP>         
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Signal level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But after a while (couple of hours?) I can no longer connect, and I get a zero signal level. The only way I can recover is if I unplug/plug the USB adapter and reissue my iwconfig command. 

Here is my lsmod:
$ sudo lsmod  | grep rt
rt2500usb              22016  0
rt73usb                25344  0
rt2x00usb              12032  2 rt2500usb,rt73usb
rt2x00lib              19584  3 rt2500usb,rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
usbcore               138632  6 rt2500usb,rt73usb,rt2x00usb,ehci_hcd,ohci_hcd

Any ideas on what to check?

---

