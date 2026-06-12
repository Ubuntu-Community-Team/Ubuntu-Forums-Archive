---
title: "Help setting up an open VPN"
date: 2016-04-16
forum: Networking &amp; Wireless
---

### Post by joshua75 on 2016-04-16
I'm following this guide on how to setup an OpenVPN. [http://www.vpnbook.com/howto/setup-openvpn-on-ubuntu](http://www.vpnbook.com/howto/setup-openvpn-on-ubuntu)
So far I came to the point where I should type this command: "openvpn --config vpnbook-euro1-tcp443.ovpn". Here I'm stuck with this error "Options error: In [CMD-LINE]:1: Error opening configuration file: vpnbook-euro1-tcp443.ovpn
Use --help for more information."

Hope someone can help since I'm new to Ubuntu and Linux in general.

---

### Post by slickymaster on 2016-04-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by howefield on 2016-04-16
> **joshua75 said:**
> So far I came to the point where I should type this command: "openvpn --config vpnbook-euro1-tcp443.ovpn". Here I'm stuck with this error 

Navigate to where you extracted the file that you downloaded and run the command from that folder or precede the filename with the path to the extracted files eg, if you extracted the .ovpn files to your Downloads folder..

```
openvpn --config ~/Downloads/vpnbook-euro1-tcp443.ovpn
```

---

