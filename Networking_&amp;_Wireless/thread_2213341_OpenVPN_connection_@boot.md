---
title: "OpenVPN connection @boot"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by eclectik on 2014-03-26
Good morning. Im running 13.10, headless. So have no access to "Network Manager".

I have recently taken out a subscription for a VPN account. Id like my Ubuntu box to connect at boot and to maintain the connection once started. 

Looking around I seem to keep coming across set up's using Network Manager or starting an actual OpenVPN server. 

I've installed OpenVPN with apt-get and to that affect its running when I manually connect in a shell. If anyone has a nice .conf they wouldnt mind sharing that hopefully has username/password support to connect the .ovpn file then Id be very grateful

Thanks,
Nige

---

### Post by eclectik on 2014-03-27
So, I was being a tool, I know. Sorted the problem.

For anyone else struggling, an .ovpn is a config, just pick the one you want, rename it client.conf and you can launch it with:

[I] sudo nohup  openvpn --config /etc/openvpn/client.conf &

[/I]Theres likely a more efficient way but so far she's been connected for over 32 hours without problem

EDIT:

To finish. If you edit: */etc/default/openvpn*

you can define your client.conf (which I renamed from a provided .ovpn) and add a line to the client.conf: [I]auth-user-pass login.conf

[/I]Then create login.conf in the same directory (*/etc/openvpn*) and add just two lines, first being username. second being password. Then your all set, on 13.10 atleast, on boot openvpn connects to my chosen VPN.

You can confirm this on cli by typing *curl ifconfig.me *and checking the IP displayed.

---

