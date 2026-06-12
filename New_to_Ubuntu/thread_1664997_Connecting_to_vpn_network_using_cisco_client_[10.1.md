---
title: "Connecting to vpn network using cisco client [10.10 netbook]"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by H3R3T1K on 2011-01-11
I need to use a Cisco VPN client in order to access the uni wireless. How do I do that using Ubuntu?

---

### Post by Synthetic Sam on 2011-01-11
install the network-manager-vpnc client using apt-get or synaptic e.g.

```
 sudo apt-get install network-manager-vpnc 
```

Then configure through gnome network manager (icon near to clock in top right).

All of the information for the VPN configuration dialogue can be gleaned from your .pcf file for the windows Cisco client.
 
The "secret" from your .pcf configuration file (for the windows cisco client) will probably be encrypted so you will need to use a program to decrypt it first (see [http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html)), then enter it in the decrypted form in the box for group password.

Screenshot below showing the dialogue from right clicking the network icon at the top right (and selecting edit connections) and the VPNC configuration dialogue.

Also, more info: [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

[[IMG]http://img232.imageshack.us/img232/322/vpnp.png[/IMG]](http://img232.imageshack.us/i/vpnp.png/)

---

### Post by H3R3T1K on 2011-01-12
I don't know how to open that .pcf file. What is the info that I need to enter in order to connect? Doesn't it work without the decrypting part 'cause that's beyond me...

---

### Post by Synthetic Sam on 2011-01-12
> **H3R3T1K said:**
> I don't know how to open that .pcf file. What is the info that I need to enter in order to connect? Doesn't it work without the decrypting part 'cause that's beyond me...
Use a text editor like gedit to open the .pcf file (right click and open with text editor).

Use this webpage to decrypt your Group password: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

There's no getting around it.

To connect you need:

1) Gateway IP address
2) Group Name
3) Group Password (set this as saved like above).
4) Username (possibly domain too depending on the on site configuration)

1-3 should be in the pcf

---

### Post by vangop on 2011-01-12
Synthetic Sam explained pretty much all of it. Just want to add - You can import the pcf from the network-manager gui (and also see your group pass)
see [here]("http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html")

---

### Post by H3R3T1K on 2011-01-12
Sorry for being such a noob. This is what the .pcf looks like:

[main]
Description=WLAN/Rote Dosen an der Uni
Host=ipsec-rz.vpn.uni-freiburg.de
AuthType=1
GroupName=campus
GroupPwd=
enc_GroupPwd=546EF3C7936F2A972F208CE4102AF1EB48E2AD49CE9C1DB566B9893ED65843DE447F8CC70AF0D3961E99DBFACF0B45E4
Username=ah260
SaveUserPassword=1
EnableLocalLAN=1
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPPhonebook=
ISPCommand=
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90

Where's the gateway ip address?

Well I hope none of you guys are nasty hackers trying to steal my identity [-X

---

### Post by Synthetic Sam on 2011-01-12
```

Non-authoritative answer:
Name:	ipsec-rz.vpn.uni-freiburg.de
Address: 132.230.123.41

```

That's your gateway address.

enc_password is decrypted to "campus" so that's your group password.

---

