---
title: "wireless card installed- not recognized by network manager"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by Stoph on 2006-10-05
I installed by Dell 1500 wireless card using ndiswrapper. It appears in the Network Connection dialog in the top right if I open that. It isn't recognized by Network Manager though. I only have one option when I click the applet in the top right: Wired Connection.

Here is my /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid welsh

```

I have heard about removing all the interfaces except lo, but that only seems to make my wlan0 device disappear completely!

Any help or further questions are appreciated.

---

### Post by wieman01 on 2006-10-05
Your "interfaces" file should indeed look like this if you use NetworkManager:
> auto lo
iface lo inet loopback
...assuming that you don't need wired (eth0) for the time being. Then restart the computer & see if this works.

---

### Post by Elaztic on 2006-10-06
actually your interfaces should look like that regardless if you are running wireless and/or wired network.

Please read: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Stoph on 2006-10-06
I finally figured out where the problem was: I had to add the line "**ndiswrapper**" to **/etc/modules**

Then I changed my **/etc/network/interfaces** to this:
```
auto lo
iface lo inet loopback
```

Network manager now picks up my connections, but whenever I try to connect to my wireless network, it fails. I am not using any form of WEP.

My workaround right now is to remove network-manager, restore my original /etc/network/interfaces file, and use wifi-radar to connect.

Can anyone help me make network manager work? It's so much easier than running wifi-radar

---

### Post by Stoph on 2006-10-06
Could these errors be related? This comes up when I try to disconnect from the wireless network in wifi-radar

```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device   ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device   ; No such device.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device   ; No such device.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device   ; No such device.
: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
: ERROR while getting interface flags: No such device

```

---

### Post by wieman01 on 2006-10-06
Question: Is the network you're trying to connect to a secured one? As fas as I know NetworkManager cannot handle unencrypted networks.

---

### Post by Stoph on 2006-10-06
yes, it's unencrypted

---

### Post by wieman01 on 2006-10-07
> **Stoph said:**
> yes, it's unencrypted
As said, I don't think NetworkManager can handle unencrypted networks at all. Have seen similar posts before.

---

### Post by tturrisi on 2006-10-07
The real question is why on earth are you using ndiswrapper with an atheros chipset card?

---

### Post by wieman01 on 2006-10-07
> **tturrisi said:**
> The real question is why on earth are you using ndiswrapper with an atheros chipset card?
That's a good question but won't resolve his problem. No matter it's ndiswrapper or the native Linux driver, it's all the same as far as his problem is concerned. But you have a point.

---

### Post by Stoph on 2006-10-08
i didn't think there were native linux drivers for my card

Dell 1500 draft-n compatible (something something blahblah)

---

### Post by wieman01 on 2006-10-08
If "ndiswrapper" works fine for you, I wouldn't bother. But up to you of course. Running "ndiswrapper" on one of my PCs and it works just fine.

---

### Post by Reb on 2006-10-09
I use NetworkManager to connect to unencrypted networks all the time, they're open but MAC authorized.

---

### Post by Reb on 2006-10-09
The fix is to add auto (name of interface) above the interface info:
**auto ath0**
iface ath0 inet dhcp
Then, kill NetworkManager and restart it (possibly also restarting nm-applet).  It should work now and in the future - did for me.

---

### Post by Reb on 2006-10-09
Here's a bug report I filed - nothing came up for a NetworkManager atheros search.  [https://launchpad.net/distros/ubuntu/+bug/64929](https://launchpad.net/distros/ubuntu/+bug/64929)

---

