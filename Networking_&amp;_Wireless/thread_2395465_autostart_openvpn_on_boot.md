---
title: "autostart openvpn on boot"
date: 2018-07-02
forum: Networking &amp; Wireless
---

### Post by mattdawolf on 2018-07-02
I would like to get my vpn to autostart on boot. meh. 

network-manager or nm-applet was working okay but as a consequence, raising network interfaces always failed on boot. It needs to startup on boot so the nfs mounts take successfully. Disabling network-manager got raising network interfaces on boot to work properly again. 

Doing so grays out any network management application. I want toauto connect and have the ability to connect/disconnect the VPN at will as a standard user.

manually connecting with openvpn always prompts for a username and password.

I have tried kvpnc but that is crashy. I tried kvpnc-trinity but it always wants root access.

What is the best solution here?

---

### Post by TheFu on 2018-07-02
I do this, but don't use any GUIs and have static IPs for my network. 

Which release? Different releases have changed the way that networking works.

---

### Post by SeijiSensei on 2018-07-02
Desktop versions of Ubuntu don't even start the network at boot, much less enable a VPN connection then. With wifi, the user needs to select the access point to which the connection will be made.  That cannot happen until the user logs in.

Connections at boot are much easier to establish on servers using static IPs and OpenVPN.  

As for the NFS problem, on laptops I maintain a script in /usr/local/sbin to mount all NFS shares.  I have to run it from the command prompt using sudo after logging in.

If this is a desktop machine with a wired connection, you may have more options.

---

### Post by mattdawolf on 2018-07-02
I've been finding that out the hard way. 18.04.

---

### Post by mattdawolf on 2018-07-02
Everything is static, run via wired, and it is a desktop machine.

---

### Post by TheFu on 2018-07-02
> **mattdawolf said:**
> Everything is static, run via wired, and it is a desktop machine.

I use autofs to deal with NFS mounts.  They are mounted dynamically when requested and umounted automatically after a period of unuse.  I don't use wifi.

You can make all of this work, just don't use network manager.

But alas, I don't have 18.04, which changed to netplan.  netplan.io has the best information, but some things for non-trivial setups have been giving people problems.  It doesn't sound like your setup should be any problem.

---

### Post by mattdawolf on 2018-07-02
thanks!

---

