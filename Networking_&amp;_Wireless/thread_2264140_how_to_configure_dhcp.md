---
title: "how to configure dhcp"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by offir on 2015-02-05
I hope this is the right forum to the question

I have a laptop with ubuntu 10.04
and two network cards
One wired
One Wireless

the wireless card ip is 192.168.0.16


I want to use the wired card
As a dhcp server

And to distribute addresses from 10.10.10.1 to 10.10.10.254
I want the computers have access to the Internet
Through the wireless network card


how do i do that
i try Several Guides
like this
[http://community.spiceworks.com/how_to/337-creating-a-dhcp-server-using-ubuntu]("http://community.spiceworks.com/how_to/337-creating-a-dhcp-server-using-ubuntu")

```
sudo gedit /etc/dhcp3/dhcpd.conf 
```

default-lease-time 21600;
max-lease-time 43200;
option subnet-mask 255.255.255.0;
option broadcast-address 10.10.10.255;
option routers 10.10.10.245;
option domain-name-servers  208.67.222.222, 208.67.220.220;

subnet 10.10.10.0 netmask 255.255.255.0 {
range 10.10.10.1 10.10.10.100;
}

then
```
sudo /etc/init.d/networking restart
```

```
sudo /etc/init.d/dhcp3-server restart
```

all i get in the end is

```
* stoping DHCP server dhcp3  [fail]
* starting DHCP server dhcp3  [fail]
* check system for diagnostics
```


where can i find diagnostics ?

and how do i make it work
Obviously I'm doing something wrong
But what ?

---

### Post by SeijiSensei on 2015-02-05
Look at /var/log/syslog.

You also need to add the line
```
INTERFACES="eth1"
```
to /etc/default/isc-dhcp-server so the server will listen on that interface.

---

### Post by Lars Noodén on 2015-02-05
Which version [s]of Ubuntu are you using[/s] and which DHCP server?

If you are using the [ISC DHCP server](http://manpages.ubuntu.com/manpages/trusty/en/man8/dhcpd.8.html) on 14.04 LTS then you can try launching dhcpd manually with the log messages sent to stderr instead.  

```

sudo dhcpd -d

```

That will put any error  messages on the screen instead of in the log.  

Otherwise you can check /var/log/syslog for the error messages, which is where they normally end up.


My guess is that you are missing a static address on the interface you want to serve DHCP from.  For dhcpd to work over the wired card, you'll need to have a static ip address assigned to the wired card, such as 10.10.10.1  That will leave only 10.10.10.2 to 10.10.10.254 as the range available to be served up with DHCP.

---

### Post by kpatz on 2015-02-05
It sounds to me like you want to use your laptop as a router, giving internet access via the wireless adapter to other computers connecting to the wireless?  Or are you giving wired computers access to an internet connection the laptop is getting via the wireless connection?

So, which way is it?  

Internet->wireless router->wireless laptop adapter->laptop as router->wired adapter->switch->wired clients?

Or...

Internet->router or modem->wired laptop adapter->laptop as router->wireless adapter->wireless clients?

In either case, the adapter connected to the internet would typically get an address via DHCP from the internet router or modem (unless you're using a connection with a static IP), and the other adapter would be assigned a static IP and the DHCP server would hand out addresses on that network.  Then you would use iptables NAT forwarding to route packets from the network to the internet and back.

---

### Post by offir on 2015-02-05
> Look at /var/log/syslog.

You also need to add the line
```
INTERFACES="eth1"
```

to /etc/default/isc-dhcp-server so the server will listen on that interface.  


where do i Write this ?



to Lars Noodén
i use ubuntu 10.04
I worked According to the manual
And put a fixed ip at first

But for some reason it is not saved
I checked with ifconfig
the wired network card
Has no ip







> kpatz

    Re: how to configure dhcp
    It sounds to me like you want to use your laptop as a router, giving internet access via the wireless adapter to other computers connecting to the wireless? Or are you giving wired computers access to an internet connection the laptop is getting via the wireless connection?

    So, which way is it?

    Internet->wireless router->wireless laptop adapter->laptop as router->wired adapter->switch->wired clients?

    Or...

    Internet->router or modem->wired laptop adapter->laptop as router->wireless adapter->wireless clients?

    In either case, the adapter connected to the internet would typically get an address via DHCP from the internet router or modem (unless you're using a connection with a static IP), and the other adapter would be assigned a static IP and the DHCP server would hand out addresses on that network. Then you would use iptables NAT forwarding to route packets from the network to the internet and back. 



I want to use the computer as a router
I want to connect a switch to the wired network card
And connect computers to the switch

And wireless card connects to cell phone
And went to the Internet

---

### Post by SeijiSensei on 2015-02-05
As I said, it goes in the file /etc/default/isc-dhcp-server.

---

### Post by offir on 2015-02-05
i use this command for static  ip
```
sudo gedit /etc/network/interfaces 
```

and i wirte this

```
iface eth0 inet static
address 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
```

but steel
the wired card has no ip address

I was able to give the card
Permanent address

The guide I used was not right
There was missing a line


I had to add this line
```
auto eth0
```
to here
```
iface eth0 inet static
address 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
```

Now it's like that

```
auto eth0
iface eth0 inet static
address 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
```

and it works


> Then you would use iptables NAT forwarding to route packets from the network to the internet and back. 

now i have A different problem 

How do I point the information coming from the the wired card
So he should go to the wireless card

i install iptables 
But I do not know how to use it

---

### Post by Lars Noodén on 2015-02-06
It would probably be something like this, but where in place of eth4 you have your own external interface:

```

iptables -t nat -A POSTROUTING -o eth4 -j MASQUERADE

```

It would be a good idea to look up forwarding/masquerading to get an idea what's going on.  Then you'll need to set the kernel so that it allows forwarding (masquerading).  Then you'll also need to make the changes so that they persist even after a reboot.

```

net.ipv4.ip_forward=1

```

That can be done with [sysctl](http://manpages.ubuntu.com/manpages/lucid/en/man8/sysctl.8.html) to have effect now and can be put in [/etc/sysctl.conf](http://manpages.ubuntu.com/manpages/lucid/en/man5/sysctl.conf.5.html) to persist across reboots.

---

### Post by offir on 2015-02-06
i use this guide
[http://www.revsys.com/writings/quicktips/nat.html]("http://www.revsys.com/writings/quicktips/nat.html")

and it dos not work

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

```
/sbin/iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

```
/sbin/iptables -A FORWARD -i wlan0 -o eth0 -m state
   --state RELATED,ESTABLISHED -j ACC
```

```
/sbin/iptables -A FORWARD -i eth0 -o wlan0 -j ACCEPT
```





```
sudo gedit /etc/sysctl.conf
```
net.ipv4.ip_forward = 0 
was already 
net.ipv4.ip_forward = 1



still no ping from the network on eth0 to wlan0


when type this command
```
sudo /etc/init.d/networking restart
```

i get this 
```
 * Reconfiguring network interfaces...                                                    Ignoring unknown interface wlan0=wlan0
```

i assume that something is not right 
but what

How to connect the two network card

I assume that this is part of the problem (or all of it)
```
 * Reconfiguring network interfaces...                                                    Ignoring unknown interface wlan0=wlan0
```

i get this after i type this
```
sudo /etc/init.d/networking restart
```

---

### Post by Bucky Ball on 2015-02-07
Slightly off-topic, but so far, not mentioned. Unless you are using 10.04 LTS server, 10.04 is no longer supported. Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730") if you are using the desktop version. Good luck. ;)

---

### Post by offir on 2015-02-07
i use desktop version 
it is an old computer witg 8 giga hdd
acer model acer aspire one AOA110L
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834115496]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834115496")

---

### Post by Bucky Ball on 2015-02-07
Well, 10.04 LTS desktop is unsupported. Would be wise to upgrade to 12.04 LTS or 14.04 LTS, both with five years support (2017 and 2019 respectively), if that machine is online.

---

### Post by Lars Noodén on 2015-02-07
So if you connect a machine to eth0, does it get an IP address via DHCP?  If so, can you ping the address you assigned manually to eth0?

---

### Post by offir on 2015-02-07
i get an ip from the dhcp
10.10.10.3 
but i cant ping to 10.10.10.10

i get request timed out


does the gateway of eth0 Should be the ip of wlan0 ?

how do i fix this ?

```
* Reconfiguring network interfaces...                                                    Ignoring unknown interface wlan0=wlan0
```

Maybe This causes the problem





[COLOR="#FF0000"][SIZE=5]update[/SIZE][/COLOR]

now there is a ping from 10.10.10.3 to 10.10.10.10

[COLOR="#0000CD"]Is there a way or command
Clear all settings
And start over[/COLOR] ????


I will try again

---

### Post by Lars Noodén on 2015-02-07
I don't have any concrete answers at the moment but just some comments.   About the DHCP server's interface, the IP number should be outside the range being served by DHCP.  So if you are serving addresses 10.10.10.2 to 10.10.10.254 then your only choice for IP address would be 10.10.10.1 for that interface.  Then a second point is that in dhcpd.conf, the gateway should be the IP of the interface which is serving DHCP.  Then a possible third item might be that your choice of DNS servers was copied directly from the tutorial and you should instead use the ones appropriate to your ISP.

---

### Post by offir on 2015-02-07
I changed the ip
According to what you said

this is /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.10.1
netmask 255.255.255.0
gateway 10.10.10.1

auto wlan0
iface wlan0 inet static
address 192.168.0.16
netmask 255.255.255.0
gateway 192.168.0.1
```



this is /etc/dhcp3/dhcpd.conf

```
default-lease-time 21600;
max-lease-time 43200;
option subnet-mask 255.255.255.0;
option broadcast-address 10.10.10.255;
option routers 10.10.10.1;
option domain-name-servers 10.10.10.1;

subnet 10.10.10.0 netmask 255.255.255.0 {
range 10.10.10.2 10.10.10.100;
}
```



and this is the cards ip 

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a4:84:fd  
          inet addr:10.10.10.1  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea4:84fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2518856 (2.5 MB)  TX bytes:289736 (289.7 KB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:338103 (338.1 KB)  TX bytes:338103 (338.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e2:91:40:16  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe91:4016/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23730022 (23.7 MB)  TX bytes:2990102 (2.9 MB)

```

the wlan0 is wan
eth0 is lan

---

### Post by Lars Noodén on 2015-02-07
ok.  From the machine(s) connected to eth0's interface and getting an address via DHCP, can you do any of the following?

ping 10.10.10.1
ping 192.168.0.16
ping 8.8.8.8
ping [www.google.com](www.google.com)

---

### Post by offir on 2015-02-07
yes
yes
no
no

---

### Post by Bucky Ball on 2015-02-07
That points to perhaps the DNS settings on the router or the machines as you can see the LAN but not the WAN (you can access your own network but you can't get out). As was previously mentioned, do you have the correct DNS numbers?

---

### Post by Lars Noodén on 2015-02-07
Can you see if that changes to 

yes 
no
no
no

if you temporarily set *net.ipv4.ip_forward=0* temporarily?  That would tell if forwarding is working.

---

### Post by offir on 2015-02-07
i just  type
```
sudo gedit  /etc/resolv.conf:
```

nameserver 208.67.222.222
nameserver 208.67.220.220


it is free dns servers

> **Lars Noodén said:**
> Can you see if that changes to 

yes 
no
no
no

if you temporarily set *net.ipv4.ip_forward=0* temporarily?  That would tell if forwarding is working.

steel the same
yes
yes
no
no

Maybe it will tell you something

```
sudo gedit /etc/sysctl.conf
```




```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1
#[COLOR="#FF0000"]net.ipv4.conf.default.forwarding=1[/COLOR]
#[COLOR="#FF0000"]net.ipv4.conf.all.forwarding=1[/COLOR]


# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
```



the two red line i add According a Guide I saw Online

when you told me to try pinging with this line net.ipv4.ip_forward=1 is net.ipv4.ip_forward=[COLOR="#FF0000"]0[/COLOR]
i remove the two lines i add and change the one line to 0

---

### Post by Lars Noodén on 2015-02-07
You need to uncomment the lines in the file for them to take effect on next reboot:

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

For right now try in the shell instead this:

```

sudo sysctl net.ipv4.ip_forward=1

```

And then check the status

```

sysctl net.ipv4.ip_forward

```

---

### Post by offir on 2015-02-07
You are a genius
It worked

What was the problem ?
Why it did not work before ?

What does that mean
> You need to uncomment the lines in the file for them to take effect on next reboot:

what i need to do ?
Paste this in terminal as sudo

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
```

---

### Post by Bucky Ball on 2015-02-07
Make this line:
```

#net.ipv4.ip_forward=1

```
Look like this:
```

net.ipv4.ip_forward=1
```

;)

---

### Post by Lars Noodén on 2015-02-07
The background is this: The kernel needs to be told whether to forward packets.  The default is not to forward, so it has to be explictly told to do so.  You can use [sysctl](http://manpages.ubuntu.com/manpages/trusty/en/man8/sysctl.8.html) with sudo, like you did above, to do that manually.  But if you go that route you have to do it after each boot before forwarding will turn on.  Fortunately, there is a configuration file, [sysctl.conf](http://manpages.ubuntu.com/manpages/trusty/en/man5/sysctl.conf.5.html) which gets read during the system start up and can set kernel parameters, such as forwarding.  These configuration files have lines that don't produce any results, they are just there for humans to read and usually contain comments and annotations.  Those lines are identified by starting with a pound sign (#) and anything on that line is ignored by the computer.  So if you remove the pound sign, the lines become active.  So edit the file /etc/sysctl.conf with the lines Bucky Ball points to.  You can use gedit for that if you like or you can take it a step further and use [nano](http://manpages.ubuntu.com/manpages/trusty/en/man1/nano.1.html) to make your changes.

```

sudo nano /etc/sysctl.conf

```

Nano is as easy to use and almost as familiar as gedit but the big advantage is that you can also run it over SSH and make your changes remotely, maybe some day saving a trip.

---

### Post by offir on 2015-02-07
now if i restart all will be saved ?


Thank you both for the help the explanations
And patience

---

### Post by Lars Noodén on 2015-02-07
No worries.  

If you have made the changes in /etc/sysctl.conf, the changes will persist even after a restart.

Try a reboot to make sure.

---

### Post by offir on 2015-02-07
stop working after restart
i did not change any thing

---

### Post by Lars Noodén on 2015-02-07
What is the status of forwarding?

```

sysctl net.ipv4.ip_forward

```

What is the status of dhcpd?

```

service isc-dhcp-server status

```

What is the ip address of the LAN interface?

```

ifconfig

```

One or more of them weren't set in a permanent way.

---

### Post by offir on 2015-02-07
```
sysctl net.ipv4.ip_forward
```
give
```
net.ipv4.ip_forward = 1
```



```
service isc-dhcp-server status
```
give
```
isc-dhcp-server: unrecognized service
```





```
ifconfig
```
give
```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a4:84:fd  
          inet addr:10.10.10.1  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea4:84fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76848 (76.8 KB)  TX bytes:60550 (60.5 KB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8046 (8.0 KB)  TX bytes:8046 (8.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e2:91:40:16  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Lars Noodén on 2015-02-07
> **offir said:**
> ```
isc-dhcp-server: unrecognized service
```

It looks like dhcpd is not running.  Which package did you install to get DHCP?  Usually it is [isc-dhcp-server](https://www.diffchecker.com/qp9xyh7b) but perhaps you have tried some other way?

---

### Post by offir on 2015-02-07
i use this command
```
sudo apt-get install dhcp3-server
```

if i use this command Again
It will fix it
Or do another problem ?

---

### Post by Lars Noodén on 2015-02-07
I forgot you are still on 10.04.  As mentioned it is only around in server form these days, so it is important to upgrade when you get a chance.  The non-server components are not getting updates, not even security updates. If you go to 14.04 LTS it will be good until 2019

Do you have a file S40dhcp3-server in the directory /etc/rc2.d?  
If you run dhcpd3-server manually in debug mode does it give any errors?

```

sudo /usr/sbin/dhcpd3 -d

```

---

### Post by offir on 2015-02-07
> Do you have a file S40dhcp3-server in the directory /etc/rc2.d? 
yes there is



> If you run dhcpd3-server manually in debug mode does it give any errors?
```
/usr/sbin/dhcpd3 -d
```

```
bash: /usr/sbin/dhcp3: no such file or dirrectory
```

---

### Post by Lars Noodén on 2015-02-07
There should be a "d" in there

sudo /usr/sbin/dhcp**d**3 -d

Most server names end with a "d" for daemon, to indicate that it is a process that waits in the background.  You'll see "sshd" and "httpd" and many other similar names.  And here you'll see [dhcpd3](http://manpages.ubuntu.com/manpages/lucid/en/man8/dhcpd3.8.html) and with the -d option above, it stays in the foreground instead of switching to the background and sends any erros to the screen instead of to the logs.

---

### Post by offir on 2015-02-07
sorry about the delay
you are right 
> There should be a "d" in there



here is the output

```
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 3 leases to leases file.
Listening on LPF/eth0/00:1e:68:a4:84:fd/10.10.10/24
Sending on   LPF/eth0/00:1e:68:a4:84:fd/10.10.10/24
Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER from 00:1e:68:a4:84:fd via eth0
icmp_echorequest 10.10.10.2: Network is unreachable
DHCPOFFER on 10.10.10.2 to 00:1e:68:a4:84:fd via eth0
DHCPREQUEST for 10.10.10.2 (10.10.10.1) from 00:1e:68:a4:84:fd via eth0
DHCPACK on 10.10.10.2 to 00:1e:68:a4:84:fd via eth0
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER from 00:1e:68:a4:84:fd via eth0
icmp_echorequest 10.10.10.2: Network is unreachable
DHCPOFFER on 10.10.10.2 to 00:1e:68:a4:84:fd via eth0
DHCPREQUEST for 10.10.10.2 (10.10.10.2) from 00:1e:68:a4:84:fd via eth0
DHCPACK on 10.10.10.2 to 00:1e:68:a4:84:fd via eth0
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER from 00:1e:68:a4:84:fd via eth0
icmp_echorequest 10.10.10.2: Network is unreachable
DHCPOFFER on 10.10.10.2 to 00:1e:68:a4:84:fd via eth0
DHCPREQUEST for 10.10.10.2 (10.10.10.2) from 00:1e:68:a4:84:fd via eth0
DHCPACK on 10.10.10.2 to 00:1e:68:a4:84:fd via eth0
```

There is another thing I want to add
Might help

I have on the computer
Two network card management software
The first came with built in Ubuntu
the second I installed through software manager (wicd network manger)


The first was gone after the first boot (restart)

---

### Post by Lars Noodén on 2015-02-08
dhcpd looks like it is probably configured ok.  Can you note the time, do a fresh restart and then scroll down to that section in /var/log/syslog?

```

less /var/log/syslog

```

You can use the slash (/) to search.  When you get down to about the right time and date, then start looking for what lines containing "dhcpd:" in the  5th column say.  They will tell you what specific problems the daemon is running into during system startup.

---

### Post by offir on 2015-02-08
Hope you meant that
I turned on the computer at 13:55
And here is the log




```
Feb  8 13:54:45 zion-ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb  8 13:54:45 zion-ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="619" x-info="http://www.rsyslog.com"] (re)start
Feb  8 13:54:45 zion-ubuntu rsyslogd: rsyslogd's groupid changed to 103
Feb  8 13:54:45 zion-ubuntu rsyslogd: rsyslogd's userid changed to 101
Feb  8 13:54:45 zion-ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Linux version 2.6.32-72-generic (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #139-Ubuntu SMP Wed Jan 14 21:19:14 UTC 2015 (Ubuntu 2.6.32-72.139-generic 2.6.32.63+drm33.26)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] KERNEL supported cpus:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Intel GenuineIntel
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   NSC Geode by NSC
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f376000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f376000 - 000000001f3bf000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f3bf000 - 000000001f46d000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f46d000 - 000000001f4bf000 (ACPI NVS)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f4bf000 - 000000001f4f0000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f4f0000 - 000000001f4ff000 (ACPI data)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f4ff000 - 000000001f500000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001f500000 - 0000000020000000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] DMI 2.4 present.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] last_pfn = 0x1f500 max_arch_pfn = 0x100000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] MTRR default type: uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   C8000-EFFFF uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   0 base 0FFFE0000 mask 0FFFE0000 write-protect
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   2 base 000000000 mask 0F0000000 write-back
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   3 base 010000000 mask 0F0000000 write-back
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   4 base 01F800000 mask 0FF800000 uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   5 base 01F600000 mask 0FFE00000 uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   6 base 01F500000 mask 0FFF00000 uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] modified physical RAM map:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000001f376000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f376000 - 000000001f3bf000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f3bf000 - 000000001f46d000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f46d000 - 000000001f4bf000 (ACPI NVS)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f4bf000 - 000000001f4f0000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f4f0000 - 000000001f4ff000 (ACPI data)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f4ff000 - 000000001f500000 (usable)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 000000001f500000 - 0000000020000000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f500000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]  0000000000 - 001f500000 page 4k
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] kernel direct mapping tables up to 1f500000 @ 7000-88000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] RAMDISK: 16f32000 - 176d7ff6
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 INTEL )
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: XSDT 1f4fe120 00064 (v01 INTEL  Napa     00000001      01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: FACP 1f4fc000 000F4 (v04 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: DSDT 1f4f2000 05D05 (v01 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: FACS 1f488000 00040
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: SSDT 1f4fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: HPET 1f4fb000 00038 (v01 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: APIC 1f4fa000 00068 (v02 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: MCFG 1f4f9000 0003C (v01 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: ASF! 1f4f8000 000A5 (v32 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: SLIC 1f4f1000 00180 (v01 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: BOOT 1f4f0000 00028 (v01 INTEL  Napa     00000001 MSFT 01000013)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] 501MB LOWMEM available.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   mapped low ram: 0 - 1f500000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   low ram: 0 - 1f500000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 1f500000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   node 0 bootmap 00082000 - 00085ea0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f500000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008e7ef8]    TEXT DATA BSS ==> [0000100000 - 00008e7ef8]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #4 [0016f32000 - 00176d7ff6]          RAMDISK ==> [0016f32000 - 00176d7ff6]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #6 [00008e8000 - 00008eb254]              BRK ==> [00008e8000 - 00008eb254]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #7 [0000007000 - 0000082000]          PGTABLE ==> [0000007000 - 0000082000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   #8 [0000082000 - 0000086000]          BOOTMAP ==> [0000082000 - 0000086000]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Zone PFN ranges:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f500
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   HighMem  0x0001f500 -> 0x0001f500
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] early_node_map[6] active PFN ranges
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0001f376
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     0: 0x0001f3bf -> 0x0001f46d
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     0: 0x0001f4bf -> 0x0001f4f0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     0: 0x0001f4ff -> 0x0001f500
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] On node 0 totalpages: 127985
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c07a2800, node_mem_map c1001000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Normal zone: 970 pages used for memmap
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]   Normal zone: 123020 pages, LIFO batch:31
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Using APIC driver default
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000001f376000 - 000000001f3bf000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000001f46d000 - 000000001f4bf000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000001f4f0000 - 000000001f4ff000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c13f6000 s36056 r0 d21288 u65536
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u65536 alloc=16*4096
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 126983
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-72-generic root=UUID=b19a1f19-8140-440c-aa3a-2b6efbfde813 ro quiet splash
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Initializing CPU#0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] allocated 2565120 bytes of page_cgroup
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Memory: 487988k/513024k available (4707k kernel code, 23532k reserved, 2128k data, 664k init, 0k highmem)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] virtual kernel memory layout:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     vmalloc : 0xdfd00000 - 0xff7fe000   ( 506 MB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf500000   ( 501 MB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]       .init : 0xc07ad000 - 0xc0853000   ( 664 kB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]       .data : 0xc0598cb7 - 0xc07acdc8   (2128 kB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0598cb7   (4707 kB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] console [tty0] enabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] hpet clockevent registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Feb  8 13:54:45 zion-ubuntu kernel: [    0.000000] Detected 1595.946 MHz processor.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.89 BogoMIPS (lpj=6383784)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004042] Security Framework initialized
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004080] AppArmor: AppArmor initialized
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004096] Mount-cache hash table entries: 512
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004326] Initializing cgroup subsys ns
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004335] Initializing cgroup subsys cpuacct
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004345] Initializing cgroup subsys memory
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004359] Initializing cgroup subsys devices
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004365] Initializing cgroup subsys freezer
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004371] Initializing cgroup subsys net_cls
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004406] Atom PSE erratum detected, BIOS microcode update recommended
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004415] CPU: L1 I cache: 32K, L1 D cache: 24K
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004422] CPU: L2 cache: 512K
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004428] CPU: Physical Processor ID: 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004432] CPU: Processor Core ID: 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004440] mce: CPU supports 5 MCE banks
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004457] CPU0: Thermal monitoring enabled (TM1)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004465] using mwait in idle threads.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004476] Performance Events: Atom events, Intel PMU driver.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004492] ... version:                3
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004497] ... bit width:              40
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004502] ... generic registers:      2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004507] ... value mask:             000000ffffffffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004512] ... max period:             000000007fffffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004517] ... fixed-purpose events:   3
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004522] ... event mask:             0000000700000003
Feb  8 13:54:45 zion-ubuntu kernel: [    0.004531] Checking 'hlt' instruction... OK.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.020010] Disabling 4MB page tables to avoid TLB bug
Feb  8 13:54:45 zion-ubuntu kernel: [    0.024450] ACPI: Core revision 20090903
Feb  8 13:54:45 zion-ubuntu kernel: [    0.040033] ftrace: converting mcount calls to 0f 1f 44 00 00
Feb  8 13:54:45 zion-ubuntu kernel: [    0.040046] ftrace: allocating 21854 entries in 43 pages
Feb  8 13:54:45 zion-ubuntu kernel: [    0.044242] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  8 13:54:45 zion-ubuntu kernel: [    0.044650] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.087201] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Feb  8 13:54:45 zion-ubuntu kernel: [    0.088005] Booting processor 1 APIC 0x1 ip 0x6000
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] Initializing CPU#1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] CPU: L2 cache: 512K
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] CPU: Physical Processor ID: 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] CPU: Processor Core ID: 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.008000] CPU1: Thermal monitoring enabled (TM1)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.172077] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Feb  8 13:54:45 zion-ubuntu kernel: [    0.172095] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176055] Brought up 2 CPUs
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176063] Total of 2 processors activated (6383.83 BogoMIPS).
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176524] CPU0 attaching sched-domain:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176533]  domain 0: span 0-1 level SIBLING
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176539]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176552]   domain 1: span 0-1 level MC
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176557]    groups: 0-1 (cpu_power = 1178)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176569] CPU1 attaching sched-domain:
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176574]  domain 0: span 0-1 level SIBLING
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176579]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176590]   domain 1: span 0-1 level MC
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176595]    groups: 0-1 (cpu_power = 1178)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] devtmpfs: initialized
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] regulator: core version 0.5
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] Time: 11:54:37  Date: 02/08/15
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] NET: Registered protocol family 16
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] Trying to unpack rootfs image as initramfs...
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] EISA bus registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176777] ACPI: bus type pci registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176848] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176858] PCI: MCFG area at e0000000 reserved in E820
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176864] PCI: Using MMCONFIG for extended config space
Feb  8 13:54:45 zion-ubuntu kernel: [    0.176871] PCI: Using configuration type 1 for base access
Feb  8 13:54:45 zion-ubuntu kernel: [    0.182488] bio: create slab <bio-0> at 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.185028] ACPI: EC: Look up EC in DSDT
Feb  8 13:54:45 zion-ubuntu kernel: [    0.189337] ACPI: Executed 1 blocks of module-level executable AML code
Feb  8 13:54:45 zion-ubuntu kernel: [    0.193781] ACPI: BIOS _OSI(Linux) query ignored
Feb  8 13:54:45 zion-ubuntu kernel: [    0.194268] ACPI: BIOS _OSI(Linux) query ignored
Feb  8 13:54:45 zion-ubuntu kernel: [    0.200190] ACPI: Interpreter enabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.200204] ACPI: (supports S0 S3 S4 S5)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.200283] ACPI: Using IOAPIC for interrupt routing
Feb  8 13:54:45 zion-ubuntu kernel: [    0.214128] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Feb  8 13:54:45 zion-ubuntu kernel: [    0.214873] ACPI: No dock devices found.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.216661] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.216682] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.216705] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Feb  8 13:54:45 zion-ubuntu kernel: [    0.216773] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.216994] pci 0000:00:02.0: reg 10 32bit mmio: [0x38480000-0x384fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217008] pci 0000:00:02.0: reg 14 io port: [0x60c0-0x60c7]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217020] pci 0000:00:02.0: reg 18 32bit mmio pref: [0x20000000-0x2fffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217033] pci 0000:00:02.0: reg 1c 32bit mmio: [0x38500000-0x3853ffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217111] pci 0000:00:02.1: reg 10 32bit mmio: [0x38400000-0x3847ffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217291] pci 0000:00:1b.0: reg 10 64bit mmio: [0x38540000-0x38543fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217402] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217413] pci 0000:00:1b.0: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217572] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217583] pci 0000:00:1c.0: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217743] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217754] pci 0000:00:1c.1: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217914] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.217925] pci 0000:00:1c.2: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218092] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218103] pci 0000:00:1c.3: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218199] pci 0000:00:1d.0: reg 20 io port: [0x6080-0x609f]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218295] pci 0000:00:1d.1: reg 20 io port: [0x6060-0x607f]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218390] pci 0000:00:1d.2: reg 20 io port: [0x6040-0x605f]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218485] pci 0000:00:1d.3: reg 20 io port: [0x6020-0x603f]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218586] pci 0000:00:1d.7: reg 10 32bit mmio: [0x38544400-0x385447ff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218690] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218702] pci 0000:00:1d.7: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.218972] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219085] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219101] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219116] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219131] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219146] pci 0000:00:1f.2: reg 20 io port: [0x60a0-0x60af]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219211] pci 0000:00:1f.2: PME# supported from D3hot
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219222] pci 0000:00:1f.2: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219306] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219441] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219453] pci 0000:00:1c.0: bridge 32bit mmio: [0x37300000-0x383fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219469] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x30000000-0x30ffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219558] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219598] pci 0000:02:00.0: reg 18 64bit mmio pref: [0x31010000-0x31010fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219630] pci 0000:02:00.0: reg 20 64bit mmio pref: [0x31000000-0x3100ffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219649] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfffe0000-0xffffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219763] pci 0000:02:00.0: supports D1 D2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219771] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219783] pci 0000:02:00.0: PME# disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219896] pci 0000:00:1c.1: bridge io port: [0x3000-0x4fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219907] pci 0000:00:1c.1: bridge 32bit mmio: [0x36300000-0x372fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.219923] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x31000000-0x320fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220057] pci 0000:03:00.0: reg 10 64bit mmio: [0x35200000-0x3520ffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220313] pci 0000:00:1c.2: bridge io port: [0x2000-0x2fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220325] pci 0000:00:1c.2: bridge 32bit mmio: [0x35200000-0x362fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220341] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x32100000-0x330fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220432] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220445] pci 0000:00:1c.3: bridge 32bit mmio: [0x34100000-0x351fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220463] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x33100000-0x340fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220555] pci 0000:00:1e.0: transparent bridge
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220616] pci_bus 0000:00: on NUMA node 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.220637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.221137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.221555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.221851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.222092] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.222335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.222912] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.222934] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.235502] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.235827] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.236175] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.236499] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.236818] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.237135] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.237453] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.237767] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.238149] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Feb  8 13:54:45 zion-ubuntu kernel: [    0.238184] vgaarb: loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    0.238560] SCSI subsystem initialized
Feb  8 13:54:45 zion-ubuntu kernel: [    0.238828] libata version 3.00 loaded.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.239112] usbcore: registered new interface driver usbfs
Feb  8 13:54:45 zion-ubuntu kernel: [    0.239158] usbcore: registered new interface driver hub
Feb  8 13:54:45 zion-ubuntu kernel: [    0.239260] usbcore: registered new device driver usb
Feb  8 13:54:45 zion-ubuntu kernel: [    0.239935] ACPI: WMI: Mapper loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    0.239944] PCI: Using ACPI for IRQ routing
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240430] NetLabel: Initializing
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240439] NetLabel:  domain hash size = 128
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240444] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240477] NetLabel:  unlabeled traffic allowed by default
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240590] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240605] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.240621] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Feb  8 13:54:45 zion-ubuntu kernel: [    0.244406] Switching to clocksource tsc
Feb  8 13:54:45 zion-ubuntu kernel: [    0.249131] AppArmor: AppArmor Filesystem Enabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.249176] pnp: PnP ACPI init
Feb  8 13:54:45 zion-ubuntu kernel: [    0.249219] ACPI: bus type pnp registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.251921] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 13 (0x1000-0x1fff), disabling
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253658] pnp: PnP ACPI: found 9 devices
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253666] ACPI: ACPI bus type pnp unregistered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253676] PnPBIOS: Disabled by ACPI PNP
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253711] system 00:01: ioport range 0x200-0x20f has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253724] system 00:01: ioport range 0x600-0x60f has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253734] system 00:01: ioport range 0x610-0x610 has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253743] system 00:01: ioport range 0x800-0x80f has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253753] system 00:01: ioport range 0x400-0x47f has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253763] system 00:01: ioport range 0x500-0x53f has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253777] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253787] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253798] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253809] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253821] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253834] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.253846] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289028] pci 0000:02:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289119] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289129] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289143] pci 0000:00:1c.0:   MEM window: 0x37300000-0x383fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289155] pci 0000:00:1c.0:   PREFETCH window: 0x00000030000000-0x00000030ffffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289176] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289185] pci 0000:00:1c.1:   IO window: 0x3000-0x4fff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289198] pci 0000:00:1c.1:   MEM window: 0x36300000-0x372fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289209] pci 0000:00:1c.1:   PREFETCH window: 0x00000031000000-0x000000320fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289225] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289235] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289248] pci 0000:00:1c.2:   MEM window: 0x35200000-0x362fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289259] pci 0000:00:1c.2:   PREFETCH window: 0x00000032100000-0x000000330fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289275] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289284] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289297] pci 0000:00:1c.3:   MEM window: 0x34100000-0x351fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289308] pci 0000:00:1c.3:   PREFETCH window: 0x00000033100000-0x000000340fffff
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289324] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289330] pci 0000:00:1e.0:   IO window: disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289341] pci 0000:00:1e.0:   MEM window: disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289351] pci 0000:00:1e.0:   PREFETCH window: disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289392]   alloc irq_desc for 16 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289399]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289417] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289431] pci 0000:00:1c.0: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289453]   alloc irq_desc for 17 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289459]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289485] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289498] pci 0000:00:1c.1: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289522]   alloc irq_desc for 18 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289529]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289541] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289556] pci 0000:00:1c.2: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289579]   alloc irq_desc for 19 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289584]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289597] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289611] pci 0000:00:1c.3: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289631] pci 0000:00:1e.0: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289645] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289654] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289663] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289672] pci_bus 0000:01: resource 1 mem: [0x37300000-0x383fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289683] pci_bus 0000:01: resource 2 pref mem [0x30000000-0x30ffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289692] pci_bus 0000:02: resource 0 io:  [0x3000-0x4fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289700] pci_bus 0000:02: resource 1 mem: [0x36300000-0x372fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289709] pci_bus 0000:02: resource 2 pref mem [0x31000000-0x320fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289718] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289726] pci_bus 0000:03: resource 1 mem: [0x35200000-0x362fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289735] pci_bus 0000:03: resource 2 pref mem [0x32100000-0x330fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289743] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289752] pci_bus 0000:04: resource 1 mem: [0x34100000-0x351fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289760] pci_bus 0000:04: resource 2 pref mem [0x33100000-0x340fffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289769] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289778] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.289881] NET: Registered protocol family 2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.290161] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291057] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291221] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291370] TCP: Hash tables configured (established 16384 bind 16384)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291377] TCP reno registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291620] NET: Registered protocol family 1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291676] pci 0000:00:02.0: Boot video device
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291726] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291756] pci 0000:00:1d.0: PCI INT A disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291775] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291803] pci 0000:00:1d.1: PCI INT B disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291821] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291850] pci 0000:00:1d.2: PCI INT C disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291868] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291897] pci 0000:00:1d.3: PCI INT D disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.291925] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:45 zion-ubuntu kernel: [    0.292090] pci 0000:00:1d.7: PCI INT A disabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.292185] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
Feb  8 13:54:45 zion-ubuntu kernel: [    0.292192] Simple Boot Flag at 0x44 set to 0x1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.292683] cpufreq-nforce2: No nForce2 chipset.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.292767] Scanning for low memory corruption every 60 seconds
Feb  8 13:54:45 zion-ubuntu kernel: [    0.293124] audit: initializing netlink socket (disabled)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.293152] type=2000 audit(1423396476.290:1): initialized
Feb  8 13:54:45 zion-ubuntu kernel: [    0.314725] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb  8 13:54:45 zion-ubuntu kernel: [    0.320186] VFS: Disk quotas dquot_6.5.2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.320388] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.322474] fuse init (API version 7.13)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.322789] msgmni has been set to 953
Feb  8 13:54:45 zion-ubuntu kernel: [    0.323530] alg: No test for stdrng (krng)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.323735] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.323745] io scheduler noop registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.323751] io scheduler anticipatory registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.323757] io scheduler deadline registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.323903] io scheduler cfq registered (default)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324262]   alloc irq_desc for 24 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324270]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324293] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324314] pcieport 0000:00:1c.0: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324593]   alloc irq_desc for 25 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324601]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324619] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324637] pcieport 0000:00:1c.1: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324927]   alloc irq_desc for 26 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324935]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324955] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
Feb  8 13:54:45 zion-ubuntu kernel: [    0.324978] pcieport 0000:00:1c.2: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325273]   alloc irq_desc for 27 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325281]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325299] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325318] pcieport 0000:00:1c.3: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325583] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325872] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.325896] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.326249] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.326268] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.326595] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.326614] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.327000] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.327020] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.327417] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.327436] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.327774] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.327793] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.328123] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.328142] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.328478] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.328497] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node dec13ca8), AE_ALREADY_EXISTS
Feb  8 13:54:45 zion-ubuntu kernel: [    0.328621] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  8 13:54:45 zion-ubuntu kernel: [    0.329365] ACPI: AC Adapter [ACAD] (off-line)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.329633] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.329645] ACPI: Power Button [PWRB]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.329786] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.330666] ACPI: Lid Switch [LID0]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.330860] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.330871] ACPI: Sleep Button [SLPB]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.331055] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb  8 13:54:45 zion-ubuntu kernel: [    0.331064] ACPI: Power Button [PWRF]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.333040] ACPI: SSDT 1f380c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.334094] ACPI: SSDT 1f37fe10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.335050] Marking TSC unstable due to TSC halts in idle
Feb  8 13:54:45 zion-ubuntu kernel: [    0.335338] processor LNXCPU:00: registered as cooling_device0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.336400] ACPI: SSDT 1f380f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.337356] ACPI: SSDT 1f37ef10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.338098] Switching to clocksource hpet
Feb  8 13:54:45 zion-ubuntu kernel: [    0.339173] processor LNXCPU:01: registered as cooling_device1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.347566] ACPI: Battery Slot [BAT1] (battery absent)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.347605] isapnp: Scanning for PnP cards...
Feb  8 13:54:45 zion-ubuntu kernel: [    0.354070] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb  8 13:54:45 zion-ubuntu kernel: [    0.358362] brd: module loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    0.360026] loop: module loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    0.360345] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Feb  8 13:54:45 zion-ubuntu kernel: [    0.360651] ata_piix 0000:00:1f.2: version 2.13
Feb  8 13:54:45 zion-ubuntu kernel: [    0.360695] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  8 13:54:45 zion-ubuntu kernel: [    0.360710] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Feb  8 13:54:45 zion-ubuntu kernel: [    0.360802] ata_piix 0000:00:1f.2: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.404605] scsi0 : ata_piix
Feb  8 13:54:45 zion-ubuntu kernel: [    0.448598] scsi1 : ata_piix
Feb  8 13:54:45 zion-ubuntu kernel: [    0.451628] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
Feb  8 13:54:45 zion-ubuntu kernel: [    0.451639] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453134] Fixed MDIO Bus: probed
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453262] PPP generic driver version 2.4.2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453405] tun: Universal TUN/TAP device driver, 1.6
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453412] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453716] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453778] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453818] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453828] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453939] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.453999] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Feb  8 13:54:45 zion-ubuntu kernel: [    0.454021] ehci_hcd 0000:00:1d.7: debug port 1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.457938] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Feb  8 13:54:45 zion-ubuntu kernel: [    0.457987] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x38544400
Feb  8 13:54:45 zion-ubuntu kernel: [    0.505601] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Feb  8 13:54:45 zion-ubuntu kernel: [    0.505948] usb usb1: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506063] hub 1-0:1.0: USB hub found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506090] hub 1-0:1.0: 8 ports detected
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506329] uhci_hcd: USB Universal Host Controller Interface driver
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506430] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506454] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506464] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506595] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506648] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
Feb  8 13:54:45 zion-ubuntu kernel: [    0.506959] usb usb2: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507049] hub 2-0:1.0: USB hub found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507075] hub 2-0:1.0: 2 ports detected
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507218] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507245] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507254] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507379] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507449] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507743] usb usb3: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507838] hub 3-0:1.0: USB hub found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.507863] hub 3-0:1.0: 2 ports detected
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508001] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508024] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508033] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508170] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508238] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508522] usb usb4: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508617] hub 4-0:1.0: USB hub found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508645] hub 4-0:1.0: 2 ports detected
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508790] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508813] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508822] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Feb  8 13:54:45 zion-ubuntu kernel: [    0.508945] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Feb  8 13:54:45 zion-ubuntu kernel: [    0.509061] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
Feb  8 13:54:45 zion-ubuntu kernel: [    0.509362] usb usb5: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    0.509462] hub 5-0:1.0: USB hub found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.509485] hub 5-0:1.0: 2 ports detected
Feb  8 13:54:45 zion-ubuntu kernel: [    0.509763] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
Feb  8 13:54:45 zion-ubuntu kernel: [    0.510824] i8042.c: Warning: Keylock active.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.562469] i8042.c: Detected active multiplexing controller, rev 1.1.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.567887] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.567927] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Feb  8 13:54:45 zion-ubuntu kernel: [    0.567938] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Feb  8 13:54:45 zion-ubuntu kernel: [    0.567948] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Feb  8 13:54:45 zion-ubuntu kernel: [    0.567958] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Feb  8 13:54:45 zion-ubuntu kernel: [    0.568284] mice: PS/2 mouse device common for all mice
Feb  8 13:54:45 zion-ubuntu kernel: [    0.568788] rtc_cmos 00:03: RTC can wake from S4
Feb  8 13:54:45 zion-ubuntu kernel: [    0.568917] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.568975] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Feb  8 13:54:45 zion-ubuntu kernel: [    0.569384] device-mapper: uevent: version 1.0.3
Feb  8 13:54:45 zion-ubuntu kernel: [    0.592800] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Feb  8 13:54:45 zion-ubuntu kernel: [    0.613461] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Feb  8 13:54:45 zion-ubuntu kernel: [    0.625154] device-mapper: multipath: version 1.1.0 loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    0.625165] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    0.637367] ata2.00: CFA: P-SSD1800, Ver2.Y0C, max UDMA/66
Feb  8 13:54:45 zion-ubuntu kernel: [    0.637378] ata2.00: 15761088 sectors, multi 0: LBA 
Feb  8 13:54:45 zion-ubuntu kernel: [    0.648493] ata2.00: configured for UDMA/66
Feb  8 13:54:45 zion-ubuntu kernel: [    0.655056] Freeing initrd memory: 7831k freed
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663678] EISA: Probing bus 0 at eisa.0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663695] Cannot allocate resource for EISA slot 1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663702] Cannot allocate resource for EISA slot 2
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663708] Cannot allocate resource for EISA slot 3
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663714] Cannot allocate resource for EISA slot 4
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663721] Cannot allocate resource for EISA slot 5
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663727] Cannot allocate resource for EISA slot 6
Feb  8 13:54:45 zion-ubuntu kernel: [    0.663747] EISA: Detected 0 cards.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.664324] cpuidle: using governor ladder
Feb  8 13:54:45 zion-ubuntu kernel: [    0.664666] cpuidle: using governor menu
Feb  8 13:54:45 zion-ubuntu kernel: [    0.665894] TCP cubic registered
Feb  8 13:54:45 zion-ubuntu kernel: [    0.666440] NET: Registered protocol family 10
Feb  8 13:54:45 zion-ubuntu kernel: [    0.668684] NET: Registered protocol family 17
Feb  8 13:54:45 zion-ubuntu kernel: [    0.669866] Using IPI No-Shortcut mode
Feb  8 13:54:45 zion-ubuntu kernel: [    0.670129] PM: Resume from disk failed.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.670159] registered taskstats version 1
Feb  8 13:54:45 zion-ubuntu kernel: [    0.670845]   Magic number: 3:631:933
Feb  8 13:54:45 zion-ubuntu kernel: [    0.670869] mdio_bus 0: hash matches
Feb  8 13:54:45 zion-ubuntu kernel: [    0.670907] pci_express 0000:00:1c.3:pcie01: hash matches
Feb  8 13:54:45 zion-ubuntu kernel: [    0.671014] rtc_cmos 00:03: setting system clock to 2015-02-08 11:54:37 UTC (1423396477)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.671023] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.671028] EDD information not available.
Feb  8 13:54:45 zion-ubuntu kernel: [    0.755697] isapnp: No Plug & Play device found
Feb  8 13:54:45 zion-ubuntu kernel: [    0.756082] scsi 1:0:0:0: Direct-Access     ATA      P-SSD1800        Ver2 PQ: 0 ANSI: 5
Feb  8 13:54:45 zion-ubuntu kernel: [    0.756464] sd 1:0:0:0: [sda] 15761088 512-byte logical blocks: (8.06 GB/7.51 GiB)
Feb  8 13:54:45 zion-ubuntu kernel: [    0.756535] sd 1:0:0:0: Attached scsi generic sg0 type 0
Feb  8 13:54:45 zion-ubuntu kernel: [    0.756677] sd 1:0:0:0: [sda] Write Protect is off
Feb  8 13:54:45 zion-ubuntu kernel: [    0.756687] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb  8 13:54:45 zion-ubuntu kernel: [    0.756795] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb  8 13:54:45 zion-ubuntu kernel: [    0.757376]  sda: sda1 sda2 < sda5 >
Feb  8 13:54:45 zion-ubuntu kernel: [    0.760571] sd 1:0:0:0: [sda] Attached SCSI disk
Feb  8 13:54:45 zion-ubuntu kernel: [    0.760630] Freeing unused kernel memory: 664k freed
Feb  8 13:54:45 zion-ubuntu kernel: [    0.761273] Write protecting the kernel text: 4708k
Feb  8 13:54:45 zion-ubuntu kernel: [    0.761351] Write protecting the kernel read-only data: 1848k
Feb  8 13:54:45 zion-ubuntu kernel: [    0.800582] udev: starting version 151
Feb  8 13:54:45 zion-ubuntu kernel: [    0.921106] usb 1-5: new high speed USB device using ehci_hcd and address 3
Feb  8 13:54:45 zion-ubuntu kernel: [    1.167212] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb  8 13:54:45 zion-ubuntu kernel: [    1.167262] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  8 13:54:45 zion-ubuntu kernel: [    1.167340] r8169 0000:02:00.0: setting latency timer to 64
Feb  8 13:54:45 zion-ubuntu kernel: [    1.167422]   alloc irq_desc for 28 on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    1.167430]   alloc kstat_irqs on node -1
Feb  8 13:54:45 zion-ubuntu kernel: [    1.167459] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
Feb  8 13:54:45 zion-ubuntu kernel: [    1.170652] eth0: RTL8102e at 0xdfd42000, 00:1e:68:a4:84:fd, XID 04a00000 IRQ 28
Feb  8 13:54:45 zion-ubuntu kernel: [    1.197405] EXT4-fs (sda1): mounted filesystem with ordered data mode
Feb  8 13:54:45 zion-ubuntu kernel: [    1.263780] usb 1-5: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    1.548095] usb 3-1: new low speed USB device using uhci_hcd and address 2
Feb  8 13:54:45 zion-ubuntu kernel: [    1.724878] usb 3-1: configuration #1 chosen from 1 choice
Feb  8 13:54:45 zion-ubuntu kernel: [    7.435996] Adding 387064k swap on /dev/sda5.  Priority:-1 extents:1 across:387064k 
Feb  8 13:54:45 zion-ubuntu kernel: [    7.526030] udev: starting version 151
Feb  8 13:54:45 zion-ubuntu kernel: [    7.675919] lp: driver loaded but no devices found
Feb  8 13:54:45 zion-ubuntu kernel: [    8.065290] Linux agpgart interface v0.103
Feb  8 13:54:45 zion-ubuntu kernel: [    8.180365] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
Feb  8 13:54:45 zion-ubuntu kernel: [    8.180509] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.414533] cfg80211: Calling CRDA to update world regulatory domain
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453810] cfg80211: World regulatory domain updated:
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453822] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453833] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453842] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453850] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453859] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.453868] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 13:54:45 zion-ubuntu kernel: [    8.458137] intel_rng: FWH not detected
Feb  8 13:54:45 zion-ubuntu kernel: [    8.472383] type=1505 audit(1423396485.301:2):  operation="profile_load" pid=579 name="/sbin/dhclient3"
Feb  8 13:54:45 zion-ubuntu kernel: [    8.473232] type=1505 audit(1423396485.301:3):  operation="profile_load" pid=579 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Feb  8 13:54:45 zion-ubuntu kernel: [    8.473734] type=1505 audit(1423396485.301:4):  operation="profile_load" pid=579 name="/usr/lib/connman/scripts/dhclient-script"
Feb  8 13:54:45 zion-ubuntu kernel: [    8.485505] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Feb  8 13:54:45 zion-ubuntu kernel: [    8.485868] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Feb  8 13:54:45 zion-ubuntu kernel: [    8.491928] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x20000000
Feb  8 13:54:45 zion-ubuntu kernel: [    8.692127] r8169: eth0: link down
Feb  8 13:54:45 zion-ubuntu kernel: [    8.692379] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 13:54:45 zion-ubuntu kernel: [    8.768124] [drm] Initialized drm 1.1.0 20060810
Feb  8 13:54:45 zion-ubuntu kernel: [    8.776433] acer-wmi: Acer Laptop ACPI-WMI Extras
Feb  8 13:54:45 zion-ubuntu kernel: [    8.776444] acer-wmi: Blacklisted hardware detected - not loading
Feb  8 13:54:45 zion-ubuntu kernel: [    8.840615] usbcore: registered new interface driver hiddev
Feb  8 13:54:45 zion-ubuntu kernel: [    8.865999] input: MLK OX-1400G Wireless Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
Feb  8 13:54:45 zion-ubuntu kernel: [    8.866567] generic-usb 0003:04FC:05DA.0001: input,hiddev96,hidraw0: USB HID v1.10 Mouse [MLK OX-1400G Wireless Mouse] on usb-0000:00:1d.1-1/input0
Feb  8 13:54:45 zion-ubuntu kernel: [    8.866651] usbcore: registered new interface driver usbhid
Feb  8 13:54:45 zion-ubuntu kernel: [    8.866662] usbhid: v2.6:USB HID core driver
Feb  8 13:54:45 zion-ubuntu kernel: [    8.874833] Linux video capture interface: v2.00
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Successfully dropped root privileges.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: avahi-daemon 0.6.25 starting up.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Successfully called chroot().
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Successfully dropped remaining capabilities.
Feb  8 13:54:45 zion-ubuntu NetworkManager: <info>  starting...
Feb  8 13:54:45 zion-ubuntu kernel: [    9.093053] acerhdf: Acer Aspire One Fan driver, v.0.5.20
Feb  8 13:54:45 zion-ubuntu kernel: [    9.093069] acerhdf: unknown (unsupported) BIOS version Acer/AOA110         /v0.3109, please report, aborting!
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: No service file found in /etc/avahi/services.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.10.10.1.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: New relevant interface eth0.IPv4 for mDNS.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Network interface enumeration completed.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Registering new address record for 10.10.10.1 on eth0.IPv4.
Feb  8 13:54:45 zion-ubuntu avahi-daemon[700]: Registering HINFO record with values 'I686'/'LINUX'.
Feb  8 13:54:45 zion-ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Feb  8 13:54:45 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Feb  8 13:54:45 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Feb  8 13:54:45 zion-ubuntu NetworkManager:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Option
Feb  8 13:54:46 zion-ubuntu kernel: [    9.184840] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  8 13:54:46 zion-ubuntu kernel: [    9.184865] ath5k 0000:03:00.0: setting latency timer to 64
Feb  8 13:54:46 zion-ubuntu kernel: [    9.184950] ath5k 0000:03:00.0: registered as 'phy0'
Feb  8 13:54:46 zion-ubuntu kernel: [    9.224817] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:d101)
Feb  8 13:54:46 zion-ubuntu kernel: [    9.232510] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
Feb  8 13:54:46 zion-ubuntu kernel: [    9.232975] usbcore: registered new interface driver uvcvideo
Feb  8 13:54:46 zion-ubuntu kernel: [    9.234016] USB Video Class driver (v0.1.0)
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Huawei
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin AnyData
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Nokia
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Gobi
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Novatel
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Sierra
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin MotoC
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Ericsson MBM
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin ZTE
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Generic
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Option High-Speed
Feb  8 13:54:46 zion-ubuntu modem-manager: Loaded plugin Longcheer
Feb  8 13:54:46 zion-ubuntu kernel: [    9.356088] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:46 zion-ubuntu kernel: [    9.356102] i915 0000:00:02.0: setting latency timer to 64
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: addresses count: 1
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPluginIfupdown: guessed connection type (wlan0) = 802-3-ethernet
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-3-ethernet, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: addresses count: 1
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
Feb  8 13:54:46 zion-ubuntu kernel: [    9.673321] mtrr: no more MTRRs available
Feb  8 13:54:46 zion-ubuntu kernel: [    9.673334] [drm] MTRR allocation failed.  Graphics performance may suffer.
Feb  8 13:54:46 zion-ubuntu kernel: [    9.680977] type=1505 audit(1423396486.509:5):  operation="profile_load" pid=753 name="/usr/share/gdm/guest-session/Xsession"
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: autoconnect
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: autoconnect
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0, iface: eth0)
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPluginIfupdown: locking wired connection setting
Feb  8 13:54:46 zion-ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: (159424240) ... get_connections.
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: (159424240) ... get_connections (managed=false): return empty list.
Feb  8 13:54:46 zion-ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb  8 13:54:46 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Feb  8 13:54:46 zion-ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb  8 13:54:46 zion-ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Feb  8 13:54:46 zion-ubuntu kernel: [    9.681532] [drm] set up 7M of stolen space
Feb  8 13:54:46 zion-ubuntu kernel: [    9.693617] type=1505 audit(1423396486.520:6):  operation="profile_replace" pid=754 name="/sbin/dhclient3"
Feb  8 13:54:46 zion-ubuntu kernel: [    9.694456] type=1505 audit(1423396486.520:7):  operation="profile_replace" pid=754 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Feb  8 13:54:46 zion-ubuntu kernel: [    9.694943] type=1505 audit(1423396486.520:8):  operation="profile_replace" pid=754 name="/usr/lib/connman/scripts/dhclient-script"
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  modem-manager is now available
Feb  8 13:54:46 zion-ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Feb  8 13:54:46 zion-ubuntu NetworkManager: <info>  Trying to start the supplicant...
Feb  8 13:54:46 zion-ubuntu kernel: [    9.822325] type=1505 audit(1423396486.649:9):  operation="profile_load" pid=767 name="/usr/bin/evince"
Feb  8 13:54:46 zion-ubuntu kernel: [    9.854203] type=1505 audit(1423396486.681:10):  operation="profile_load" pid=775 name="/usr/lib/cups/backend/cups-pdf"
Feb  8 13:54:46 zion-ubuntu kernel: [    9.854506] [drm] initialized overlay support
Feb  8 13:54:46 zion-ubuntu kernel: [    9.855171] type=1505 audit(1423396486.681:11):  operation="profile_load" pid=775 name="/usr/sbin/cupsd"
Feb  8 13:54:46 zion-ubuntu kernel: [    9.967972] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000/0xa0000
Feb  8 13:54:46 zion-ubuntu kernel: [   10.051573] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
Feb  8 13:54:46 zion-ubuntu avahi-daemon[700]: Server startup complete. Host name is zion-ubuntu.local. Local service cookie is 2668198378.
Feb  8 13:54:47 zion-ubuntu init: apport pre-start process (828) terminated with status 1
Feb  8 13:54:47 zion-ubuntu cron[835]: (CRON) INFO (pidfile fd = 3)
Feb  8 13:54:47 zion-ubuntu kernel: [   10.272651] ath: EEPROM regdomain: 0x65
Feb  8 13:54:47 zion-ubuntu kernel: [   10.272658] ath: EEPROM indicates we should expect a direct regpair map
Feb  8 13:54:47 zion-ubuntu kernel: [   10.272668] ath: Country alpha2 being used: 00
Feb  8 13:54:47 zion-ubuntu kernel: [   10.272674] ath: Regpair used: 0x65
Feb  8 13:54:47 zion-ubuntu anacron[844]: Anacron 2.3 started on 2015-02-08
Feb  8 13:54:47 zion-ubuntu acpid: starting up with proc fs
Feb  8 13:54:47 zion-ubuntu cron[846]: (CRON) STARTUP (fork ok)
Feb  8 13:54:47 zion-ubuntu cron[846]: (CRON) INFO (Running @reboot jobs)
Feb  8 13:54:47 zion-ubuntu init: apport post-stop process (848) terminated with status 1
Feb  8 13:54:47 zion-ubuntu anacron[844]: Will run job `cron.daily' in 5 min.
Feb  8 13:54:47 zion-ubuntu anacron[844]: Jobs will be executed sequentially
Feb  8 13:54:47 zion-ubuntu acpid: 36 rules loaded
Feb  8 13:54:47 zion-ubuntu acpid: waiting for events: event logging is off
Feb  8 13:54:47 zion-ubuntu kernel: [   10.330596] fb0: inteldrmfb frame buffer device
Feb  8 13:54:47 zion-ubuntu kernel: [   10.330605] registered panic notifier
Feb  8 13:54:47 zion-ubuntu kernel: [   10.330626] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Feb  8 13:54:47 zion-ubuntu kernel: [   10.330742] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 13:54:47 zion-ubuntu kernel: [   10.330823] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb  8 13:54:47 zion-ubuntu kernel: [   10.349363] vga16fb: initializing
Feb  8 13:54:47 zion-ubuntu kernel: [   10.349375] vga16fb: mapped to 0xc00a0000
Feb  8 13:54:47 zion-ubuntu kernel: [   10.349387] vga16fb: not registering due to another framebuffer present
Feb  8 13:54:47 zion-ubuntu NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Feb  8 13:54:47 zion-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlan0, iface: wlan0)
Feb  8 13:54:47 zion-ubuntu NetworkManager:    SCPluginIfupdown: locking wired connection setting
Feb  8 13:54:47 zion-ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 2
Feb  8 13:54:47 zion-ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Feb  8 13:54:47 zion-ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k')
Feb  8 13:54:47 zion-ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb  8 13:54:47 zion-ubuntu kernel: [   10.422426] phy0: Selected rate control algorithm 'minstrel'
Feb  8 13:54:47 zion-ubuntu kernel: [   10.424827] Registered led device: ath5k-phy0::rx
Feb  8 13:54:47 zion-ubuntu kernel: [   10.424894] Registered led device: ath5k-phy0::tx
Feb  8 13:54:47 zion-ubuntu kernel: [   10.424903] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Feb  8 13:54:47 zion-ubuntu kernel: [   10.545221] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Feb  8 13:54:47 zion-ubuntu kernel: [   10.675585] Console: switching to colour frame buffer device 128x37
Feb  8 13:54:47 zion-ubuntu avahi-daemon[700]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.16.
Feb  8 13:54:47 zion-ubuntu kernel: [   10.920342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 13:54:47 zion-ubuntu avahi-daemon[700]: New relevant interface wlan0.IPv4 for mDNS.
Feb  8 13:54:47 zion-ubuntu avahi-daemon[700]: Registering new address record for 192.168.0.16 on wlan0.IPv4.
Feb  8 13:54:47 zion-ubuntu gdm-binary[882]: WARNING: Unable to find users: no seat-id found
Feb  8 13:54:48 zion-ubuntu dhclient: isc-dhclient-V3.1.3
Feb  8 13:54:48 zion-ubuntu dhclient: isc-dhclient-V3.1.3
Feb  8 13:54:48 zion-ubuntu acpid: client connected from 1078[0:0]
Feb  8 13:54:48 zion-ubuntu acpid: 1 client rule loaded
Feb  8 13:54:48 zion-ubuntu dhcpd: Wrote 3 leases to leases file.
Feb  8 13:54:51 zion-ubuntu dhcpd: 
Feb  8 13:54:51 zion-ubuntu dhcpd: No subnet declaration for wlan0 (192.168.0.16).
Feb  8 13:54:51 zion-ubuntu dhcpd: ** Ignoring requests on wlan0.  If this is not what
Feb  8 13:54:51 zion-ubuntu dhcpd:    you want, please write a subnet declaration
Feb  8 13:54:51 zion-ubuntu dhcpd:    in your dhcpd.conf file for the network segment
Feb  8 13:54:51 zion-ubuntu dhcpd:    to which interface wlan0 is attached. **
Feb  8 13:54:51 zion-ubuntu dhcpd: 
Feb  8 13:54:53 zion-ubuntu kernel: [   16.690037] ppdev: user-space parallel port driver
Feb  8 13:54:56 zion-ubuntu init: plymouth-stop pre-start process (1278) terminated with status 1
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Sucessfully called chroot.
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Sucessfully dropped privileges.
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Sucessfully limited resources.
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Running.
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Watchdog thread running.
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Canary thread running.
Feb  8 13:54:56 zion-ubuntu polkitd[1291]: started daemon version 0.96 using authority implementation `local' version `0.96'
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Sucessfully made thread 1279 of process 1279 (n/a) owned by '114' high priority at nice level -11.
Feb  8 13:54:56 zion-ubuntu rtkit-daemon[1287]: Supervising 1 threads of 1 processes of 1 users.
Feb  8 13:54:57 zion-ubuntu rtkit-daemon[1287]: Sucessfully made thread 1305 of process 1279 (n/a) owned by '114' RT at priority 5.
Feb  8 13:54:57 zion-ubuntu rtkit-daemon[1287]: Supervising 2 threads of 1 processes of 1 users.
Feb  8 13:54:57 zion-ubuntu init: anacron main process (844) killed by TERM signal
Feb  8 13:54:57 zion-ubuntu kernel: [   20.302358] CPU0 attaching NULL sched-domain.
Feb  8 13:54:57 zion-ubuntu kernel: [   20.302375] CPU1 attaching NULL sched-domain.
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324169] CPU0 attaching sched-domain:
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324180]  domain 0: span 0-1 level SIBLING
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324189]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324208]   domain 1: span 0-1 level MC
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324216]    groups: 0-1 (cpu_power = 1178)
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324234] CPU1 attaching sched-domain:
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324242]  domain 0: span 0-1 level SIBLING
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324250]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324267]   domain 1: span 0-1 level MC
Feb  8 13:54:57 zion-ubuntu kernel: [   20.324275]    groups: 0-1 (cpu_power = 1178)
Feb  8 13:54:57 zion-ubuntu rtkit-daemon[1287]: Sucessfully made thread 1321 of process 1279 (n/a) owned by '114' RT at priority 5.
Feb  8 13:54:57 zion-ubuntu rtkit-daemon[1287]: Supervising 3 threads of 1 processes of 1 users.
Feb  8 13:54:57 zion-ubuntu gdm-simple-greeter[1183]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Feb  8 13:54:57 zion-ubuntu acpid: client connected from 1371[108:114]
Feb  8 13:54:57 zion-ubuntu acpid: 1 client rule loaded
Feb  8 13:54:59 zion-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb  8 13:54:59 zion-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb  8 13:54:59 zion-ubuntu dhclient: All rights reserved.
Feb  8 13:54:59 zion-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb  8 13:54:59 zion-ubuntu dhclient: 
Feb  8 13:54:59 zion-ubuntu dhclient: Listening on LPF/wlan0/00:1f:e2:91:40:16
Feb  8 13:54:59 zion-ubuntu dhclient: Sending on   LPF/wlan0/00:1f:e2:91:40:16
Feb  8 13:54:59 zion-ubuntu dhclient: Sending on   Socket/fallback
Feb  8 13:55:00 zion-ubuntu dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Feb  8 13:55:00 zion-ubuntu avahi-daemon[700]: Withdrawing address record for 192.168.0.16 on wlan0.
Feb  8 13:55:00 zion-ubuntu avahi-daemon[700]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.16.
Feb  8 13:55:00 zion-ubuntu avahi-daemon[700]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb  8 13:55:00 zion-ubuntu kernel: [   24.114670] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 13:55:00 zion-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb  8 13:55:00 zion-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb  8 13:55:00 zion-ubuntu dhclient: All rights reserved.
Feb  8 13:55:00 zion-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb  8 13:55:00 zion-ubuntu dhclient: 
Feb  8 13:55:00 zion-ubuntu dhclient: Listening on LPF/eth0/00:1e:68:a4:84:fd
Feb  8 13:55:00 zion-ubuntu dhclient: Sending on   LPF/eth0/00:1e:68:a4:84:fd
Feb  8 13:55:00 zion-ubuntu dhclient: Sending on   Socket/fallback
Feb  8 13:55:00 zion-ubuntu dhclient: DHCPRELEASE on eth0 to 10.10.10.1 port 67
Feb  8 13:55:01 zion-ubuntu avahi-daemon[700]: Withdrawing address record for 10.10.10.1 on eth0.
Feb  8 13:55:01 zion-ubuntu avahi-daemon[700]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.10.10.1.
Feb  8 13:55:01 zion-ubuntu avahi-daemon[700]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb  8 13:55:01 zion-ubuntu dhcpd: receive_packet failed on eth0: Network is down
Feb  8 13:55:01 zion-ubuntu kernel: [   24.255901] r8169: eth0: link down
Feb  8 13:55:01 zion-ubuntu kernel: [   24.256048] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 13:55:01 zion-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb  8 13:55:01 zion-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb  8 13:55:01 zion-ubuntu dhclient: All rights reserved.
Feb  8 13:55:01 zion-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb  8 13:55:01 zion-ubuntu dhclient: 
Feb  8 13:55:01 zion-ubuntu dhclient: Listening on LPF/wlan0/00:1f:e2:91:40:16
Feb  8 13:55:01 zion-ubuntu dhclient: Sending on   LPF/wlan0/00:1f:e2:91:40:16
Feb  8 13:55:01 zion-ubuntu dhclient: Sending on   Socket/fallback
Feb  8 13:55:01 zion-ubuntu dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Feb  8 13:55:01 zion-ubuntu dhclient: send_packet: Network is unreachable
Feb  8 13:55:01 zion-ubuntu dhclient: send_packet: please consult README file regarding broadcast address.
Feb  8 13:55:01 zion-ubuntu kernel: [   24.435358] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 13:55:03 zion-ubuntu ntpdate[1063]: can't find host ntp.ubuntu.com
Feb  8 13:55:03 zion-ubuntu ntpdate[1063]: no servers can be used, exiting
Feb  8 13:55:05 zion-ubuntu kernel: [   28.169774] wlan0: direct probe to AP 00:11:6b:26:a4:70 (try 1)
Feb  8 13:55:05 zion-ubuntu kernel: [   28.172346] wlan0: direct probe responded
Feb  8 13:55:05 zion-ubuntu kernel: [   28.172362] wlan0: authenticate with AP 00:11:6b:26:a4:70 (try 1)
Feb  8 13:55:05 zion-ubuntu kernel: [   28.173950] wlan0: authenticated
Feb  8 13:55:05 zion-ubuntu kernel: [   28.174005] wlan0: associate with AP 00:11:6b:26:a4:70 (try 1)
Feb  8 13:55:05 zion-ubuntu kernel: [   28.176234] wlan0: RX AssocResp from 00:11:6b:26:a4:70 (capab=0x431 status=0 aid=2)
Feb  8 13:55:05 zion-ubuntu kernel: [   28.176254] wlan0: associated
Feb  8 13:55:05 zion-ubuntu kernel: [   28.178088] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  8 13:55:05 zion-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb  8 13:55:05 zion-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb  8 13:55:05 zion-ubuntu dhclient: All rights reserved.
Feb  8 13:55:05 zion-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb  8 13:55:05 zion-ubuntu dhclient: 
Feb  8 13:55:05 zion-ubuntu kernel: [   28.648690] __ratelimit: 12 callbacks suppressed
Feb  8 13:55:05 zion-ubuntu kernel: [   28.648702] type=1503 audit(1423396505.477:16):  operation="open" pid=1439 parent=1408 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Feb  8 13:55:05 zion-ubuntu dhclient: Listening on LPF/wlan0/00:1f:e2:91:40:16
Feb  8 13:55:05 zion-ubuntu dhclient: Sending on   LPF/wlan0/00:1f:e2:91:40:16
Feb  8 13:55:05 zion-ubuntu dhclient: Sending on   Socket/fallback
Feb  8 13:55:06 zion-ubuntu avahi-daemon[700]: Registering new address record for fe80::21f:e2ff:fe91:4016 on wlan0.*.
Feb  8 13:55:07 zion-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Feb  8 13:55:07 zion-ubuntu dhclient: DHCPOFFER of 192.168.0.16 from 192.168.0.1
Feb  8 13:55:07 zion-ubuntu dhclient: DHCPREQUEST of 192.168.0.16 on wlan0 to 255.255.255.255 port 67
Feb  8 13:55:07 zion-ubuntu dhclient: DHCPACK of 192.168.0.16 from 192.168.0.1
Feb  8 13:55:07 zion-ubuntu avahi-daemon[700]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.16.
Feb  8 13:55:07 zion-ubuntu avahi-daemon[700]: New relevant interface wlan0.IPv4 for mDNS.
Feb  8 13:55:07 zion-ubuntu avahi-daemon[700]: Registering new address record for 192.168.0.16 on wlan0.IPv4.
Feb  8 13:55:07 zion-ubuntu dhclient: bound to 192.168.0.16 -- renewal in 2815 seconds.
Feb  8 13:55:11 zion-ubuntu ntpdate[1462]: step time server 91.189.94.4 offset -0.243082 sec
Feb  8 13:55:11 zion-ubuntu gdm-simple-greeter[1183]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `row_align >= 0.0 && row_align <= 1.0' failed
Feb  8 13:55:11 zion-ubuntu gdm-simple-greeter[1183]: last message repeated 12 times
Feb  8 13:55:11 zion-ubuntu gdm-session-worker[1205]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Feb  8 13:55:15 zion-ubuntu kernel: [   38.724124] wlan0: no IPv6 routers present
Feb  8 13:55:23 zion-ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  8 13:55:23 zion-ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  8 13:55:23 zion-ubuntu rtkit-daemon[1287]: Sucessfully made thread 1567 of process 1567 (n/a) owned by '1000' high priority at nice level -11.
Feb  8 13:55:23 zion-ubuntu rtkit-daemon[1287]: Supervising 4 threads of 2 processes of 2 users.
Feb  8 13:55:23 zion-ubuntu rtkit-daemon[1287]: Sucessfully made thread 1584 of process 1567 (n/a) owned by '1000' RT at priority 5.
Feb  8 13:55:23 zion-ubuntu rtkit-daemon[1287]: Supervising 5 threads of 2 processes of 2 users.
Feb  8 13:55:24 zion-ubuntu rtkit-daemon[1287]: Sucessfully made thread 1590 of process 1590 (n/a) owned by '1000' high priority at nice level -11.
Feb  8 13:55:24 zion-ubuntu rtkit-daemon[1287]: Supervising 6 threads of 3 processes of 2 users.
Feb  8 13:55:24 zion-ubuntu pulseaudio[1590]: pid.c: Daemon already running.
Feb  8 13:56:36 zion-ubuntu AptDaemon: INFO: Initializing daemon
Feb  8 13:56:51 zion-ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  8 14:01:37 zion-ubuntu AptDaemon: INFO: Quiting due to inactivity
Feb  8 14:01:37 zion-ubuntu AptDaemon: INFO: Shutdown was requested
Feb  8 14:01:57 zion-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 1)
Feb  8 14:01:57 zion-ubuntu kernel: [  440.541498] r8169: eth0: link up
Feb  8 14:01:57 zion-ubuntu kernel: [  440.541918] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb  8 14:01:58 zion-ubuntu avahi-daemon[700]: Registering new address record for fe80::21e:68ff:fea4:84fd on eth0.*.
Feb  8 14:02:01 zion-ubuntu dhcpd: DHCPDISCOVER from 00:80:ad:73:b7:fe via eth0
Feb  8 14:02:02 zion-ubuntu dhcpd: DHCPOFFER on 10.10.10.4 to 00:80:ad:73:b7:fe (home) via eth0
Feb  8 14:02:04 zion-ubuntu dhcpd: DHCPREQUEST for 10.10.10.4 (10.10.10.1) from 00:80:ad:73:b7:fe (home) via eth0
Feb  8 14:02:04 zion-ubuntu dhcpd: DHCPACK on 10.10.10.4 to 00:80:ad:73:b7:fe (home) via eth0
Feb  8 14:02:07 zion-ubuntu kernel: [  451.296105] eth0: no IPv6 routers present
```

---

### Post by Lars Noodén on 2015-02-08
Ok the DHCP part looks ok, from that angle.  You have at that boot 192.168.0.16 on wlan0 and on eth0 you have 10.10.10.1 with one machine recieving a DHCP lease 10.10.10.4  We can also see that the time was set by ntpdate, so that implies the external network is ok.  That mostly leaves just the forwarding.  Can you check the permanent settings?

```

grep forward /etc/sysctl.conf

```

It should have a line "net.ipv4.ip_forward=1" without a pound sign.  

Then can you confirm the current forwarding status?

```

sysctl net.ipv4.ip_forward

```

It should say "net.ipv4.ip_forward = **1**"

---

### Post by offir on 2015-02-08
```
grep forward /etc/sysctl.conf
```
give this
```
# Uncomment the next line to enable packet [COLOR="#FF0000"]forward[/COLOR]ing for IPv4
net.ipv4.ip_[COLOR="#FF0000"]forward[/COLOR]=1
#net.ipv4.conf.default.[COLOR="#FF0000"]forward[/COLOR]ing=1
#net.ipv4.conf.all.[COLOR="#FF0000"]forward[/COLOR]ing=1
# Uncomment the next line to enable packet [COLOR="#FF0000"]forward[/COLOR]ing for IPv6
#net.ipv6.conf.all.[COLOR="#FF0000"]forward[/COLOR]ing=1

```



```
sysctl net.ipv4.ip_forward
```
give this
```
net.ipv4.ip_forward = 1
```

---

### Post by Lars Noodén on 2015-02-08
Ok.  Those appear to show the correct values.  On the server can you ping google, just to be sure that DNS works as well as the net?

```

ping www.google.com

```

On the machine connected to eth0 can you do all of these four (if 192.168.0.16 is the current address for wlan0 on the server)?

```

ping 10.10.10.1
ping 192.168.0.16
ping 8.8.8.8
ping www.google.com

```

---

### Post by offir on 2015-02-08
from the main server ican ping to [www.google.com](www.google.com)


from a machine connected to eth0
i cant ping anywhere

---

### Post by Lars Noodén on 2015-02-08
and just to double check, the machine connected to eth0 did get an ip address via DHCP?  On the machine connected to eth0

```

ifconfig eth0

```

if so, then the remaining item must be the packet filter on the server.  

```

sudo /usr/sbin/ufw status verbose

```

[https://help.ubuntu.com/lts/serverguide/firewall.html#ip-masquerading](https://help.ubuntu.com/lts/serverguide/firewall.html#ip-masquerading)

---

### Post by offir on 2015-02-08
> the machine connected to eth0 did get an ip address via DHCP?
 yes

10.10.10.3

after restart (of the laptop)
i can ping to 10.10.10.1 and 192.168.0.16



```
sudo /usr/sbin/ufw status verbose
```
status: inactive

---

### Post by Lars Noodén on 2015-02-08
Ok.  Then as far as I know the only missing piece is the forwarding in the filter which was described in #9 above.

```

[s]iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE[/s]

```

However, that needs to be made permanent by putting it in the right file, so in the file /etc/ufw/before.rules, try the following

```

-A POSTROUTING -s 10.10.10.0/24 -o wlan0 -j MASQUERADE

```

and then reload UFW.  Be sure to save a copy of the original /etc/ufw/before.rules file just in case.

```

sudo ufw disable && sudo ufw enable

```

I don't have a spare machine to test that on, yet, but it's the general idea.

---

### Post by offir on 2015-02-08
how do i save a copy of this file 
i am trying 
and it say i dont have  privileges
i try sudo su nautilus
gksudo nautilus
sudo nautilus

same result

---

### Post by Lars Noodén on 2015-02-08
Give [nano](http://manpages.ubuntu.com/manpages/lucid/en/man1/nano.1.html) a try.  

```

sudo nano /etc/ufw/before.rules

```

---

### Post by offir on 2015-02-08
```
-A POSTROUTING -s 10.10.10.0/24 -o wlan0 -j MASQUERADE
```

this command do not work

---

### Post by Lars Noodén on 2015-02-08
it's not a command in and of itself but parameters that are added to *before.rules*

---

### Post by offir on 2015-02-08
i copy the line in to the before.rules file
and save


then use this command
```
sudo ufw disable && sudo ufw enable
```

i got this 
```
ERROR: problem running ufw-init
```

---

### Post by Lars Noodén on 2015-02-08
Ok. Then we'll skip UFW this time.

```

sudo ufw reset

```

The quick and dirty way would be to put the following into /etc/rc.local just ahead of the line "exit 0"

```

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

```

The official way is with UFW, but if you're not otherwise using UFW then rc.local works.

---

### Post by offir on 2015-02-08
after this two lines
do restart ?

---

### Post by Lars Noodén on 2015-02-08
Yes.  A restart will test that everything is in place.  The file /etc/rc.local is a shell script that gets run by root at the tail end of the start up.   By putting the line there, it gets run once when the system boots, after everything else is in place.

---

### Post by offir on 2015-02-08
What is going on here
My post is split into two
Some messages have been deleted



It just does not work

The computer will not connect to the wireless network
And there is no sign of a wireless network
in the Lower panel because it disappears


only when i go to ```
/etc/network/interfaces
```
and delete all but

```
auto lo
iface lo inet loopback
```

the icon return
and i can tell the computer conncet


in both cases i have dhcp

in first case with only two lines
i cant ping any where

in seconde case with all the setting
i can ping 10.10.10.1 and 192.168.0.16

---

### Post by Bucky Ball on 2015-02-08
For some odd reason post 52 and the reply, 53, became a new thread. I merged that thread with this one and deleted the duplicated post 52. ;)

---

### Post by offir on 2015-02-08
But there were 62 messages
Now shows only 54

---

### Post by Lars Noodén on 2015-02-08
Ok.  I set up a machine to try to duplicate the scenario that your describe that shares its wireless connection over its ethernet connection.  The wireless connection (wlan0) I left alone and it gets its address from another DHCP service.  The ethernet connection, I had to assign a static IP address.  In /etc/network/interfaces I added

```

auto eth0
iface eth0 inet static
address 10.10.10.1
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255

```

Then I installed the DHCP server.  On 10.04 LTS, which by the way goes away in April, it is the package dhcp3-server.  On 14.04 LTS, which you will probably be moving to before April, it is the package isc-dhcp-server.  For the former, the configuration file is /etc/dhcp3/dhcpd.conf for the latter the configuration file is /etc/dhcpd/dhcpd.conf.  In that I added information about the subnet to be served and the DNS.

Then I uncommented a line in /etc/sysctl.conf to enable forwarding.  Because the change is in sysctl.conf it takes effect after booting.  

```

net.ipv4.ip_forward=1

```

Then I enabled forwarding in the packet filter.  

```

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

```

For that change to be permanent, I put it in /etc/rc.local so it is run last after rebooting.  The right way would have been to mess with UFW, but I need to find the right notes on that.

---

### Post by offir on 2015-02-08
This is exactly the settings
I did according to what you told me

But
No ping beyond 192.168.0.16


By the way
Thanks again for your help

---

### Post by Lars Noodén on 2015-02-08
We'll get this sorted, I think.

What is the current status of forwarding in the server's kernel?

```

sysctl net.ipv4.ip_forward

```

What is the current status of forwarding in the packet filter?

```

sudo iptables-save | grep MASQ

```

---

### Post by Lars Noodén on 2015-02-08
For what it's worth, sharing can be done with a few clicks in 14.04 LTS.  In 14.04 LTS go to the networking icon in the panel at the top of the screen, then choose Edit Connections, then choose your Wi-Fi connection, then Edit, then IPv4 Settingd, then for Method choose Shared to Other Computers.

---

### Post by offir on 2015-02-08
I would like to upgrade
to a More suitable version
I guess there is special versions of what I try to do (router version or some thing like that)


But I do not know if the computer's hardware matches
I tried Once or twice to install Ubuntu 12.04 and it did not fit



> What is the current status of forwarding in the server's kernel?



```
sysctl net.ipv4.ip_forward
```

What is the current status of forwarding in the packet filter?



```
sudo iptables-save | grep MASQ
```




net.ipv4.ip_forward = 1


and 


-A POSTROUTING -o wlan0 -j MASQUERADE





There is something strange

When a computer  is connected 
To the  wired connection (eth0) 

Computer \ Router
Trying to get out to the Internet via wired connection
If I disconnect the cable
He is trying to get out to the Internet through wireless connection

---

