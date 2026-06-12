---
title: "USB recommendations"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-11-24
Well, after not having any luck with Xubuntu 6.06 recognizing a Linksys WMP54g V4 PCI card, or a Netgear WG311NA (V3?) as hardware in the device manager, I'm left to the possibility of running a USB adapter instead (which I'd prefer not to do, but...).

After searching the Wiki, it looks like the...

Linksys WUSB54G V4
DLink DWL G122 Ver. B1 
Airlink AWLL3026 

...all look like they work out-of-the box with Xubuntu 6.06.
The wireless network includes "g" with WPA PSK.

Any suggestion for a solid pick of the three, or another?

Thanks, new to Linux.

---

### Post by FrodoB on 2006-11-24
Well I would be cautious about the  Airlink AWLL3026 working out of the box. There is an older version that uses the ZyDas zd1211 and the newer version uses the ZyDas zd1211b. The newer zd1211b will not work out of the box.

Here are instructions for getting the zd1211b version working correctly:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

The Zonet ZEW2500P is working out of the box on Edgy for me, but it does take about 15 seconds for the device to initialize and be ready for use after system startup, It uses a Ralink rt2500 2570 chipset. I personally prefer the two Belkin F5D7050 versions below.

The F5D7050 ver 3000 and ver 4000 work after you build drivers for them:

Ver 4000:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Ver 3000:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

I should also add that I have no idea if WPA PSK works on any of these.

---

### Post by DapperMe17 on 2006-11-24
Thanks for your reply.

I would prefer something that works as simply as possible, or out-of-the-box within range.

---

