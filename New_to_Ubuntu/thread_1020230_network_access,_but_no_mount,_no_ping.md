---
title: "network access, but no mount, no ping"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by randym on 2008-12-23
I have recently installed Ubuntu 8.10 with gnome desktop and have kept current with all updates. My machine is called legolas, at 192,168.0.23 (DHCP from my router)

I have a predominantly Windows network, but once I get everything working with Ubuntu, will phase out Windows.

I have a Windows XP server called gandalf, at 192.168.0.3, that has a number of shares. I can access these shares by 'connecting to server' gandalf or by accessing smb://randy@gandalf/music from the file browser

If I try to ping gandalf, I get host unknown. If I ping 192.168.0.3, I get the usual message that the destination host is not reachable.

If I try to mount, following numerous threads, using

[INDENT][/INDENT]sudo smbmount //192.168.0.3/music /mnt/gandalf -o username=randy,password=******

I get mount error 113 = no route to host.

Any ideas? I'm assuming that once I fix "the problem", I'll be able to ping and then to mount (ultimately, persistent mounts).

Thanks,

Randy

---

### Post by cmnorton on 2009-01-08
Your Ubuntu system will only know gandolph if gandolph is in your /etc/hosts or some system is serving as a LAN DNS server. I cannot ping my Windows XP workstation on my home network, and that's because my anti-intrusion/virus software does not accept SMTP inbound.

Assuming you are running some product like Symantec, you'll need to make peace on your Windows system so you can access it. I had to turn on a lot of stuff through my firewall just to get VPN to work. The name resolution is the least of your worries; just put gandolph in /etc/hosts.

---

### Post by albinootje on 2009-01-08
> **randym said:**
>  I have a Windows XP server called gandalf, at 192.168.0.3, that has a number of shares. I can access these shares by 'connecting to server' gandalf or by accessing smb://randy@gandalf/music from the file browser

If I try to ping gandalf, I get host unknown. If I ping 192.168.0.3, I get the usual message that the destination host is not reachable.


The difference is that for pinging you need a "real" hostname, and the host that you want to ping needs to return your ping requests before you can get a nice output.

The fact that you can reach gandalf via smb:// is because MS-Windows (and Samba) uses NetBIOS names.
See here : [http://en.wikipedia.org/wiki/NetBIOS](http://en.wikipedia.org/wiki/NetBIOS)

Putting gandalf and legolas in your /etc/hosts is the easiest solution to make those hostnames work on your Ubuntu machine.

```

# example of /etc/hosts
127.0.0.1       localhost
127.0.1.1       your-desktop

192.168.0.3     gandalf
192.168.0.23    legolas

```

---

