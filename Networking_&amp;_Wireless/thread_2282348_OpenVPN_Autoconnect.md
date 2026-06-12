---
title: "OpenVPN Autoconnect"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by stu-y on 2015-06-13
Hi all,

I am trying to get Ubuntu to log in to my PIA account when I log in, I have added OpenVPN and the OpenVPN addon for Network Manager. I have added my VPN details and I can successfully connect to my VPN service, however when I open my wired connection and tell it to automatically connect to VPN when using this connection. When my machine comes on it just keep saying that my network connection is disconnected and tries to connect again in a loop, if I manually click on the wired connection it will then connect and also connect to the VPN.

Does anyone have any experience on this and what I need to do to sort it out?

Thanks, hope you can help

---

### Post by Yahoé on 2015-06-28
Bump

I'd also be interested byhow to autoconnect to a VPN. I tried "/usr/lib/network-manager-vpnc/nm-vpnc-auth-dialog -s <service_name> -n <connection_name>"  as explained in help.ubuntu.com but it returns a bunch of errors.

---

### Post by nlee2 on 2015-07-01
I do this by running openvpn service.

1. Put your keys and crt in a folder such as /etc/openvpn/myconnection
2. put your myconnection.ovpn file in /etc/openvpn but name it myconnection.conf (change the paths in file as needed)

Need ubuntu 15.04 / systemd for the following commands to work

ln -s /lib/systemd/system/openvpn@.service /etc/systemd/system/openvpn@myconnection.service
systemctl enable [email]openvpn@myconnection.servic[/email]e
systemctl start [email]openvpn@myconnection.servic[/email]e

Now openvpn client connection will start at boot

---

