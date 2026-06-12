---
title: "Wired network with 802.1x - IP doesn't refresh automatically"
date: 2016-09-21
forum: Networking &amp; Wireless
---

### Post by cr1zz on 2016-09-21
[COLOR=#000000][FONT=&amp]Hey all,[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I got the following problem: I want to connect a Ubuntu client via RADIUS to my network. I've done this via wpa_supplicant.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][B]
wpa_supplicants.conf[/B][/FONT][/COLOR]
[CENTER]
[/CENTER]
[I]ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=2
ap_scan=0

network={
    ssid=&#8221;802.1X&#8221;
    key_mgmt=IEEE8021X
    eap=PEAP
    identity=### DOMAIN USER ###
    password=### PASSWORD ###
    phase2=&#8220;auth=MSCHAPV2&#8220;
}
[/I]
[COLOR=#000000][FONT=&amp]The authentication works fine.
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]After that I edited the file '/etc/network/interfaces', so that the RADIUS auth will be done automatically.
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][B]/etc/network/interfaces
[/B][/FONT][/COLOR]
[I]auto lo
iface lo inet loopback

auto enp1s0f0
iface enp1s0f0 inet dhcp

wpa-driver wired
wpa-conf /etc/wpa-supplicant/wpa-supplicant.conf

[/I][COLOR=#000000][FONT=&amp]Now I have the following problem: Before the RADIUS auth the client gets an IP address of a guest net (192.250.x.x). Unfortunately the client doesn't seem to refresh the IP-address after the RADIUS auth and still holds the IP of the guest net. When I do:[/FONT][/COLOR]

[I]dhclient -r enp1s0f0
dhclient enp1s0f0[/I]

[COLOR=#000000][FONT=&amp]the client gets the correct IP-address.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]How to automate this? When I do this command via rc.local, the client still holds the guest net IP.
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Thanks in advance.[/FONT][/COLOR]

---

