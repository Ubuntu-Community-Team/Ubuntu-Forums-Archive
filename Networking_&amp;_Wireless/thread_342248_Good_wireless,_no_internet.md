---
title: "Good wireless, no internet"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by mgaskell on 2007-01-19
My Intel wireless adapter was working fine until yesterday. I don't know what I could have done.

I have an Intel internal wireless adapter that I understand should work "out of the box" with Edgy. Signal strength is strong and apparently the card is communicating with my network. It is DHCP. It works booting into the Windows partition. I just cannot get a wireless internet connection booting to Ubuntu. I must plug into my router to get on line.

Here are some printouts that may help:

mike@mike-laptop:~$ sudo ifconfig ath0
ath0: error fetching interface information: Device not found

mike@mike-laptop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSID:"LinksysDownStairs"
Mode:Managed Frequency:2.437 GHz Access Point: 00:13:100:5C6
Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thrff Fragment thrff
Encryption keyff
Power Managementff
Link Quality=97/100 Signal level=-28 dBm Noise level=-89 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

Let me know if there are any other commands I can execute to better explain the problem.

Thanks,
Mike

---

### Post by funkadelic on 2007-01-19
In Edgy, I had to actually type in the name of my wireless network, even though my router is set to broadcast it. Try that, perhaps?

---

### Post by mgaskell on 2007-01-19
Thanks,

I'll give that a try. Where do I enter that information?

BTW, this may be problematic because I'm using a laptop that I take on the road and will be unable to know the name of the network in range sometimes.

I'm wondering if my installation and subsequent complete removal of the app "KWiFiManager" could have gotten rid of something that I needed.

---

### Post by teaker1s on 2007-01-19
try installing
[COLOR="Red"]network-manager-gnome[/COLOR]

---

### Post by mgaskell on 2007-01-19
Thanks. I just installed it and rebooted but it doesn't show up under Applications. How do I use it?

---

### Post by mgaskell on 2007-01-19
Hunted around - found out how to use it - Network Manager was the answer. Don't know how or why but I'm not complaining. Everything works great now!

Thanks for all the great help.

---

### Post by teaker1s on 2007-01-20
I expect a config file was altered, glad your fixed :guitar:

---

