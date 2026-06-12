---
title: "Wifi networking not working after 14.04 update"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by brendacsnv on 2014-04-21
Hello,

I upgraded from Kubuntu 13.10 to 14.04 and I cannot connect to my wireless network.  It seems that some packages were not upgraded or installed correctly because the update manager has notified me that there are still quite a few updates needed even after the restart.  The network manager app does not show any wireless networks even though networking is enabled.  I even tried a wired connection but that also did not work.

*nmcli nm status* shows that my laptop is disconnected but that wifi-hardware, wifi, wwan-hardware and wwan are all enabled.

*nmcli -p dev wifi list* does not show any wireless APs that it should have scanned.

I am using another computer to write this, since I cannot connect to the Internet from my recently upgraded laptop.

---

### Post by praseodym on 2014-04-21
Please show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by SeijiSensei on 2014-04-21
The fact that the wired connection did not work is more troubling to me than the wifi issue.

If you know the IP address of the router, say 192.168.1.1, try connecting the computer with the Ethernet cable again and enter this into a terminal:
```
ifconfig eth0
```
Do you see an address assigned to the Ethernet adapter?  If not, then run
```
sudo ifconfig eth0 192.168.1.133 netmask 255.255.255.0 broadcast 192.168.1.255
```
In either case now use
```
ping 192.168.1.1
```
Can you ping the router?  I chose a random address in 192.168.1.2-254. It's remotely possible that you already have a machine with .133; if so choose a different number.  And if your network uses a different IP subnet instead of 192.168.1.0/24, use that instead.

If you can ping the router, see if you can ping Google's DNS server at 8.8.8.8?  Does that work?

---

