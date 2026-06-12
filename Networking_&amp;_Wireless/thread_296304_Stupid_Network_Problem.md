---
title: "Stupid Network Problem"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by tmahmood on 2006-11-09
Ok heres the situation
I am on Edgy updated from Dapper, connected through a LAN, I have give a user name and password to connect and use the Internet. The connection on my Linux system is configured using pppoeconf. Upto this evening it was working fine. Suddenly It just stopped working ](*,) 

It gets connected OK
when I ping google it pings OK

but I just can't browse!! Browsing works fine in Windows but not in Linux!! :confused: FF, Opera or Epiphany, nothing works 

I've already re-installed Ubuntu 6.06. but no it still not working :( 

help :(

---

### Post by Najand on 2006-11-09
Hmm, there is a command line web browser called w3m... Can you use it to see if it connects to the internet or not... 
```

*Example:*
w3m www.google.com

```
If it does not work, tell us and we will help you reconfigure your connection.

---

### Post by mips on 2006-11-09
Have a look into Disabling IPv6 and/or your DNS settings.

---

### Post by Najand on 2006-11-09
Well, in case it is a matter of updating your local DNS  servers, the 
```

bind

```
command may help. Disabling IPv6 will not change the situation, but will make 
your Internet connection a little bit faster.

---

### Post by tmahmood on 2006-11-10
> Hmm, there is a command line web browser called w3m... Can you use it to see if it connects to the internet or not... 

Nop it didn't work. I've tried Lynx also but it didn't work. I've also tried telnet to connect a server but it didn't work gives a temporary name resolution failure

---

### Post by stream303 on 2006-11-10
> **tmahmood said:**
> 
when I ping google it pings OK

but I just can't browse!!

Usually the ability to ping but not browse indicates a dns problem.  If you look at your **/etc/resolv.conf** file, is one of your isp's dns server addresses in it? You should be able to match it up to what address your windows install shows. If not, you may want to look at this howto:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Let's see if this helps!

---

### Post by tmahmood on 2006-11-10
Can't find any DNS address in windows...
Internet properties don't show it.. tried Advanced option too
System Information don't display it
nor ipconfig 

but if it is a problem with DNS, why it worked earlier? 

Can it be somehow my ISP is blocking me when I am connected using Linux? Is it possible?

---

### Post by emdeem on 2006-11-10
> **stream303 said:**
> Usually the ability to ping but not browse indicates a dns problem.
If you can ping google.com, then it's not a DNS problem.

Tell us more about your LAN.  Is there a router?  If so, why are you using PPPoE on the client machines?  Is there a firewall or proxy server running?

---

### Post by JayTheHun on 2006-11-10
> **tmahmood said:**
> Can't find any DNS address in windows...
Internet properties don't show it.. tried Advanced option too
System Information don't display it
nor ipconfig 

but if it is a problem with DNS, why it worked earlier? 

Can it be somehow my ISP is blocking me when I am connected using Linux? Is it possible?

Hi there.  On your working Windows box, click Start-Run, type in "cmd" (without the quotes), click OK.  At the command prompt that appears, type "ipconfig /all" (without the quotes again), hit Enter, then you'll see your DNS servers listed.

---

### Post by tmahmood on 2006-11-12
I am on a Shared Internet and I don't have any router. I have to be authorized to connected to the server. thats why I have to use PPPoE. I'm not sure how the system works. but all I've found out my Connection in Linux is done by a re-director rp-pppoe plug-in. Which let me authorize and connect to the dhcp server and updates my resolve.conf file.

Don't looks like a DNS problem to me either but here goes ipconfig /all s result

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : 
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : mshome.net

Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . : mshome.net
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.22
        DHCP Server . . . . . . . . . . . : 192.168.0.22
        DNS Servers . . . . . . . . . . . : 192.168.0.22
        Lease Obtained. . . . . . . . . . : Sunday, November 12, 2006 3:33:42 PM

        Lease Expires . . . . . . . . . . : Sunday, November 19, 2006 3:33:42 PM


PPP adapter linknet:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 172.16.102.76
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 172.16.102.76
        DNS Servers . . . . . . . . . . . : 69.88.14.4
                                            69.88.14.7
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

and here goes my resolve.conf
```
nameserver 69.88.14.4
nameserver 69.88.14.7

```

---

