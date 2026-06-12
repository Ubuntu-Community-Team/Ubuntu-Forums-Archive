---
title: "ICS on Ubuntu"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by ihatecommies on 2007-02-10
I have two Windows boxes and one Ubuntu box through which I want to share an internet connection with Windows. All of my network cards are working properly.

None of the posts about this topic in this forum has worked for me, now even the long thread of antiwindows about this. Everybody keeps saying (and I have even read this in a book) that you have type in commands like ```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
``` but that simply doesn't work and it gets reseted after a reboot.

Here's how my /etc/network/interfaces looks like:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet static
address 192.168.0.200
netmask 255.255.255.0
gateway 192.168.0.1
```

```
eth0      Link encap:Ethernet  HWaddr 00:04:76:21:7B:A6  
          inet addr:80.57.193.157  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe21:7ba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:175947531 (167.7 MiB)  TX bytes:144362861 (137.6 MiB)
          Interrupt:217 Base address:0x6400 

eth1      Link encap:Ethernet  HWaddr 00:17:31:2E:F5:74  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:74 

eth2      Link encap:Ethernet  HWaddr 00:17:31:2E:F9:C0  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe2e:f9c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16026 (15.6 KiB)  TX bytes:17909 (17.4 KiB)
          Interrupt:225 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21791 (21.2 KiB)  TX bytes:21791 (21.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Note: I don't need eth1 for now because I will hook it later on with my second Windows box.

So here's my setup:

Ubuntu 6.10 Edgy <------> Windows XP

Ubuntu gives an IP address to Windows, but now it has to share an internet connection with Windows as well.

What should I do?

---

### Post by koenn on 2007-02-10
> Everybody keeps saying (and I have even read this in a book) that you have type in commands like
Code:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

but that simply doesn't work and it gets reseted after a reboot.
It roughly comes down to this, but with some extra work to
- make it work
- make it persistent after a reboot. 

I'm giving you the command line version. There may be GUI ways to do this but I don't know them. (Firestarter maybe ?)

first, create text file with gedit, as folows (from the terminal)
```
sudo gedit /etc/init.d/iptables.sh
```
copy & paste following commands into it, save it, close the file
```

iptables --flush
iptables -P FORWARD ACCEPT

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

echo "1" > /proc/sys/net/ipv4/ip_forward

```

then, in a terminal, execute the folowing commands to make this an executable script, and have it executed at startup

```

chown root:admin /etc/init.d/iptables.sh
chmod 770 /etc/init.d/iptables.sh
update-rc.d iptables.sh defaults 20

```

you can "reboot for changes to take effect", or you can just run
```
/etc/init.d/iptables.sh
``` 
and it should already be working. 

---------
I'm doing this of the top of my head so there could be a mistake here and there. Post back if there are any problems
Also, it's a bit quick and dirty : it enables internet connection sharing, but does not provide any security to the ubuntu box that is directly connected to the internet through eth0. That can be accomplished with additional iptables statements

---

### Post by ihatecommies on 2007-02-10
It doesn't work. I have first executed all those commands, restarted the network on my Windows box and nothing happened. That's my point exactly, the iptables commands have never had any kind of effect on my Ubuntu box.

---

### Post by ihatecommies on 2007-02-10
BTW I prefer to set this up without a GUI (command line and editing text files with a command line is how I prefer it).

---

### Post by koenn on 2007-02-10
> It doesn't work. I have first executed all those commands, restarted the network on my Windows box and nothing happened. That's my point exactly, the iptables commands have never had any kind of effect on my Ubuntu box.
You do have iptables installed, do you ? check with
```
which iptables
```
what does it say ?

> It doesn't work.  ... nothing happened
This is not something that you can see happening :) .  How did you test whether it works, and what makes you think it doesn't  ?  (just making sure we're on the same wavelenght here)

You're sure you have network between the ubuntu box and the windows box ? They can each ping the other one ? 

Can the Ubuntu box get on the internet ? 

What does the Windows box have for default gateway ?

---

### Post by ihatecommies on 2007-02-10
[QUOTE=koenn]You do have iptables installed, do you ? check with
```
which iptables
```
what does it say ?[/QUOTE]

I have iptables installed. It says: ```
/sbin/iptables
```

> This is not something that you can see happening :) .  How did you test whether it works, and what makes you think it doesn't  ?  (just making sure we're on the same wavelenght here)

I went to the Windows box, restarted its network, and opened Firefox and I got a "can't connect" error page. I went to IE and got the same error. There is no internet on the Windows box.

> You're sure you have network between the ubuntu box and the windows box ? They can each ping the other one ? 

Yes, I can ping Windows and from Windows I can ping Ubuntu.

> Can the Ubuntu box get on the internet ? 

Yes I'm now in Ubuntu, writing this.

> What does the Windows box have for default gateway ?

Ubuntu automatically gives my Windows box an IP (through eth2, check out the results of ifconfig above).

---

### Post by koenn on 2007-02-10
While you're at it : your 'interfaces' looks funny. 
Why does it state
```
gateway 192.168.0.1
```
which machine is 192.168.0.1 ? Why do you set it as gateway ?

---

### Post by koenn on 2007-02-10
> Ubuntu automatically gives my Windows box an IP (through eth2, check out the results of ifconfig above).
an IP address, yes, and that part is working, since you can ping between the machines. 
Your windows machine also needs a "default gateway" to know that its route to the internet passes through the ubuntubox.

Open a cmd window on the windows machine (Start : Run : cmd.exe) and show the output of
```
ipconfig /all
```

---

### Post by ihatecommies on 2007-02-10
>  	While you're at it : your 'interfaces' looks funny.
Why does it state

gateway 192.168.0.1? That's wrong with that?

> Open a cmd window on the windows machine (Start : Run : cmd.exe) and show the output of

It's in Dutch, sorry for that, but I think you will understand it:

```
Windows IP-configuratie

        Host-naam  . . . . . . . . . . . .: Dave
        Primair DNS-achtervoegsel. . . . .:
        Knooppunttype . . . . . . . . . . : gemengd
        IP-routering ingeschakeld. . . . .: nee
        WINS-proxy ingeschakeld . . . . . : nee

Ethernet-adapter LAN-verbinding:

        Verbindingsspec. DNS-achtervoegsel:
        Beschrijving . . . . . . . . . . .:
          Realtek RTL8139 Family PCI Fast Ethernet NIC
        Fysiek adres. . . . . . . . . . . : 00-50-BF-5A-15-8E
        DHCP ingeshakeld. . . . . . . . . : ja
        Autom. configuratie ingeschakeld. : ja
        IP-adres. . . . . . . . . . . . . : 192.168.0.201
        Subnetmasker. . . . . . . . . . . : 255.255.255.0
        Standaardgateway. . . . . . . . . : 192.168.0.1
        DHCP-server . . . . . . . . . . . : 192.168.0.200
        Lease verkregen . . . . . . . . . : zaterdag 10 februari 2007 22:48:13
```

---

### Post by koenn on 2007-02-10
> gateway 192.168.0.1? That's wrong with that?
At best : nothing wrong with it - it's just meaningless if you don't have a machine (computer, router, ...) somewhere with that address.

> Windows IP-configuratie

        DHCP ingeshakeld. . . . . . . . . : ja
        IP-adres. . . . . . . . . . . . . : 192.168.0.201
        **Standaardgateway. . . . . . . . . : 192.168.0.1**

Here you have that again, and in this case it's definitely wrong : your default route is through the ubuntu machine, therefore the default gateway of the Windows machine should be the ip address of eth2 on the ubuntu machine : 192.168.0.200

You could solve this with manual network configuration, but as you're already using DHCP, we could stick with that and tell the dhcp server to give out the correct gateway address. 

On the ubuntu, edit (sudo gedit) /etc/dhcp3/dhcpd.conf, look for "option routers", and make it 
```
option routers 192.168.0.200 ;
```
I think you'd have to have it in your subnet declaration, like this :
```

subnet 192.168.0.200 netmask 255.255.255.0 {
  range 192.168.0.201 192.168.0.254;
  option routers 192.168.0.200;
}
```

to activate it, 
run this on the ubuntu :
```
/etc/init.d/dhcp3-server
```
(dhcp3-server could be something else, I run a Debian for this - look for something that starts with dhcp)

then this on the windows, in a cmd window
```
ipconfig /release
ipconfig /renew
```


to test, try to ping an ip address on the internet  ( 64.233.183.99 ) - i suspect your dns is not working either so simply browsing a web site won't work yet.

---

### Post by ihatecommies on 2007-02-10
Done, I can ping back and forth, still no internet on Windows.

> At best : nothing wrong with it - it's just meaningless if you don't have a machine (computer, router, ...) somewhere with that address.

Wait, gateway is simply the place where the network card should look, right?

> to test, try to ping an ip address on the internet ( 64.233.183.99 ) - i suspect your dns is not working either so simply browsing a web site won't work yet.

Why do I need DNS for this?

---

### Post by koenn on 2007-02-10
> Done, I can ping back and forth, still no internet on Windows.
Can you be more precise ?
"ping back and forth" - do you mean between the ubuntu and the windows, or to that adress i gave you ?
"still no internet on Windows" - does that mean "with firefox and/or IE" or does it refer to that "ping an address on the internet" I gave you ?

> Wait, gateway is simply the place where the network card should look, right?  No. 
look for what ? 
(default) gateway means, for the computer : if a packet is not destined for a machine on the local network, and there is no specific route to be used, send it to the default gateway to route it to its derstination. I'm not sure this will make sense - it requires a basic understanding of TCP/IP networking

> Why do I need DNS for this?
You need it for the firefox/IE on the windows machine to translate [www.google.nl](www.google.nl) to its IP address, 64.233.183.99.  (and likewise for all other internet applications)

---

### Post by ihatecommies on 2007-02-10
> "ping back and forth" - do you mean between the ubuntu and the windows, or to that adress i gave you ?

Yes, I can ping from Ubuntu to Windows and from Windows to Ubuntu using 192.168.0.200 for Ubuntu and 192.168.0.201 for Windows.

> "still no internet on Windows" - does that mean "with firefox and/or IE" or does it refer to that "ping an address on the internet" I gave you ?

Browser.

> No.look for what ?
(default) gateway means, for the computer : if a packet is not destined for a machine on the local network, and there is no specific route to be used, send it to the default gateway to route it to its derstination. I'm not sure this will make sense - it requires a basic understanding of TCP/IP networking

That means sense, thanks.

> You need it for the firefox/IE on the windows machine to translate [www.google.nl](www.google.nl) to its IP address, 64.233.183.99. (and likewise for all other internet applications)

Okay, well, let's then set that up :).

---

### Post by koenn on 2007-02-10
> Okay, well, let's then set that up
No, first check what you have so far. 
run ipconfig /all on the windows box, verify that it says the standard gateway is 192.168.0.200

then, do that ping from the windows machine :
```
ping 64.233.183.99
```
it verifies connectivity to the internet - even without dns. (your browser can fail for at least two reasons - lack of dns or lack of connectivity, so that doesn't tell us wheter the ICS is working or not)
There's no point in working on your DNS config as long as the underlying network is not working right.

Besides, it's getting late here, and I'm getting tired.

---

### Post by ihatecommies on 2007-02-10
> run ipconfig /all on the windows box, verify that it says the standard gateway is 192.168.0.200

It does.

> then, do that ping from the windows machine :

I can't ping to that address from my Windows machine.

> Besides, it's getting late here, and I'm getting tired.

No what?

---

### Post by koenn on 2007-02-10
Is your WAN IP (Ubuntu eth0  IP address) still 80.57.193.157 ?
If so, ping it from the windows machine, and let's see what it says

---

### Post by ihatecommies on 2007-02-10
Yes it is, my IP is 80.57.193.157 and I can ping to that address from Windows.

---

### Post by koenn on 2007-02-10
At least that's something - you can reach an address in a different subnet. 
take away that "gateway 192.168.0.1" from eth2 in 'interfaces'.

Then ping again, from windows, both to your WAN IP and the google.nl address. 
If you can't ping that google address, trace the route (from windows) :

```
tracert 64.233.183.99
```

just to make sure, also post the output of the following commands (Ubuntu)
```
iptables --list
cat /proc/sys/net/ipv4/ip_forward
ls -al /etc/init.d/iptables.sh
```

---

### Post by ihatecommies on 2007-02-10
> If you can't ping that google address, trace the route (from windows)

Doesn't work.

iptables --list gives me this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

cat /proc/sys/net/ipv4/ip_forward:

```
1
```

> ls -al /etc/init.d/iptables.sh

Hmmm, I type the commands manually for now.

---

### Post by koenn on 2007-02-11
I can't see the monitors of your computers from here, so I need you to post output of those commands - they usually tell something more than "doesn't work" and I'll need to know what that is in order to pinpoint where things go wrong. 

(Windows: )
```
tracert 64.233.183.99
```
probably lists some addresses, then starts giving * * * * * . I have to see which addresses it finds (if any), and where the * * * * start. 
*you could make a screenshot or copy the output to a text file and copy it over to the ubuntu machine or so*

(Ubuntu: )
> Quote:
ls -al /etc/init.d/iptables.sh
Hmmm, I type the commands manually for now.
output of **ls -al /etc/init.d/iptables.sh** ?

(Ubuntu: ) show output of
```
sudo iptables -t nat -n --list
```

---

### Post by ihatecommies on 2007-02-11
> I can't see the monitors of your computers from here, so I need you to post output of those commands - they usually tell something more than "doesn't work" and I'll need to know what that is in order to pinpoint where things go wrong.

It says that the host is unreachable. Host unreachable = doesn't work.

I appreciate your help, but if you don't know how to do this, please, just tell me and save some time. I'm doing my best to do what you are telling me.

> probably lists some addresses, then starts giving * * * * * . I have to see which addresses it finds (if any), and where the * * * * start.
you could make a screenshot or copy the output to a text file and copy it over to the ubuntu machine or so

All it says (in Dutch) is "host unreachable".

> show output of

sudo iptables -t nat -n --list



```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        
```

---

### Post by koenn on 2007-02-11
> I appreciate your help, but if you don't know how to do this, please, just tell me and save some time. I'm doing my best to do what you are telling me.
your ICS question was basically solved in post #2. The rest is troubleshooting your network which, in all honestly, looks kinda messy.

"host unreachable" is unusual in the given circomstances. tracert should at least get a return from 192.168.0.200 - the gateway, unless the default gateway (eth2 on ubuntu) is down, or the windows box' network config has an incorrect address for default gateway - but that we already fixed yesterday.
Did anything change at either the ubuntu or the windows since then ? Can they still ping each other ?

"host unreachable" can also mean "no route found to that host', so let's check the routing table on the ubuntu 

```
route -n
```

---

### Post by ihatecommies on 2007-02-11
> Did anything change at either the ubuntu or the windows since then ?

No, nothing.

> Can they still ping each other ?

Yes I can.

> "host unreachable" can also mean "no route found to that host', so let's check the routing table on the ubuntu 

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
80.57.193.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
0.0.0.0         80.57.193.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by koenn on 2007-02-11
```
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
```

there's that **192.168.0.1** again. Where does that keep coming from ? 

I asked this before, but you never gave a definitive answer, so I'll asked it again : 
do you have a machine somewhere that has IP address 192.168.0.1 ? 

In any case, gateway 192.168.0.1 through eth2 won't work, as eth2 has 192.168.0.200, so that gateway needs to be added. 

first, clean up /etc/network/interfaces some more. If you haven't done so already, take out that 192.168.0.1 gateway address there. Also, add a network and broadcast address so there won't be mistakes about that either.
It should look something like this. 

```

auto eth2
iface eth2 inet static
    address 192.168.0.200
    netmask 255.255.255.0
    network 192.168.0.0
    gateway 192.168.0.200
    broadcast 192.168.0.255

```

run the following to make changes effective, and check that route again (+ post it in case other funny stuff shows up)
```
ifdown
ifup
route -n
```

possibly ifdown && ifup will already set the correct gateway in the routing table. If, not, we'll have to add a gateway to the table manually

---

### Post by ihatecommies on 2007-02-11
> there's that 192.168.0.1 again. Where does that keep coming from ?

It comes from /etc/network/interfaces.

> I asked this before, but you never gave a definitive answer, so I'll asked it again :
do you have a machine somewhere that has IP address 192.168.0.1 ? 

And I have told you before, no I haven't.

> In any case, gateway 192.168.0.1 through eth2 won't work, as eth2 has 192.168.0.200, so that gateway needs to be added.

first, clean up /etc/network/interfaces some more. If you haven't done so already, take out that 192.168.0.1 gateway address there. Also, add a network and broadcast address so there won't be mistakes about that either.
It should look something like this.
```
auto eth2
face eth2 inet static
address 192.168.0.200
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.200
broadcast 192.168.0.255
```


Doesn't work, it screws up my network when I set the gateway to 192.168.0.200. When restarting the network, I get this:

```
 * Reconfiguring network interfaces...                                                                                  There is already a pid file /var/run/dhclient.eth0.pid with pid 10577
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:04:76:21:7b:a6
Sending on   LPF/eth0/00:04:76:21:7b:a6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.19.128.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:04:76:21:7b:a6
Sending on   LPF/eth0/00:04:76:21:7b:a6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.19.128.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.19.128.1
bound to 80.57.193.157 -- renewal in 1645 seconds.
```

And there it hangs. So I have restored the gateway to 192.168.0.1 now, because that doesn't screw up my network, if I change it it screws up my internet connection.

---

### Post by koenn on 2007-02-11
> do you have a machine somewhere that has IP address 192.168.0.1 ?
And I have told you before, no I haven't.
Let me rephrase that then : what is the reason for your having 192.168.0.1 in a network configuration file, if that address does not exist on your network ? 

> And there it hangs. 
 my mistake - the ifdown /up should have been for eth2 only

Add this to eth2 in /etc/network/interfaces again
```
network 192.168.0.0
gateway 192.168.0.200
broadcast 192.168.0.255
```

then
```
sudo ifdown eth2
sudo ifup eth2
route -n
```

---

### Post by ihatecommies on 2007-02-11
> Let me rephrase that then : what is the reason for your having 192.168.0.1 in a network configuration file, if that address does not exist on your network ?

There are two reasons for that:

1. Because I got that from a book, the author recommend to set up my network the way I did.
2. I don't have enough networking knowledge to make a good judgment about the gateway address.

> Add this to eth2 in /etc/network/interfaces again
```
network 192.168.0.0
gateway 192.168.0.200
broadcast 192.168.0.255

```

That doesn't work, as soon as I add that gateway, refreshing the network hangs at:

```
Listening on LPF/eth0/00:04:76:21:7b:a6
Sending on   LPF/eth0/00:04:76:21:7b:a6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.19.128.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.19.128.1
bound to 80.57.193.157 -- renewal in 1709 seconds.

```

---

### Post by koenn on 2007-02-11
> 1. Because I got that from a book, the author recommend to set up my network the way I did.
You must have misunderstood that. It would only make sense on a computer such as your XP  - and then only if your router (i.e. the ubuntu) has 192.168.0.1 as IP address - which is not the case.

Anyway, 
> refreshing the network hangs at: ....
it "hangs" after **eth0** has completed receiving an ip address from your internet provider - it probably hangs because you have an **eth1** somewhere in /etc/network.innterfaces, and it's setup for dhcp - is that correct ? 
if so, you migh want to remove it or configure it for static -,at least for the time being. 

Also, it does not make sense that eth0 (and eth1) get reconfigured if you specified **eth2 **for the ifup / ifdown commands. So either you forgot to add eth2, or there's yet another unexplicable wrong setting somewhere in one of your config files - one we've yet to discover. 

I suggest you
- remove eth1 from 'interfaces', or set a static config for it
- modifiy eth2 configuration as explained before
- run ifdown eth2, ifup eth2 and route -n ; as before

if ifup / ifdown still  fail, try
```
ifconfig eth2 down
ifconfig eth2 up
route -n
```

---

### Post by ihatecommies on 2007-02-11
> it "hangs" after eth0 has completed receiving an ip address from your internet provider - it probably hangs because you have an eth1 somewhere in /etc/network.innterfaces, and it's setup for dhcp - is that correct ?

No, that is not correct. Eth1 is disabled on my computer. And my DHCP server is configured for eth2, which uses the following configuration: ```
subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.200 192.168.0.229;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.0.255;
	option routers 192.168.0.200;
}

```

> Also, it does not make sense that eth0 (and eth1) get reconfigured if you specified eth2 for the ifup / ifdown commands. So either you forgot to add eth2, or there's yet another unexplicable wrong setting somewhere in one of your config files - one we've yet to discover.

I suggest you
- remove eth1 from 'interfaces', or set a static config for it
- modifiy eth2 configuration as explained before
- run ifdown eth2, ifup eth2 and route -n ; as before

if ifup / ifdown still fail, try

```
ifconfig eth2 down
ifconfig eth2 up
route -n
```


Okay, now we have the following:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
80.57.193.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         80.57.193.1     0.0.0.0         UG    0      0        0 eth0
```

Of course, upon refreshing the network, it will still hang.

---

### Post by koenn on 2007-02-11
> No, that is not correct. Eth1 is disabled on my computer.
Well, it's obvious that eth0 gets configured OK, and eth2 has a static configuration, so what's there to hang ? 

> And my DHCP server is configured for eth2, which uses the following configuration:
That's besides the question - your dhcp server listening / giving leases on eth2 has nothing to do with eth0 (and eth1, etc.) being configured by dhcp. eth0 does not use your dhcp server, it uses your isp's dhcp server.
There's probably still something wrong in /etc/network/interfaces. Can you post it, completely ?

> 
Okay, now we have the following:

Code: ...

Of course, upon refreshing the network, it will still hang.
You've lost me there. From your feedback, I have no way of knowing which of the commands you've actually executed, which of the suggested changes to config files you actually made, and so on. All I can see is that the routing table has changed so you probably did something. That, and your prediction that 'the network will hang' - not much to go by for a next step.

Oh well,  it's bedtime again.

---

### Post by koenn on 2007-02-11
should have thought of this sooner:
just remove the gateway statement at eth2 in 'interfaces, then go through the motions (ifdown, up, route) again.

---

