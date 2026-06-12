---
title: "wlan0 becomes eth1 after suspend/hibernate"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by rumo_orbis on 2007-05-20
I have successfully installed Xubuntu 7,04 on my system. I have a problem with my wireless connection after suspend/hibernate. I noticed that Wicd doesn't find any aps after suspend/hibernate. 
I now just had the idea it might work if i change wlan0 to eth1 in wicd's preferences as my wireless card had this name before when i had ubuntu. and weirdly... it works.
so now the question is... how can i make xubuntu remember that the wireless card is wlan0 after suspend/hibernate or alternatively how can i have my wireless card have the name eth1 all the time. i don't care about the naming... but some consistency would be nice.

thanks for help
rumo

btw. i'm on (x)ubuntu now for one/two months and almost only had good experiences... wireless with wpa works, wireless network printer works, samba works, exaile rocks etc. im really happy to have switched :)

---

### Post by rumo_orbis on 2007-05-20
just a quick add... my wireless card runs with the ndiswrapper drivers, if that's of any relevance

---

### Post by rumo_orbis on 2007-05-21
i solved it... changed /etc/iftab so that my wireless card is wlan0 now. i still don't understand why it was wlan0 when i did a normal boot/restart but eth1 with resume from hibernation/suspension though....

---

### Post by bicchi on 2007-07-20
I have the same problem and this is the output of dmesg that might explain what is happening:
Jul 20 18:31:30 localhost kernel: [   26.616000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'

This is what I noticed in my case: 
If I boot running on battery (no AC power) I get: eth1
If I boot using AC power I get: wlan0

Modifying /etc/iftab worked for me. I just made my mac address for the wireless point to wlan0. Now I get the same interface every time regardless.

Makes me think if this is related to acpi?

---

### Post by stocks29 on 2007-07-24
I have the same problem with my desktop, except it isn't wireless. It is wired. I only have one interface -- one physical NIC that is on the motherboard. Before suspending the machine, it is called eth0 and the MAC address is correct. After suspending the machine. It is eth1 and the MAC address is incorrect, although I have no connection problems. The only problem is that my is configured to give the machine a certain IP address based on its MAC address, which now cannot be done properly after suspend. Anyone have any ideas?

---

### Post by rogun on 2007-07-28
I, too, am having this problem with a desktop, but mine's a little different, because I do have connection problems after resuming. If I suspend and resume again, then it changes back to eth0 and I'm connected again.

Also, when eth1 is "connected", clicking "Connection Information" in the NetworkManager Applet shows a MAC address that's identical to eth0, except that it's reversed! My motherboard does have two NICs, but I'm only using one of them and the other is disabled in the BIOS, fwiw. The NetworkManager Applet doesn't give an IP address for eth1 either, but it will eventually say that it's connected.

I should also mention that I use a static address, rather then DHCP for eth0 and can't connect using DHCP.

---

### Post by ssam on 2008-03-02
any updates on this?

I am seeing it on a acer aspire 7520. after suspending and resuming the mac address has changed for the build in ethernet. this is a problem because it needs to connect to a network that filters by mac address.

is there a good way to manually fix the address that does not interfere with network manager?

---

