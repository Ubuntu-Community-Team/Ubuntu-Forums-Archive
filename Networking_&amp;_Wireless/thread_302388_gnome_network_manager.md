---
title: "gnome network manager"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by obavjestenja on 2006-11-18
Hi,
I will try to explane my "problem" :( 
im beginer with ubuntu and i cannot make gnome network manager to work
with my wireless home network.
I have cable internet true DHCP.
I want to see this:

[[IMG]http://img62.imageshack.us/img62/8779/screenshotev3.png[/IMG]](http://imageshack.us)

---

### Post by janbockaert on 2006-11-18
does this link help?

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Any already configured devices that you want to be available in Network Manager will need to de-configured, as otherwise they will be ignored.

The easiest way to do this is by going to System -> Administration -> Networking and then going to "Properties" of each connection. In Properties, just untick the "Enable this connection" checkbox. Logout then log back in again. These connections should now be available in Network Manager.

OR, the harder way, is to backup and then edit the /etc/network/interfaces file to remove the configuration of these devices (except for lo which is needed for the loopback interface). You will have to save the file and reboot for the changes to take effect (or don't reboot and run /etc/init.d/networking restart instead). For example, if you wanted Network Manager to be able to control all of your devices, your /etc/network/interfaces file would look somewhat like the following:

auto lo
iface lo inet loopback

---

### Post by obavjestenja on 2006-11-18
i allready try the first option  but:
gnome networ manager see the wirless network,low signal,  but cannot login into wireless network.

---

