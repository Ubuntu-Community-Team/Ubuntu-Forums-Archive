---
title: "disable ipv6 on Ubuntu [16.10]?"
date: 2016-11-21
forum: Networking &amp; Wireless
---

### Post by sproid2 on 2016-11-21
How do I disable ipv6 on Ubuntu 16.10? It was working in 16.04. I have tried the same previous used method with no avail. Any google search or this forum search does not give a new method for Ubuntu  16.10. Any help appreciated.

---

### Post by Hadaka on 2016-11-22
Hi, you didnt state what you did before so I hope this isnt a repeat of what you tried.
*Open your editor or your editor of choice.
```
gksudo  /etc/sysctl.conf
```
*Copy and paste to the editor
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
*Save and close the editor
*Open a terminal and do...
```
sudo sysctl -p
```
*******************************************
```
***To disable IPv6 in Firefox***

1.    In the Location bar, type ***about:config ***and press enter

      * The about:config "This might void your warranty!" warning page may appear. ...
      * accept risk. 

2.    In the Search field, type ***network.dns.disableIPv6***

3.    In the list of preferences, double-click ***network.dns.disableIPv6*** to set its value to ***true***.
```

---

### Post by Doug S on 2016-11-22
In my /etc/default/grub file, I do this:```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```and then:```
sudo update-grub
```

---

### Post by sproid2 on 2016-11-23
Yeah, I follow that exact method and it did not worked plus the vpn was not connecting. I don't know if that somehow broke the openvpn service. I had to revert the process for the vpn service to connect. Another thing I notice is that on Windows 10 ( I have dual boot) also did not wanted to connect to internet thru wifi or Ethernet cable. So I don't know if that has something to do.

---

### Post by sproid2 on 2016-11-23
Thank you for the reply. I have dual boot with Windows 10 with UEFI on. Will messing with the GRUB potentially mess up booting up or anything?

---

### Post by Doug S on 2016-11-24
> **sproid2 said:**
> Thank you for the reply. I have dual boot with Windows 10 with UEFI on. Will messing with the GRUB potentially mess up booting up or anything?Oh, I don't know about UEFI.

---

### Post by sproid2 on 2017-01-14
So I waited after a couple of updates and tried again disabling ipv6 on Ubuntu 16.10. The good news is that this command cat /proc/sys/net/ipv6/conf/all/disable_ipv6  shows a 1, that means ipv6 is disable according to this tutorial ([http://www.upubuntu.com/2016/09/how-to-permanently-disable-ipv6.html](http://www.upubuntu.com/2016/09/how-to-permanently-disable-ipv6.html)). BUT Google chrome still gives my ipv6 address I can see on the Connection Information on the Network I am. I can see my ipv6 address with a google search of "my ip" and more detailed on this website [FONT=Roboto]en.internet.nl ). It shows:

[/FONT]
[LIST]
[*]the resolver can connect to a name server over IPv6
[*]an IPv6 connection (via DNS) was established successfully
[*]an IPv6 connection (directly to an address) was established successfully; 
your IP address is: ###long address...[I'm obfuscating it]
[*]your reverse domain name is: value not available
[*]your internet provider is: COMCAST- - Comcast Cable Communications, LLC
[*]the IPv6 privacy extensions are enabled (or you are not using SLAAC)
[*]an IPv4 connection (via DNS) was established successfully; 
your IP address is: ##.###.###.###
your reverse domain name is: value not available 
your internet provider is: NOBIS-TECH - Nobis Technology Group, LLC
[/LIST]
[COLOR=black]
I have disable ipv6 on Windows 10 too and it shows error on having ipv6 enabled.
Any help appreciated. :)[/COLOR]

---

