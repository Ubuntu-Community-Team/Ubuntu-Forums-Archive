---
title: "Question about wireless drivers"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by geezerone on 2008-08-26
Hi

I had a working Edimax 7318UG (RT73 based chipset) but after a boot problem requiring fsck I am getting a failed network connection after about an hour if using network manager or the nm 2.12.1 applet added to the panel. If I try and configure the wlan0 interface from the nm applet the message:

```
The interface does not exist.

Check that it is correctly typed and that it is correctly supported by your system.
```I then get the message after about an hour:

```
SIOCGIFFLAGS error: No such device 
```I have manually configured the /etc/network/interfaces config to get a wireless connection but cannot use network manager which was working fine before.

Sometimes X restarts with a message saying reconfiguring networking before x restarts if that is any help? Also getting very slow speeds on high speed connection when performing broadband speed tests.

BTW, I haven't had much in the way of updates since the crash = have there been any today or yesterday?

Here is my lsmod output when working ok and when not working with net manager:

Before:

```
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
cfg80211               15112  1 mac80211
```After (current): 

```
rt73usb                27776  0 
crc_itu_t               3072  1 rt73usb
rt2x00usb              14080  1 rt73usb
rt2x00lib              26752  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
rt2x_mac80211         177944  2 rt2x00usb,rt2x00lib
input_polldev           5896  1 rt2x00lib
rt2x_cfg80211          29704  2 rt2x00lib,rt2x_mac80211

```

---

