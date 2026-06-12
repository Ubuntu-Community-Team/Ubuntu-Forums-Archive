---
title: "network adapter issues"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by sgriesel on 2016-03-30
Hi guys,

I am having a strange problem. I have only noticed it now since I have not really used my ethernet adapter port before, only been using wireless. I did some research and tried setting dns but still having issues. Something really strange happens where I can browse some pages and others not, thinking it was DNS but after configuring as below I still had issues. My wireless works fine though it is just the eth0 adapter I am having issues with.

Here is what I have tried, configured interfaces file as below:

> # The loopback network interfaceauto lo eth0
iface lo inet loopback


# The primary network interface
iface eth0 inet dhcp

Set DNS in /etc/resolv.conf to Google DNS:

> nameserver 8.8.8.8
nameserver 8.8.4.4


Any suggestions what else to try?

---

### Post by sgriesel on 2016-03-31
[COLOR=#111111][FONT=Ubuntu]Anyone able to make some more suggestions I could try to fix this? See other people also experienced same problem but when they try what I did as mentioned then their problem resolved. The only other change that was done was installing dconf to exclude sites from proxies I sometimes use, changed them all back to default so don't think dconf can be the issue?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-03-31
You don't mention which version of Ubuntu you are using (please include relevant details like this in future to help us help you) but if you are running a standard Ubuntu or one of its flavours you would probably have Network Manager installed. You should be changing things like DNS etc. in there, not in the /interfaces file. That can cause problems and the two don't play together. 

Put the /interfaces file back to what it was originally and make changes by clicking the network icon> Edit> highlight your connection> click 'Edit'> configure (DNS address goes in IPv4 tab).

---

### Post by sgriesel on 2016-03-31
Hi Bucky Ball,

Im running:

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

I have changed the interfaces file back to default and tried setting it in Network Manager, same thing :(

---

### Post by Bucky Ball on 2016-03-31
If your wireless network is working, change the DNS details to the same as the wireless ones in the wired config. Not sure why you would need to change them in the first place, though, and not sure if it has anything to do with your issue. You didn't change them for the wireless I presume so the wired shouldn't be any different.

---

### Post by sgriesel on 2016-03-31
Yep they exactly the same, this is why it is so strange to me. Here is the output:

> XXXXXX:/etc/network$ nmcli dev list iface eth0 | grep IP4
IP4.ADDRESS[1]:                         ip = 192.168.0.11/24, gw = 192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             192.168.0.2
XXXXXX:/etc/network$ nmcli dev list iface wlan0 | grep IP4
IP4.ADDRESS[1]:                         ip = 192.168.0.10/24, gw = 192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             192.168.0.2


---

### Post by SeijiSensei on 2016-03-31
Any edits you make to resolv.conf will be overwritten the next time the machine boots.  You can add the two nameserver lines to /etc/resolvconf/resolv.conf.d/head which is used to create resolv.conf.

---

### Post by sgriesel on 2016-04-01
> **SeijiSensei said:**
> Any edits you make to resolv.conf will be overwritten the next time the machine boots.  You can add the two nameserver lines to /etc/resolvconf/resolv.conf.d/head which is used to create resolv.conf.

Thank you, but it is still not working :( This does not make sense, very strange. If I use the same cable on my other laptop (which is running Mint) then it works 100%. Is there no other way to reset all adapter settings to eliminate all possible causes?

---

