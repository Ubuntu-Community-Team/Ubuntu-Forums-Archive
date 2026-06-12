---
title: "How to make computer's ethernet interface static"
date: 2019-09-20
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2019-09-20
In thread [https://ubuntuforums.org/showthread.php?t=2426877](https://ubuntuforums.org/showthread.php?t=2426877) I was advised to set up a router with ddwrt firmware to get the priority I need for a voice over internet (VOIP) phone.  I am trying to follow the instructions at this website ([https://dd-wrt.com/support/router-database/](https://dd-wrt.com/support/router-database/)).  I clicked in the Router Database for Linksys wrt54g ver 6. and it brought up this page ([https://dd-wrt.com/support/router-database/?model=WRT54G_v6.0](https://dd-wrt.com/support/router-database/?model=WRT54G_v6.0)).  I selected DD-WRT Wiki: Linksys WRT54G v5.0/v5.1/v6.0 and got this page ([https://wiki.dd-wrt.com/wiki/index.php/Linksys_WRT54G_v5.0_&_5.1_&_6.0](https://wiki.dd-wrt.com/wiki/index.php/Linksys_WRT54G_v5.0_&_5.1_&_6.0)).  It said to set a static ip on my computer ethernet interface.  
I followed the directions in this site to set up a static interface: [https://www.howtoforge.com/debian-static-ip-address](https://www.howtoforge.com/debian-static-ip-address) .  First I executed ifconfig under terminal and got t he following:```
ralph@asp1:~$ ifconfig
enp4s0f1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a8:1e:84:42:9c:22  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1026  bytes 99261 (99.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1026  bytes 99261 (99.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 58:00:e3:9e:25:89  txqueuelen 1000  (Ethernet)
        RX packets 29863  bytes 32393636 (32.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20468  bytes 2341643 (2.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```
I then edited the file /etc/network/interfaces to contain: ```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# added by ralph
auto eth0
iface eth0 inet static
address 192.168.1.7
netmask 255.255.255.0

```
I then ran "sudo service network-manager restart" followed by ifconfig and got:```
enp4s0f1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a8:1e:84:42:9c:22  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2199  bytes 202890 (202.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2199  bytes 202890 (202.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.9  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::1d7a:fdc0:3489:1fd1  prefixlen 64  scopeid 0x20<link>
        ether 58:00:e3:9e:25:89  txqueuelen 1000  (Ethernet)
        RX packets 50786  bytes 54113370 (54.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 34694  bytes 4243428 (4.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```  As near as I can tell I changing /etc/network/interfaces did nothing.  
Can somebody tell me what I did wrong???

---

### Post by TheFu on 2019-09-20
The last 3 Ubuntu LTS releases each have different management techniques for networking. Follow the instructions specific to your release.  There is probably an "*Ubuntu Desktop Guide*" for the release with that information.  There is an *Ubuntu Server Guide* if you are running a non-desktop server install too.

And I didn't suggest DD-WRT as THE answer. I suggested QoS as the answer. Which router firmware you use or should use is completely up to you. Regardless, the firmware should be supported and maintained for the hardware you use.

---

### Post by lensman3 on 2019-09-26
Google "Ubuntu removing Networkmanger".   You will first have to stop and then disable the manager.  Then you can use another method that used "ifconfig" and the "ip" commands.

I would recommend you google "raspberry pi networking" to see how to setup a  computer without using networkmanager.

---

### Post by HermanAB on 2019-09-27
You want to know the easy way?
Leave your computer settings alone - it works - don't change anything.
Use your web browser to go to your router configuration page.
Find the MAC address of your computer.
Go to the DHCP server configuration and set the IP address for the MAC address
Save the settings and restart the router.
La voila.

---

### Post by &amp;KyT$0P# on 2019-09-27
Ralph L, why not just use NetworkManager to set the static IP?  That's how I do it on my local servers.

---

### Post by slickymaster on 2019-09-27
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2019-09-27
> **halogen2 said:**
> Ralph L, why not just use NetworkManager to set the static IP?  That's how I do it on my local servers.

Because NetworkManager isn't installed on servers?  I've never seen it.  Now, if you are running a desktop and calling it a server, sure, NetworkManager can be used.  I suppose someone could install nm-cli and do it that way on a server?  IDK.

---

### Post by &amp;KyT$0P# on 2019-09-27
> **TheFu said:**
> Because NetworkManager isn't installed on servers? 

Well, not by default.  I install it manually.

> I suppose someone could install nm-cli and do it that way on a server? IDK. 

I use [FONT=Courier New]nmtui[/FONT] for server.

---

