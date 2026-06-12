---
title: "Using vpnc instead of legacy cisco client"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by bfuzze on 2014-10-01
I've got a couple of clients that use these legacy Windows Cisco clients.  They issue host and group credentials.

I can connect using the Windows client with no problems, but vpnc (via the network-manager) won't connect.

The only settings in the Windows clent are host, group authentication (checked), group name, group password, and transport: NAT/UDP.

On Ubuntu 14.04: Network icon > Edit connections > [my-vpn-connection] > Edit
I have Gateway set to host, 'user name' and 'group name' set to group name, 'user password' set to not reuired, and I set group password to always ask.
  If I set group password to saved, it fails immediately.  As always ask, it prompts me before "... no valid VPN secrets.".  
  Tried leaving user name empty.
  Tried using same password for user and group.
  Tried various security configurations (encryption: strong, weak, none)

Any suggestions

Similar [thread]("http://ubuntuforums.org/showthread.php?t=1526015&highlight=cisco+vpn+group+authentication"), but no help here.

---

### Post by gordintoronto on 2014-10-02
Have you tried openvpn?

---

### Post by bfuzze on 2014-10-03
Tried installing network-manager-openvpn which in turn install openvpn and network-manager-openvpn-gnome.  

Initially, when I went to create a new vpn profile I selected openvpn from the dropdown, hit create and it just hung for a couple minutes then eventually it crashed.  It should be noted that a number of applications have been behaving this way since I installed Ubuntu 14.  

I tried again and got to the profile setup form, but I don't see any settings for group authentication (?).

---

### Post by gordintoronto on 2014-10-03
Do you have cert and other VPN-related files? My vpn folder contains seven files, but I'm not sure I need them all. I run this script:
cd ~/vpn
sudo openvpn --config [server]-udp-[a number].ovpn

The items in the square brackets are private....

---

