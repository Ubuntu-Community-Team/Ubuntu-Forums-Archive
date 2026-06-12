---
title: "Configure dns-nameservers only in interface file"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by Xraizor on 2015-10-10
Hi everybody

I'm pretty new to Linux and I have a problem to configure my network settings..
I have red that for network configuration you should edit the /etc/network/interfaces file.
So I tried to configure only my dns servername what does not work as I expected.
First I tried to make a static entry where I only inserted the dns-nameservers line, what ofc did not work.
Then I tried to add it to a dynamic entry, what also doesn't work (see quote below).
And now I'm not sure if it's even possible to set only the dns-servernames and let the other data apply through DHCP.
When I changed the ip in the resolv.conf it could not resolve any other URL in the browser, so I recovered the original state of the file.
So is there a way that I catch my aim?

> 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
dns-nameservers 192.168.0.1


---

### Post by SeijiSensei on 2015-10-11
The NetworkManager GUI has an entry where you can set the nameservers you want to use and override any provided by DHCP.

A better solution, though, is to edit the DHCP server configuration on your router and specify the name server addresses you want it to distribute there.

---

