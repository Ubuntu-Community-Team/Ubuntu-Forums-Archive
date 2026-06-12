---
title: "can't connect with VPN since 16.04 LTS upgrade"
date: 2016-09-01
forum: Networking &amp; Wireless
---

### Post by TommyAlfaro on 2016-09-01
I cannot make VPN with anything since a made the last upgrade , i think it's a problem with this Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so but i don't know what happened


this is my log


```
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746232.4553] audit: op="connection-activate" uuid="65806e76-279
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746232.4668] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746232.4865] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746232.6863] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: ** Message: pppd started with pid 7095
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746232.6946] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: /usr/sbin/pppd: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so is for ppp
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: ** (nm-pptp-service:7086): WARNING **: pppd exited with error code 2
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <warn>  [1472746232.7811] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <warn>  [1472746232.7812] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:10:32 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746232.7838] vpn-connection[0x14695b0,65806e76-2790-42ea-ba17-f
Sep 01 10:13:38 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746418.1095] keyfile: update /etc/NetworkManager/system-connect
Sep 01 10:13:38 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746418.1103] audit: op="connection-update" uuid="65806e76-2790-
Sep 01 10:14:30 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746470.4876] keyfile: add connection /etc/NetworkManager/system
Sep 01 10:14:30 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746470.4922] audit: op="connection-add" uuid="52183dac-ee41-4ce
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746476.5964] audit: op="connection-activate" uuid="52183dac-ee4
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746476.6135] vpn-connection[0x14693c0,52183dac-ee41-4cee-9d62-7
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746476.6354] vpn-connection[0x14693c0,52183dac-ee41-4cee-9d62-7
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746476.8456] vpn-connection[0x14693c0,52183dac-ee41-4cee-9d62-7
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: ** Message: pppd started with pid 7219
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746476.8556] vpn-connection[0x14693c0,52183dac-ee41-4cee-9d62-7
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: /usr/sbin/pppd: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so is for ppp
[COLOR=#b22222]Sep 01 10:14:36 tommy-OptiPlex-745 pppd[7219]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so is for pppd version 2.4.7, this is 2[/COLOR]
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: ** (nm-pptp-service:7211): WARNING **: pppd exited with error code 2
Sep 01 10:14:36 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472746476.9352] vpn-connection[0x14693c0,52183dac-ee41-4cee-9d62-7
Sep 01 10:34:48 tommy-OptiPlex-745 dhclient[2612]: DHCPREQUEST of 10.0.0.7 on eth0 to 10.0.0.1 port 67 (xid=0x2d0e27f0)
Sep 01 10:34:48 tommy-OptiPlex-745 dhclient[2612]: DHCPACK of 10.0.0.7 from 10.0.0.1
Sep 01 10:34:48 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472747688.1900]   address 10.0.0.7
Sep 01 10:34:48 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472747688.1901]   plen 24 (255.255.255.0)
Sep 01 10:34:48 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472747688.1901]   gateway 10.0.0.1
Sep 01 10:34:48 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472747688.1901]   server identifier 10.0.0.1
Sep 01 10:34:48 tommy-OptiPlex-745 NetworkManager[2360]: <info>  [1472747688.1901]   lease time 18000
```

---

### Post by yonnie on 2016-09-03
Ditto, same problem.  Have tried installing **openvpn plugin gnome**.  Still get vpn connection failed message.
The vpn connection had been working on this computer with 14.04 for years, did the upgrade to 16.04 and now it won't work no matter what I try.  
BTW, VPN does work on another computer running Linux Mint 17.3

Previous settings on 14.04 and other computers connecting to remote server are not setup to use certificates, just a user name and password.  This new VPN seems to have a box for a certificate.  Is this required for a connection?  Perhaps I have the wrong VPN plugin installed?  How do I get what came with 14.04 installed?  I don't recall having to install anything to build the VPN on 14.04, it just worked, ditto for Mint and ditto for other Linux versions.  Why is 16.04 such a PITA?

---

### Post by Cthulhu336 on 2016-09-16
I'm having the same problem. I use IPVanish. Before upgrading to 16.04, I could connect with no issues at all. But since upgrade (and eventual fresh re-installation) , it still doesn't connect. It says connection refused due to fatal error. I hate having to use Windows just to access my VPN. I'm a linux junkie! I catch myself doing linux commands in windows shell, UGH. LOL. Please help. I have installed all openvpn packages I have ever needed to get my VPN to connect. So any help would be much appreciated. Thanks Ubuntu community!

---

### Post by Cthulhu336 on 2016-09-19
I think I have a follow-up. From what I can tell, my openvpn connection is sending my IPv6 address as "my" address, instead of showing my IPVanish address. I have disabled (from what I can find on Google) my IPv6 address lookup etc, but my wifi connection info shows that IPv6 address in my connection information. I don't know what to do.

---

### Post by timsdeepsky on 2016-09-19
I have had this issue since going from Ubuntu 14.04 to 16.04.
I was able to connect before easily on `14.04 with Openvpn.
With 16.04 the only way i have been able to connect is by downloading the older version 62 client.
New version 63 fails.
This is with Private Internet Access.

---

### Post by feartheterrapin on 2016-09-19
Do you have [FONT=Verdana]libcrypt11 and [FONT=Verdana]libgnutls26 installed.  I needed to add these to get PIA to install properly and work for me on 16.04LTS.[/FONT][/FONT]

[FONT=Verdana]libcrypt11 is available here: 
[https://launchpad.net/~ubuntu-security-proposed/+archive/ubuntu/ppa/+build/7110687/+files/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb]("https://launchpad.net/%7Eubuntu-security-proposed/+archive/ubuntu/ppa/+build/7110687/+files/libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb")

libgnutls26 is available here: [http://packages.ubuntu.com/precise-updates/amd64/libgnutls26/download](http://packages.ubuntu.com/precise-updates/amd64/libgnutls26/download)[/FONT]

---

### Post by timsdeepsky on 2016-09-19
I have libgnutls30 installed....I do not have libcrypt11 installed....

---

### Post by Cthulhu336 on 2016-09-24
I FINALLY GOT it to work! After googling my behind off. This is what I did (Ubuntu GNOME 16.04) 

Below is the guide how to disable IPv6 Linux/Ubuntu:


1 Open Terminal


2Enter gksudo gedit /etc/sysctl.conf and open the configuration file and add the following lines at the end


net.ipv6.conf.all.disable_ipv6 = 1


net.ipv6.conf.default.disable_ipv6 = 1


net.ipv6.conf.lo.disable_ipv6 = 1


3After that run $ cat /proc/sys/net/ipv6/conf/all/disable_ipv6


If it reports &#8216;1&#8242; means you have disabled IPV6. If it reports &#8216;0&#8216; then please follow Step 4 and Step 5.  


4Type command sudo sysctl -p you will see this in terminal.


net.ipv6.conf.all.disable_ipv6 = 1


net.ipv6.conf.default.disable_ipv6 = 1


net.ipv6.conf.lo.disable_ipv6 = 1


5Repeat above &#8220;Step 3&#8221; and it will now report 1.


Then - check it @ [http://ipv6-test.com](http://ipv6-test.com) 


NEXT - - - - - - > 


sudo apt install openvpn network-manager-openvpn network-manager-openvpn-gnome 


WIFI SETTINGS 
Clone your ethernet MAC address in Identity Section
Shut off IPv6 settings in Wifi Connection dialog box (IPv6 Tab)




VPN 
Import OPVN file 
Cut off IPv6 on that tab of Configuration




Do All This Should Work ------> :)

---

