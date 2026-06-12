---
title: "Network Manager Does not List My Nic"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by matt11601 on 2007-02-24
Hey everyone. I'm another Ubuntu 6.10 (linux noob) convert trying to get my NIC card to work.

Device Manager accurately lists my 3Com Etherlink XL NIC. Specifally, Device Manager lists it as "3c905C-TX/TX-M"

But when I go to Network Settings, my NIC Card is not listed. The only thing there is "Modem Connection." So basically I can't get on the internet.

If I type "ifconfig eth0" in the terminal, I get this:

----------------------------------------------------------------------
eth0: error fetching interface information: Device not found
----------------------------------------------------------------------

And here's the contents of my /etc/network/interfaces file:

---------------------------------------------------------------------
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
----------------------------------------------------------------------------------

I provided you with that information because other people seem to ask that when troubleshooting networking problems. But I really have no idea what it means.

Hopefully someone can help me out. Thank.

-Matt

---

### Post by TwistofLemon on 2007-02-24
I have the same problem. I have an improcomm 2220 it is listed in the device manager but not in the network manager. Ndiswrapper says the device is present but as long as it is not recognized by linux as a wlan device I'm stuck.

I have no clue how to solve this. The funny thing is that somehow suddenly when I was running edgy but not .17 but .18 core is suddenly worked. The nic was detected as wlan and ndiswrapper worked like a charm. I am now testing feisty and have no such luck :S

I keep on wondering if there was something I had installed but I just dont know.
frustrating as hell :S

update:
sudo modprobe ndiswrapper was the key for me. It keeps on crashing but I'll sort that out.

---

### Post by matt11601 on 2007-02-25
I've been doing a lot of searching for this problem. Specifically, I've looked at posts regarding my 3C905C-TX card. But all the posts I've found do not relate to my problem because in those posts Ubuntu already recognizes the NIC card. 

My problem, as of now, is getting Ubuntu to recognize my NIC card in the first place.

So now I'm stuck.

---

