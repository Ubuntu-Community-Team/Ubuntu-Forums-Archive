---
title: "Server 20.10 - Network Applet Shows No Connection"
date: 2021-03-11
forum: Networking &amp; Wireless
---

### Post by No_Gate$ on 2021-03-11
Recently installed Server 20.10 as part of upgrade due to disk change for OS. Everything appeared to install correctly and existing disks were accessible. 
"No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.10
Release:        20.10
Codename:       groovy"


Installed KDE desktop as I already use this on other PC and again no errors on the installation. 
However, the Network applet in the system tray shows no connections and Discover cannot refresh cache as it says there is no internet connection.  This is not correct as I can ping google DNS on 8.8.8.8, Chrome works and can use apt on command line to get updates. 
I have tried creating connections via nmcli but they still don't show as connecting/connected on any gui.
Attached is output from ifconfig and yaml file.

Not sure that whether this is a network or desktop issue but any help appreciated

Thanks

Paul

---

### Post by TheFu on 2021-03-12
Typically, when you install the "Server" version of any Ubuntu, text files are used to setup and control the network connections.  This makes perfect sense because "Servers" don't have a GUI. Management of the core Server settings is via text files.  I happen to prefer that. Many people do not.

If you want a DE, then you probably want all the GUI integration that each DE works very hard to create. Best to get that by installing the GUI flavor of the DE you prefer - Kubuntu - in this situation. You can still install and run all the server stuff just fine.

So ... onto your self-inflicted issue.  There are multiple ways to manage networking.  There's ifupdown, netplan, wicd, and network-manager. I don't know if KDE uses network-manager, but all the Gnome-based DEs do.  Netplan uses files in /etc/netplan/ to manage configurations.  network-manager doesn't know anything about these, so it ignores them.  It might be possible to tell netplan to use network-manager, assuming that is installed with all the integrations you need/want back into the GUI.  Because this isn't normally done, it is a risk to try, but it could work, maybe.

ifconfig has been deprecated for a few years, BTW. Use 'ip' instead. At some point, it will not provide correct data.

---

### Post by No_Gate$ on 2021-03-14
> **TheFu said:**
>   Netplan uses files in /etc/netplan/ to manage configurations.  network-manager doesn't know anything about these, so it ignores them.  It might be possible to tell netplan to use network-manager, assuming that is installed with all the integrations you need/want back into the GUI.  Because this isn't normally done, it is a risk to try, but it could work, maybe.

Thanks for the reply. From your suggestion, edited the yaml file to use 'NetworkManager' as the renderer and the connections are now visible in the 'Connections' gui and Discover displays updates/software as opposed to no connection.

Thanks again

Paul

---

