---
title: "Ethernet connection not working Lubuntu 17.04 specific computer"
date: 2017-08-08
forum: Networking &amp; Wireless
---

### Post by cedbomb on 2017-08-08
I have a server that I use for backups. Its an old HP tower. It was  working fine with Debian Jessie until I moved it somewhere else with  another router and modem where it wont connect. To try to resolve the  issue, I installed Lubuntu 17.04. I can connec my laptop running Debian  Jessie to internet without issue. My router is a Dlink 860-L set-up for  DHCP. My ethernet chip controller on my server is the 82567LM-3 from  Intel.

  On the network manager, on boot up I can see the connection but I  doesn't stays connected. I cant run ifconfig right now since Lubuntu  doesn't ship with it and I did not install it since I can't connect to  internet. When I was on debian, Eth0 showed up after running ifconfig.  When I plug the server directly to my laptop, it sees the connection but  wont connect. I think the issue is in the configuration of my machine or  in the router. I really dont know where to go from here. I already  tried to edit NetworkManager.conf and dhclient.conf. I cant remember  what I tried to edit in those files but there in their original  condition. I also added in /etc/network/interfaces auto eth0 but it did  not work. I have really noooooo idea where to go from here. Thats why I  am asking for help. I am open to all your suggestion. What bug me is  that it used to work at my other place... Thanks in advance :) !

  Cedric from Montreal !

---

### Post by Hadaka on 2017-08-09
Hi, did you load...Desktop Lubuntu 17.04....Desktop Server Lubuntu 17.04...or..Server Lubuntu 17.04 ??
The 82567LM-3 chip  looks like it uses the e1000e driver.. Try it with..
```
sudo modprobe -v e1000e
```
Let's see what the pci-id is to verify the driver..please do and post
```
lspci -n | awk '/200/{print$3}'
```
```
cat /etc/network/interfaces
```
Not sure about Lubuntu but every ubuntu no longer uses eth0...it changed
take a look at..
```
ifconfig
```
To see what the ethernet is now called.
Thanks.

---

