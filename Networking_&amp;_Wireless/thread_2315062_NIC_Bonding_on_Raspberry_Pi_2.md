---
title: "NIC Bonding on Raspberry Pi 2"
date: 2016-02-25
forum: Networking &amp; Wireless
---

### Post by macpoetter on 2016-02-25
Hi, 


I am trying to make NIC bonding work on my Raspberry Pi 2. It works like a charm with my Apple USB to Ethernet Adapter and the WiFi Dongle from  Detroit DIY Electronics, but not with the internal eth0. Regardless if I want to combine eth0 + eth1, or eth0 + wlan0. eth1 + wlan0 works always.


Following the working /etc/network/interfaces file:


```

auto bond0
iface bond0 inet dhcp
  bond-slaves eth1 wlan0
  bond-mode active-backup
  bond-primary eth1
  bond-miimon 100


allow-hotplug wlan0
iface wlan1 inet manual
  wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```


```
cat /proc/net/bonding/bond0
``` 
The above command, however, shows that the connection/disconnection was successfully detected if using eth0 instead of eth1 + wlan0.


The problem seems to be that eth0 always wants to have its own IP address and isn't forwarding it to its master bond0. I can see that by observing ifconfig while unplugging and reconnecting the ethernet cable. After reboot and after plugging the cable in again the IP of bond0 moves to eth0 and the internet connection is gone. Removing the cable results in the fact that bond0 gets its old IP back.


When I run 


```
sudo ip addr flush dev eth0
```


every time eth0 gets an IP then it also works. Adding 

```
up /sbin/ip addr flush dev eth0
```


under the definition for eth0 in the interface file didn't help unfortunately. 


Does someone has an explanation for this strange behavior? I am debugging for 2 days now already and can't find the reason nor a work around.


Thanks a lot for your help.


Best.

---

### Post by him610 on 2016-02-26
NIC Bonding -  a new term for me. I had to look it up to see what it meant. I only know a little about a few things - definitely not a moderator or a guru. Most of the issues one finds in this Forum are more ordinary. Pointing you to a link that references UbuntuBonding, is about as much advice that I can give.
[HTML]https://help.ubuntu.com/community/UbuntuBonding[/HTML]

I was unaware the Rpi2B had two network interfaces. I have an orginal RpiB that only has one network interface.

As a suggestion, you might want to post your system specifications - both hardware and software. You may well be the resident Forum expert on Bonding. In that case, "Physician, heal thyself." Good luck.

---

### Post by macpoetter on 2016-02-26
[COLOR=#000000]Hi [/COLOR][COLOR=#000000]hgh9mrp!

Thanks a lot for your interest in my problem. You could also call the topic: **Combining eth0 + wlan0 fails in RP2** ;)

The link you posted was the one that brought me to this topic in the first place. I'm not sure if thats then the right word for it, but *unfortunately* I know that link already.

The RP 2 doesn't have 2 NICs, just one ethernet, like the original one. As I was writing in the thread description already, I have additionally an* Apple USB to Ethernet Adapter*, whereby the USB part is plugged in into the Pi itself, and the ethernet into my router. The Wireless adapter is a *Ralink Technology, Corp. RT5370 Wireless Adapter.* But I think the problem is more about the internal ethernet. lsusb says me this one is called: *Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter*.

It seems like running the following commands after rebooting helps:

```
sudo ip link set eth0 down
sudo ifenslave bond0 eth0
sudo ip link set bond0 up
sudo dhcpcd bond0

```

So my guess is, that some process maybe ifups the eth0 already before the /etc/network/interface file tries to ifenslave it?! Don't know if that makes sense. Adding these commands without the sudo and /sbins/ instead to /etc/rc.local still doesn't seem to work (reliable). I will try further in this direction.

My hardware contains additionally a second wifi dongle, same chip, which I removed for testing, as well as every other entries in the interface file as well as hostapd and the isc-dhcp-server. 

Best, [/COLOR]

---

### Post by him610 on 2016-02-26
Hello macpoetter,

Well, here is another link for you; it has some more current information. It was referenced in the original one that I posted.

[https://www.kernel.org/doc/Documentation/networking/bonding.txt]("https://www.kernel.org/doc/Documentation/networking/bonding.txt")

I would think that using a wireless adapter brings its own set of problems. Did you consider using a USB Ethernet adapter? They used to be fairly common. I have one, but I have not used it in years.

---

### Post by macpoetter on 2016-02-28
Hi hgh9mrp,

I knew that txt file already. It's not that I can't make it to work, I made it work between the Apple USB to Ethernet Adapter (eth1) and the WiFi Dongle (wlan0). But every combination with the internal one (eth0), also eth0 + eth1, doesn't work...

---

