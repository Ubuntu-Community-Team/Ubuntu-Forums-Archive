---
title: "network-admin gone AWOL"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Efros on 2008-06-26
Hardy 8.04, network-admin has gone bye byes, even the applet has disappeared from the system tray. Everything seems to be working ok as far as internet and local networking, apart from browsing shares on windows machines but that never worked anyway. I can enter smb://IP.ad.re.ss/sharename to access my shares bit of a bugger if you can't remember the share name but it worked at least. But methinks something more serious has happened. System>Administration>Network brings up an error Could not launch menu item, Failed to execute child process "network-admin" (No such file or directory) and that's that. Checked the interfaces file and got 
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


ifconfig yields 

> eth0      Link encap:Ethernet  HWaddr 00:e0:4d:3b:ce:1e  
          inet addr:192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe3b:ce1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47548266 (45.3 MB)  TX bytes:32038743 (30.5 MB)
          Interrupt:247 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160962 (157.1 KB)  TX bytes:160962 (157.1 KB)


any help would be appreciated.

---

### Post by Efros on 2008-06-27
Nobody got any ideas on how to return network-admin apart from a reinstall?

---

### Post by prshah on 2008-06-27
> **Efros said:**
>  network-admin has gone bye byes, even the applet has disappeared from the system tray.


You can try bringing back the applet by opening a terminal and giving the command```
nm-applet
``` If it doesn't work, the error output might be useful for diagnosis.

If it works, note that it will close down when you close the terminal. In that case, press Alt+F2, and give the same command. It should reappear, and it should be persistent across reboots, otherwise you may have to add it to System-Preferences-Sessions-Startup Programs.

---

### Post by Efros on 2008-06-28
Thanks for the reply, unfortunately twas one of the first things I tried, problem solved by reinstall, drastic but other stuff was misbehaving too.

---

### Post by spetey on 2009-12-16
In trying to change my DNS, I just noticed my network-admin has mysteriously disappeared in 9.10; "System > Administration" had only "Network Tools" and no "Network" option.  I thought maybe they'd moved network configuration somewhere else but couldn't find it anywhere, or any information on the web except this forum.  I eventually just installed gnome-network-admin from synaptic, and now it shows up in the system > admin menu.  What the?!

---

