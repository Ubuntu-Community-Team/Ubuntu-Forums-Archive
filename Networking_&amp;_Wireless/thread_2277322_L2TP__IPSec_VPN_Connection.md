---
title: "L2TP / IPSec VPN Connection"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by Muntrue on 2015-05-08
I can't for the live of me figure this out. I have been trying for a few hours now to get a L2TP/IPSec connection going but its just not happening.

I am using the standard network-manager in Kubuntu 14.04, I am unsure what additional packages I installed over the past few hours because I have been trying so much.

I enter all the correct info into the L2TP Network-Manager connection window and save the settings, This is the config file it creates:

```
[connection]
id=connection
uuid=9a6ff370-0fe0-463a-a08d-442bf9b0b460
type=vpn
permissions=user:muntrue:;

[vpn]
service-type=org.freedesktop.NetworkManager.l2tp
gateway=<my_gateway>
ipsec-psk=<my_shared_key>
user=Mario
ipsec-enabled=yes
password-flags=2 

[ipv4]
method=auto
```

But when I try to start the connection I first get:

```
> nmcli con up id vpnconnection
Error: Connection activation failed: no valid VPN secrets.

```

But when I try it again it will give me:

```
> nmcli con up id vpnconnection

** (process:16365): WARNING **: Could not create object for /org/freedesktop/NetworkManager/ActiveConnection/104: Method "GetAll" with signature "s" on interface "org.freedesktop.DBus.Properties" doesn't exist

Error: Connection activation failed: Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/104' failed in libnm-glib.
```

I am at a loss here and really hope someone has some answers or can point me in the right direction.

Thanks in advance!

---

### Post by etescartz on 2015-05-08
I'm not sure but I think you might need some additional packages installed. I used to run it from command line.
I think I had the "vpnc" package installed. 

Nowadays I install ShrewSoft VPN if I need graphical VPN connection management. 

Sorry for not getting all the details , but I think you can narrow your search with what I said.

---

