---
title: "BCM 4352 Works During Install, but Not After Install"
date: 2015-01-02
forum: Networking &amp; Wireless
---

### Post by johnathanamber on 2015-01-02
Hey everyone,

I've just installed 14.10 on my Dell Precision M6800 Mobile Workstation which has a Broadcom BCM 4352 Wifi card. When I first launched Ubuntu from my USB flash drive, I was able to enable the driver from Settings > Software & Updates > Additonal Drivers and then selecting the STA driver. However, after install, I can see this same drive, but each time I select it and apply, it doesn't activate the Wifi and continue to revert back to "Do not use the device". Why is that? If it worked during install, I would assume that it would work after install.

Thanks,
Johnathan

---

### Post by chili555 on 2015-01-02
May we see a few readings? From a terminal:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by johnathanamber on 2015-01-02
Well, this system doesn't have access to the 'net so I'll have to type it out... but here it is:

```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

```

Both the **dell-wifi: Wireless LAN** and **dell-bluetooth: Bluetooth** are showing "no" for Soft/Hard blocked.

---

### Post by chili555 on 2015-01-02
I believe you need to install bcmwl-kernel-source. Without internet access, you can install it like this: [http://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619](http://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619)

---

### Post by johnathanamber on 2015-01-02
@chili555,

While that resolved my problem, it still doesn't answer my original inquiry of why this works during installation, but not after being installed.

> 
Do you still have the install USB or DVD? Insert it and drill down to pool > restricted > b > bcmwl and drag bcmwl-kernel-source to your desktop. Do the same with pool > main > d >dkms and drag dkms to you desktop. Then install:

```

cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i bcmwl*.deb
```

Reboot and tell us if your wireless is working.


Thanks,
Johnathan

---

### Post by chili555 on 2015-01-02
If you were definitely connected to the internet during install and you definitely selected to install updates while installing, then I have no idea. I see this pretty regularly. Marking the thread Solved will help the searchers find the solution.

---

### Post by johnathanamber on 2015-01-03
@chili555,

Yes, I had connected to the Internet via my local Wifi. I did check both boxes to download updates and to get other packages.

The weird thing is that I can't connect to my home Wifi like I was during the install... but at least I see them now... I'll continue working on it.

Thanks for the help.,
Johnathan

---

### Post by johnathanamber on 2015-01-03
OK, Wifi is now working correctly. For some reason, and I remember doing this when I used Linux a few years ago, I had to restart my router in order for the Ubuntu installation to connect to it... even though it worked during installation. Thanks for the help chili555!

---

### Post by johnathanamber on 2015-01-05
Just an added note, for others with an M6800, or M4800, Dell Precision laptop, the following post has good information for additional drivers.

[http://askubuntu.com/questions/432933/linux-ubuntu-12-04-driver-for-broadcom-corp-bcm-4352-wireless-network-adapter/436959#436959](http://askubuntu.com/questions/432933/linux-ubuntu-12-04-driver-for-broadcom-corp-bcm-4352-wireless-network-adapter/436959#436959)

---

### Post by johnathanamber on 2015-01-07
Hey guys,

I've got one more issue. I keep having to reset my router in order to connect to the WiFi network. No issues on the same machine running Windows. Any thing you can think of that I can do to get this working without resetting my router each time?

---

### Post by johnathanamber on 2015-01-07
Well, I've found out via the /var/log/syslog that my wifi card isn't getting its DHCP address from my router:
```

Jan  6 23:33:47 name NetworkManager[928]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  6 23:33:47 name NetworkManager[928]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  6 23:33:47 name NetworkManager[928]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  6 23:33:47 name NetworkManager[928]: <info> dhclient started with pid 4391
Jan  6 23:33:47 name NetworkManager[928]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
...
Jan  6 23:34:11 name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x542a9db7)
Jan  6 23:34:24 name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x542a9db7)
Jan  6 23:34:33 name NetworkManager[928]: <warn> (wlan0): DHCPv4 request timed out.
Jan  6 23:34:33 name NetworkManager[928]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4391
Jan  6 23:34:33 name NetworkManager[928]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jan  6 23:34:33 name NetworkManager[928]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jan  6 23:34:33 name NetworkManager[928]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]

```

Knowing the local network, I set it up, I went ahead and assigned my own IP address along with the netmask, gateway, and DNS servers... VOILA!

So, now, the question is why would DHCP work before the installation, but not afterwards. Any ideas?

---

