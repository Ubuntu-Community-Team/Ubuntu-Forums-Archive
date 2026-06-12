---
title: "How to config /etc/network/interface"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by satimis on 2014-03-28
Hi all,

Ubuntu 12.04 64bit

Network:
FTTH (Fiber To The Home) Optic Fibre Network

Cable connection:
ISP -> Ont -> PC

Ont (please see attached photo)

Interface - Internet, without password

Please advise how to configure /etc/network/interface ?

Do I need to procure following info from ISP ?```

(TYPE: GATEWAY)
(TYPE: WAN IP)
(TYPE: BROADCAST)
BB GATEWAY:

```

Thanks in advance.

Rgds
satimis

---

### Post by steeldriver on 2014-03-28
Are you using a Desktop (GUI) or Server (CLI)? Desktops should probably configure interfaces via the GUI applet rather than /etc/network/interfaces

What is the make and model of the "Ont" - in particular is it a modem/router or a plain modem? The picture doesn't really help.

---

### Post by satimis on 2014-03-28
> **steeldriver said:**
> Are you using a Desktop (GUI) or Server (CLI)? Desktops should probably configure interfaces via the GUI applet rather than /etc/network/interfaces
Hi,

Desktop

Whether you meant network-manager-gnome ?

$ apt-cache policy network-manager-gnome```

network-manager-gnome:
  Installed: 0.9.4.1-0ubuntu2.3
  Candidate: 0.9.4.1-0ubuntu2.3
  Version table:
 *** 0.9.4.1-0ubuntu2.3 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.4.1-0ubuntu2 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

How to start it?  I can't start it on terminal as root.

> 
What is the make and model of the "Ont" - in particular is it a modem/router or a plain modem? The picture doesn't really help.
I just received a photo from the new ISP.  I'll ask for detail later.

Rgds
satimis

---

### Post by steeldriver on 2014-03-28
network-manager-gnome is the *package* - the actul GUI applet is called nm-applet, but it should be running already (the icon will be a fan or an up/down arrow depending whether you have a wired connection or not). If you can't find the icon you can access the settings from a terminal by typing **nm-connection-editor**

**However** if you don't actually have the box yet I'd sit tight and wait - it may well just work when you plug everything together (all it needs is a DHCP/DNS service provided by the "Ont" box, after that it should auto configure a default wired connection for you).

BTW did you have to provide your computer's MAC address to your ISP when you signed up for the service? That's the only gotcha I'm aware of with cable modems.

---

### Post by satimis on 2014-03-28
> **steeldriver said:**
> network-manager-gnome is the *package* - the actul GUI applet is called nm-applet, but it should be running already (the icon will be a fan or an up/down arrow depending whether you have a wired connection or not). If you can't find the icon you can access the settings from a terminal by typing **nm-connection-editor**

I found it.  On clicking the icon it drops down a list of service```

VNPs Connection
Enable Networking
Connection Information
Edit Connections ...

```

> 
**However** if you don't actually have the box yet I'd sit tight and wait - it may well just work when you plug everything together (all it needs is a DHCP/DNS service provided by the "Ont" box, after that it should auto configure a default wired connection for you).

It has been confirmed by the new ISP that no logon name and password are required for connecting their server.

Just confirmed by them that "No manual of ONT to be supplied as no configuration can be set by client’s side" upon my request for ONT manual.

> 
BTW did you have to provide your computer's MAC address to your ISP when you signed up for the service? That's the only gotcha I'm aware of with cable modems.
No

satimis

---

