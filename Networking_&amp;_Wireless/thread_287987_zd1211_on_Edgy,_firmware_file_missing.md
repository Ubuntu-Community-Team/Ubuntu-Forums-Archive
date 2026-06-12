---
title: "zd1211 on Edgy, firmware file missing"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by bed on 2006-10-29
Hi, I recently installed ubuntu 6.10, and I have trouble to detect my wireless card. On dapper I followed these steps: [https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211]("https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211")
Unfortunately, it doesnt work anymore. So, I decided to download from Synaptic the zd1211 source. I created the module package and installed it.

Here what: dmesg | grep zd1211
returns

[   32.213673] zd1211 - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - SVN_TRUNK
[   32.494565] zd1211:bulk out: wMaxPacketSize = 200
[   32.494567] zd1211:bulk in: wMaxPacketSize = 200
[   32.494569] zd1211:interrupt in: wMaxPacketSize = 40
[   32.494570] zd1211:interrupt in: int_interval = 1
[   32.494572] zd1211:interrupt out: wMaxPacketSize = 40
[   32.529043] Failed to load zd1211-WS11UPhR.fw firmware file!
[   32.529050] zd1211_Download_IncludeFile failed
[   32.529055] zd1211: probe of 2-5:1.0 failed with error -5
[   32.529063] usbcore: registered new driver zd1211

So not able to load the firmware file... indeed there is not such file in my disk.

If anyone could help, it will be appreciated.

Thank you

---

### Post by Bezmotivnik on 2006-10-29
> **bed said:**
> 
If anyone could help, it will be appreciated.

Can't help, but I can reassure you that this device won't work properly in v6.10.  You're not imagining this. ](*,) 

It works OK in v6.06, so I reinstalled that.  I haven't tried either with the 1211b-chip device, just the 1211.

Good luck!

---

### Post by todds on 2006-10-30
i can confirm that edgy does not work properly with the zd1211b versions of the zydas chipset,there is a post on this website giving some detail of various problems with the zd1211 modules... it is for pclinuxos at [http://www.theloveoflinux.com/](http://www.theloveoflinux.com/) i have got the zd1211b module running through ndiswrapper but had to blacklist the zd1211rw driver through modprobe.d/blacklist...

regards

todds

---

### Post by bed on 2006-10-31
Following this HOW-TO, I been able to make the wireless work. 

[http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy](http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy)

Thanks to the community!

---

### Post by Roland32 on 2006-12-09
I had the same problem (zd1211-WS11UPhR.fw firmware file missing), but I could find it in the directory /lib/firmware/2.6.15-25-k7 (I had this directory from the installation  on the 6.06 version). I just copied the file to the directory /lib/firmware/2.6.17-10-generic (my current version), and now it works! It may not be the most elegant way to solve the problem, but at least, it works.

Regards

---

### Post by FrodoB on 2006-12-09
Detailed instructions for installing both the zd1211 and zd1211b drivers  from ZyDas:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

---

