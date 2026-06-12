---
title: "Using Cisco VPN or AnyConnect or else?"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by ofnuts on 2014-10-31
I need to connect to a VPN for which Windows users are given 1) a Cisco VPN Client V5, 2) a PCF file (with encrypted group password) and 3) an id/password.

I have a WinXP VirtualBox from which I can use the VPN with the above, but this somehow restricts me to what I can do under Windows (not much, or not easy).

I'd like to connect to that VPN directly from my Ubuntu. My options:


[LIST=1]
[*]Find an old Cisco VPN client (but where? Doesn't seem distributed anymore? Are there 64-bit versions or 64-bit compatible?) which hopefully would accept the PCF file directly 
[*]Use Cisco AnyConnect but the configuration is now an intractable XML file. Unless there is some way to convert the PCF to usable XML? What about the encrypted group password? 
[*]Use some other software (which), but this would also require to unravel the PCF file. 
[/LIST]

Needless to say, in this all-Windows shop, I am a complete alien, so I cannot really expect help, even if there is a slight chance that if I wring enough arms, I may be able to obtain the original group password, but if I can avoid it that's all the better.

Any ideas?

---

### Post by bashiergui on 2014-11-02
If you're connecting to a corporate network then talk to the admin. 

When you connect to a VPN it will give you a connection into the internal network but you will use native programs to interact with the network. So if it's a Windows network they will probably expect MS Office products. You *might* be able to use libreoffice or openoffice. If you're "restricted" in XP, it might be because you don't have compatible apps installed on your VM.

They might also be doing host checking before they allow VPN connections, where they ensure the clients meet certain criteria. The only people that know what that criteria is are the network admins.

In the past when I remotely connected to a Windows shop I used RDP, which doesn't require any apps installed on the Linux client except rdp. Again, you'll have to check with your admins to see if that's allowed.

---

### Post by ofnuts on 2014-11-02
> **bashiergui said:**
> If you're connecting to a corporate network then talk to the admin. 

When you connect to a VPN it will give you a connection into the internal network but you will use native programs to interact with the network. So if it's a Windows network they will probably expect MS Office products. You *might* be able to use libreoffice or openoffice. If you're "restricted" in XP, it might be because you don't have compatible apps installed on your VM.

They might also be doing host checking before they allow VPN connections, where they ensure the clients meet certain criteria. The only people that know what that criteria is are the network admins.

In the past when I remotely connected to a Windows shop I used RDP, which doesn't require any apps installed on the Linux client except rdp. Again, you'll have to check with your admins to see if that's allowed.


The poilcy matters have been dealt with. My only problem is getting a Linux-based VPN connection, when the VPN person only knows about Windows VPN clients.

---

### Post by bashiergui on 2014-11-02
Right. Did you determine if they're doing host checking? What native apps are required to do whatever you need to do on the VPN?

---

### Post by ofnuts on 2014-11-03
For the moment I cannot even connect...

---

### Post by ofnuts on 2014-11-03
Solved the problem:

[LIST]
[*]Got a VPNC debian package from [here]("http://backports.debian.org/debian-backports/pool/main/v/vpnc/") and installed it.
[*]Configured following instructions [here]("http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-with-vpnc/") (and the PCF files and credentials I had).
[/LIST]

Got me connected in no time.

---

