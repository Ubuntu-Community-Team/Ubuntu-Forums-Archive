---
title: "Trying to make another IP to a client with Internal network in VirtualBox"
date: 2018-07-04
forum: Networking &amp; Wireless
---

### Post by harardin on 2018-07-04
Hi everyone I'am new to Ubuntu and linux. Trying to experiment with IP changing.

To do that I'am trying to use 2 Ubuntu systems in VirtualBox
 - 1-st is Ubuntu 16.04 32-bit used as Gate:
To do that I set active 2 network adapters in VirtualBox settings for this machine: 1) Simple NAT to get actual Internet from Host Machine and 2) InternalNetwork to with name "test" to send internet to a client machine
Also i edited network interfaces with command ```
sudo nano /etc/network/interfaces
``` and added a folowing lines to it: 

```
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
   address 192.168.0.1
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255
```

 - 2-nd is Ubuntu 16.04 32-bit used as Client:
With 1 active adapter only for InternalNetwork name of network is "test"
And I edited network interfaces in it too at the same pattern as in Gate machine ```
sudo nano /etc/network/interfaces
``` with the folowing lines:

```
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
   address 192.168.1.2
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255
```

And reboot network-manager on both machines with command ```
sudo service network-manager restart
```

Second thing was setting the "Wireless connection 2" in GateMachine as "Shared to another computer" because connection won't work without that.

Everything connected but, thing is the Client get's IP of HOST machine? The Idea was that Client gets some static IP from Gate Machine.

---

### Post by TheFu on 2018-07-04
hostnames should be all lowercase to avoid scripting issues by lazy programmers.  Yes, it shouldn't matter, but sometimes it does.

Having 2 NICs on the same subnet can lead to routing issues. What is the subnet for the DHCP provided stuff on both systems?

Don't use "network" or "broadcast" lines.  They lead to mistakes.  You only need 3 lines.  address, netmask and gateway.
If you carefully look at what you've posted above, either you will find a mistake or a typo.  There are definitely inconsistencies.

Virtualbox has some specific caveats around networking that behave in ways that aren't always obvious. The virtualbox manual [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html) has an entire chapter about it. For example, ports need to be over 1024/tcp to be forwarded inside a NAT'd VM.  UDP doesn't work reliably. 

Another example, NAT in 1 VM doesn't connect to NAT in any other VM when you put them on different subnets, as you've done above.

Disable the DHCP stuff, restart networking, then if you would please run a few commands and post the output?
```
ifconfig
route -n
```
Run on both systems.  Please post with "code tags", so things line up nicely in the forums.

---

### Post by whistl034 on 2018-07-07
I believe Network Manager, if enabled, may be conflicting, or possibly even completely ignoring, your /etc/network/interfaces settings.  I would recommend trying:

```

sudo apt-get install ifupdown
sudo apt-get remove network-manager
sudo ifdown eth1
sudo ifup eth1

```

That may work for you.

---

### Post by TheFu on 2018-07-08
ifupdown is a default install on 16.04 and earlier.
In 18.04, netplan.io became the default and has shown some growing pains/failures.

I think it was used before 18.04, but since I only run LTS releases, I'm not certain when it started.

---

### Post by harardin on 2018-07-10
> **TheFu said:**
> hostnames should be all lowercase to avoid scripting issues by lazy programmers.  Yes, it shouldn't matter, but sometimes it does.

Having 2 NICs on the same subnet can lead to routing issues. What is the subnet for the DHCP provided stuff on both systems?

Don't use "network" or "broadcast" lines.  They lead to mistakes.  You only need 3 lines.  address, netmask and gateway.
If you carefully look at what you've posted above, either you will find a mistake or a typo.  There are definitely inconsistencies.

Virtualbox has some specific caveats around networking that behave in ways that aren't always obvious. The virtualbox manual [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html) has an entire chapter about it. For example, ports need to be over 1024/tcp to be forwarded inside a NAT'd VM.  UDP doesn't work reliably. 

Another example, NAT in 1 VM doesn't connect to NAT in any other VM when you put them on different subnets, as you've done above.

Disable the DHCP stuff, restart networking, then if you would please run a few commands and post the output?
```
ifconfig
route -n
```
Run on both systems.  Please post with "code tags", so things line up nicely in the forums.

Thank you for your reply.

Here is input from ```
ifconfig
``` and from ```
route -n
```
Host UbuntuServer 16.04
[IMG]https://image.ibb.co/ixWZ98/Screenshot_2018_07_10_17_23_47.png[/IMG]
Client Ubuntu 16.04:
[IMG]https://image.ibb.co/hvr4bo/Client_Machine.png[/IMG]

I am actually trying to achieve an different IP for an internet connection on the client machine for anonymity and security, and for now testing it on VirtualBox, but it looks like it ignores my settings and just taking the main IP address with InnternalNetwork.

I also edited [IMG]https://ibb.co/nxiQGo[/IMG]```
/etc/network/interfaces
``` as you recommended.[IMG]https://ibb.co/nxiQGo[/IMG]
Here is the inside:
[IMG]https://image.ibb.co/gg6Rp8/Screenshot_2018_07_10_17_35_36.png[/IMG]

After setting the network I found out about **squid **and **privoxy **I used this guide for **privoxy: **[http://www.christianschenk.org/blog/enhancing-your-privacy-using-squid-and-privoxy/](http://www.christianschenk.org/blog/enhancing-your-privacy-using-squid-and-privoxy/)

And setup squid config as this:
[IMG]https://image.ibb.co/k0EkhT/squid_Conf_Setup.jpg[/IMG]

It looks like squid working properly but client machine ignores it.

---

