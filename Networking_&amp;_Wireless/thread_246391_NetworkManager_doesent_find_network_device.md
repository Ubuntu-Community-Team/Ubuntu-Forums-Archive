---
title: "NetworkManager doesent find network device"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by flugheim on 2006-08-29
Hi, i've problem with Network-manager, when i left-click it it says "No network devices have been found"
As far as i can see my card should be supported since their homepage says this: "Intel Pro Wireless 2200/2915"
Anyone who knows how i can get this application to work?

---

### Post by flugheim on 2006-08-30
Anyone?

---

### Post by NetworkGuy on 2006-08-30
Did you remark out all the interfaces listed in your /etc/network/interfaces files (except lo)?

---

### Post by flugheim on 2006-08-30
Nut sure exactly what you mean (my english suck :S ), but i can paste it here:
> 
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp
wireless-essid 3comsuger
wireless-key **removed**

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp







iface eth0 inet dhcp


---

### Post by tazzik on 2006-09-01
I also have the same problem but with a Netgear WG511T
Any ideas PLEASE?

---

### Post by Veridis on 2006-09-01
[FONT="Arial"]NetworkGuy meant that you put a # at the beginning of every line except the first two.

I tried this also (it was from the Network Manager website) but it didn't fix the problem for me.

Does Network Manager work with ndiswrapper, or only with drivers compiled in the kernel?
[/FONT]

---

### Post by flugheim on 2006-09-02
It didnt work for me either

---

### Post by flugheim on 2006-09-07
I've since the last post here, reinstalled Ubuntu, and now it seems to find one of the networkcards, but not the wireless one.. But it is there, because the built-in client and wlanmanager detects it(and let me use it :D) but i like network-manager better.. anyone that knows how to solve this?

---

