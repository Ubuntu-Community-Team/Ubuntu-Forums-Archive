---
title: "How apply a vpn (openvpn) on a hotspot with a bridge on eth0 and wlan0"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by CARADANT on 2015-11-21
[COLOR=#111111][FONT=Ubuntu]Hi everyone, 

I created a hotspot with a bridge eth0 wlan0 in /etc/network/interfaces, for Android and Windows from Linux. It works. This was my first problem.
[Hotspot created and connected from linux but no internet access on phone]("http://askubuntu.com/questions/699995/hotspot-created-and-connected-from-linux-but-no-internet-access-on-phone")
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now, I try to connect my vpn on this hotspot on Linux but I can t because the network manager said me : device not managed for WiFi and ethernet. 
So I don t know where I can looking for to do this the most simple possible :/. 
I TRIED to follow this:
[http://www.slsmk.com/getting-started-with-openvpn/installing-openvpn-on-ubuntu-server-12-04-or-14-04-using-tap/](http://www.slsmk.com/getting-started-with-openvpn/installing-openvpn-on-ubuntu-server-12-04-or-14-04-using-tap/) 
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]but everytime I reboot my vps, I can t to connect on this by ssh... I have to fail something in /etc/network/interfaces[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I think.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
And I m not sure that I have to follow this, to sucess to connect my vpn on this hotspot. I Just tried to see the result :/
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks you for you suggestion and help :)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is my /etc/network/interfaces[/FONT][/COLOR]

auto lo
iface lo inet loopback
#wired adapter
iface eth0 inet dhcp
#bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0 wlan0

---

