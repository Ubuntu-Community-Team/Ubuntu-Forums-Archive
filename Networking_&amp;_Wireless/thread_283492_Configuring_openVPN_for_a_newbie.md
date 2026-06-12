---
title: "Configuring openVPN for a newbie"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by freshtoast on 2006-10-24
A linux-newbie question I'm afraid!
Is anyone able to elaborate on these instructions for installing Witopia's
personalVPN:

> 
1. Install OpenVPN on your Ubuntu partition
2. Copy all of the files from your C:\Program Files\WiTopia.Net\config directory on your WinXP partition to your Ubuntu partition
3. Edit your config file and update the following lines:

remote vpn.witopia.net 1194
ca path-to-ca-certificate (i.e. /usr/local/ssl/certs/ca.crt)
key path-to-private-key (i.e /usr/local/ssl/private/name.key)
cert path-to-signed-certificate (i.e. /usr/local/ssl/certs/name.crt)

I'm afraid I've got as far as "sudo apt-get install openvpn", and copying the relevant files onto a CD from a windows installation! :oops:

Now I have no idea where to copy those files too, and what config file am I supposed to be editing?!

I'm sure it is a very simple procedure but I am very much at the bottom of the ubuntu learning curve!

Many thanks

---

