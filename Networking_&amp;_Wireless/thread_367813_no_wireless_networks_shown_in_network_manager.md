---
title: "no wireless networks shown in network manager"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by adamstorm on 2007-02-22
I am using ubuntu 6.10 with a belkin (atheros) wireless pci card installed. Using the System->Administration->Networking dialog, I was able to successfully connect to a WEP encrypted network, so I know my card is recognized and working. I installed network manager and I am still able to connect to the wireless network, but no wireless networks show up in the network manager. In fact, network manager doesn't seem to even know that the wireless card is installed. the only thing I get when I click on the network manager is a greyed out button to connect to my wired network (which is unplugged). How can I get this working?

Thanks!

---

### Post by Reknall on 2007-02-22
I've run into the same problem with my Intel Pro/wireless 2915ABG card.  Using Edgy as well, only difference is my router is using WPA-PSK.

Anyone know what the deal is, or have suggestions?

---

### Post by ldbooth on 2007-02-22
My network manager did that for a while too, especially when I come out of standby. 

open up the terminal and  go to this folder:
/etc/network

use your favorite editor (mine is gedit):
sudo gedit interfaces &

What I did is comment out everything except eth0 and eth1 and network manager started working.

Here is mine. Of course this is only a partial fix.
```

#auto lo
#iface lo inet loopback

#iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto eth1

auto eth0
iface eth0 inet dhcp


```

---

### Post by adamstorm on 2007-02-22
I tried to do this and it seemed to not do anything except keep me from getting online at all, even after I changed it back! grrr!

Edit:  I went into the networking dialog and deselected the connection, then clicked configure and disabled the connection, restarted, then network manager magically works! YAY!

Thanks!

---

