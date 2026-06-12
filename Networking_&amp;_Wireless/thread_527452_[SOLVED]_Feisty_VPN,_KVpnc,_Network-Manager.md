---
title: "[SOLVED] Feisty VPN, KVpnc, Network-Manager"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by ssergeje on 2007-08-16
Hi!
I would like to connect to my corp OpenVPN. Network-manager has a fancy GUI for that, but it fails to connect. This is due I was given only a CA file, no key or certificate (my cert that is). And it desperatly needs them.

I was luckly enough to connect through KVpnc, as it imported the windows' OpenVPN conf file, only needed to change the paths. 

The tun device is up, but theres no traffic going through it. Only about 300Kb. KVpnc's log shows, that everything is up&running. I guess I need to force NetworkManager to use the tun device. How do I do that?? Google doesn't give the answer ](*,)
Others advices are also welcome

Cheers,
Ser

---

### Post by ihristov on 2007-08-17
Forget Network Manager for the time being. You need to first make sure the OpenVPN client works properly.

Start it directly

```
cd ~/.openvpn
sudo openvpn office.ovpn
```

Thisis of course assuming your config file is called office.ovpn
I am first switching to the folder, because my config file does not have fully qualified paths and it needs to find the external referenced files.

Content of office.ovpn

```
#OpenVPN Server conf
tls-client
client
dev tun
proto tcp
remote openvp.server.com 636
pkcs12  cert.user-server.com.p12
cipher BF-CBC
comp-lzo
verb 3

```

and you obviously need to have the .p12 file (with your private cert) referenced above
and adjust the protocol, port and server name.

Once you are able to connect like this, then you can worry about Network Manager.

Frankly I opted to not use the Network Manager UI, because it stores your password in your keyring and then you can actually see your plain password inside the "Keyring Manager" interface.

---

### Post by ssergeje on 2007-08-27
I tried the CLI openVPN. It worked :guitar: , I only had to edit paths to the cert file.
It worked all before. I didn't notice cause host names are not provided and I needed to surf the intranet with IPs instead of text addresses. This could be fixed with joining corp domain with samba I guess :-k or simply configuring the [FONT="System"]/etc/hosts[/FONT] file
You can check if your VPN connection works with [FONT="System"]ip route show[/FONT] You'll see some corporate IPs there. GIYF ;)

---

