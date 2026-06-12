---
title: "Odd: Network Manager on Intrepid just stopped funcioning."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by OverlordManny on 2009-01-04
Ok Here's my issue and a little back ground info.

Server, laptop, and desktop all running Intrepid desktop version.

I have a local server running the desktop version of Intrepid. It's on a local static IP address (dhcp on this server has been uninstalled.). I have nfs running on it and I have a shared folder on this server that I mount on my desktop and laptop to a local folder through fstab. This has been up and running fine since the beginning of November. Yesterday I was accessing some videos from the shared folder (via NFS not Samba) and one video began to stop and lock up my desktop in the process. I tried the video again and it played fine for a while and locked up again at a different point. I later found that I had lost total access to the server, no remote desktop no shared folder, nothing. So I swap my monitor to my server and lo and behold nm-applet tells me the network is disabled. I look into the wired connections and find an oddly named connection (unfortunately I don't remember the name but I know I didn't make it.) that has no settings applied to it at all, (ie. no IP, Gateway, etc.) The weird thing is I can still access the internet from the server. Since the network manager is down (I assume) I just can't access the server with nfs). Any changes made with nm-applet are not used, as if it is totally non functional now.

There were no updates to the server that are concurrent with this problem. What I mean is I haven't changed anything software wise (including updates since the middle of November.

/etc/network/connections

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1



Output of sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:e6:28:ef
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:e2:1d:86:bf:52
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


The only thing that I can think of that may have any relation to this is that I had my DSL modem die on me and had to replace it. All systems are on a linksys wireless router though all but the laptop are wired connections. The server is set to static and is not controlled by the router's DHCP as the IP is out of router's DHCP range.

I have reinstalled Network Manager on the server through synaptic but I'm hesitant to to a complete remove and reinstall for fear of losing the internet connection I have now.

Any help? I'm not a total noob but this has me scratching my head since it was out of the blue.

Oh one more thing I have, since this has happened, updated with system update on the server.

---

### Post by OverlordManny on 2009-01-04
Ok so I just saw an error with my CD drive involving dbus. Im going to look into this since it could be part of my issue with NM. 

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by OverlordManny on 2009-01-04
Ok I'm pretty sure this is a dBus related issue since after closing this error I can now access my shared nfs directories, though I have googled the heck out of this error I have not found any solutions. It does seem a fairly common error in Intrepid, well, all of versions of ubuntu really, though I've never seen it in the past 2 years. I don't think I'm going to press my luck and let it sit though. I'm going to reinstall. This makes me a bit sad but I'm not going to chance it. Plus it'll give me a chance to install another hard drive to have separate physical drives for os and data storage.

---

### Post by OverlordManny on 2009-01-04
Ok so I learned something more thank goodness I didn't reinstall yet. 

The network manager problem WAS the result of an update. Apparently I just had not realized it all this time since my server is headless. Anyway...
If you are having problems with nm-aplet saying devices not managed check here for a fix. Worked for me.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417)

NOW I still have to find the dBus problem.

---

