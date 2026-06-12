---
title: "Wired network not using Reserved IP on Arris TG862G"
date: 2014-11-15
forum: Networking &amp; Wireless
---

### Post by nilandj-nilandsplace on 2014-11-15
Hello
I am having a heck of a time getting Ubuntu 12.04 to use the Arris TG862G router/modem's Fixed DHCP Clients. On my laser printer I just set the ip to 192.168.0.7 and it works, but in ubuntu it won't connect to 192.168.0.5 reserved for it. in the network GUI I have tried Automatic (DHCP), Automatic (DHCP) addresses only and Manual. On manual it will use the IP, but then I cannot connect to the internet. On Automatic (DHCP) addresses only it will not connect to 192.168.0.5 but it connects to 192.168.99.195 for IPv4. I have
[ATTACH=CONFIG]257984[/ATTACH][ATTACH=CONFIG]257985[/ATTACH]
 I don't know what "Search domains:" is for. I have the Arris set up this way
[ATTACH=CONFIG]257986[/ATTACH]
The first one is my desktop, the second one is the printer and the third one is my VoIP box
I have tried editing the /etc/network interfaces and static interfaces, but it does not change anything
(The x's to hide info in place of the real IP)
############
auto lo
iface lo inet loopback

Wired connection eth0 
iface eth0 inet static
address 192.168.0.5
gateway 192.168.0.1
netmask 255.255.255.0
dns-nameservers 208.xx.xxx.xxx 208.xx.xxx.xxx
#################
auto lo
iface lo inet loopback

Wired connection eth0
iface eth0 inet static
address 192.168.0.5
gateway 192.168.0.1
netmask 255.255.255.0
dns-nameservers 208.xx.xxx.xxx 208.xx.xxx.xxx
or
dns-nameservers 209.xx.xxx.xxx 209.xx.xxx.xxx
################
With and without the OR dns-nameserver and with and without the Wired connection eth0
I just don't understand why Ubuntu will not pick up the address 192.168.0.5. The printer and VoIP box was easy.
My goal is to be able to download backups from my server, but I can't get a connection. I also have DynDNS set up and it will not work either?

[ATTACH=CONFIG]257987[/ATTACH]

I have Ubuntu server 12.04 LAMP on my destop computer with FTP-Pro and GADMIN-PROFTPD, but it likes a static IP.
I don't see why this is so hard. It is just a stupid LAN IP. I have done my research. the pages for the router don't look like mine from [http://arrisi.force.com](http://arrisi.force.com) and the Ubuntu mostly has terminal descriptions (no GUI) and I have checked all that I understand in Webmin for the localhost LAMP.
HELP ME!
Thanks James Niland

---

