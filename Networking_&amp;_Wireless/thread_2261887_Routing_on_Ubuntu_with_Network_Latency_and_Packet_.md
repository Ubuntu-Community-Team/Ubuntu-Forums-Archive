---
title: "Routing on Ubuntu with Network Latency and Packet Loss"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by sensie2 on 2015-01-21
hi Friends,

i am new to Ubuntu..

i have install Ubuntu Server with 7 Ethernet Ports i need to enable routing between these ports every port will be in different subnet.

Ex:
eth0: 172.25.25.1  255.255.255.248
eth1: 172.25.25.9  255.255.255.248
eth2: 172.25.25.17 255.255.255.248
eth3: 172.25.25.33 255.255.255.248

after that i will need to Add **Network Latency and Packet Loss Emulation .. ** (**[COLOR=#0000cd]NetEM[/COLOR]**)

please when you replay keep in mind that i am [COLOR=#ff0000]**Network Engineer**[/COLOR] that know [COLOR=#ff0000]nothing [/COLOR]about Ubuntu and don't know how to navigate in VIM Edit for text.

Thanks A lot

---

### Post by sensie2 on 2015-01-21
Friends, 

As start i need to know how to configure the Interfaces with the Correct IP Addresses?

i open the file /etc/network/interfaces using the command
sudo vim /etc/network/interfaces

then i press [a] to be able to write and and [Esc then write :wq to Save and quit]

[B][FONT=Courier New]auto eth0[/FONT]
[B][FONT=Courier New]iface eth0 inet static[/FONT]
[B][FONT=Courier New]address 10.10.6.203[/FONT]
[B][FONT=Courier New]netmask 255.255.255.0[/FONT]
[B][FONT=Courier New]gateway 10.10.6.203 [/FONT]
[B][FONT=Courier New]
[/FONT][B][FONT=Courier New]auto eth1[/FONT]
[B][FONT=Courier New]iface eth1 inet static[/FONT]
[B][FONT=Courier New]address 10.10.6.204[/FONT]
[B][FONT=Courier New]netmask 255.255.255.0[/FONT]
[B][FONT=Courier New]gateway 10.10.6.2 

[FONT=arial]but it's not working ??? should i add another command that are missing here ? 
[/FONT][/FONT]
help guys
thanks[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]

---

### Post by sensie2 on 2015-01-21
i complete the configuration for the interfaces and enable the IP Forwarding .. all is left is to add the delay and packet loss

i thought this forum is active ? i didn't get any help !!!

---

