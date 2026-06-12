---
title: "Help with internet connection sharing in ubuntu?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-11-07
I have a small pet project going: To firewall my server. Not tremendously hard, but it is creating major headaches. I am sharing through 8.04 server edition. I have 2 network interfaces, eth0 and eth1. eth0 faces the web, and I can confirm that works, eth1 faces the other computers.

I followed this guide at this thread here:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
and it worked flawlessly. No errors, no problems of any type. 
I rebooted, and I went to connect through another one of my computers, and zip. Zero. Nada. Nothing. I can't ping the eth1 card (the card the computers connect through) but the computers can ping one another.

I tried to see if this was a problem with my network interfaces, so, on the gateway machine, i did:
```
root@USSR-PROXY~$ /etc/init.d/networking restart
```
I got back the following response:
```

    * Reconfiguring network interfaces....
SIOCADDRT: No such process
Failed to bring up eth1
                                                          [ OK ]

```

Does anybody know what siocaddrt is and why it is causing problems with eth1? I tried apt-get install siocaddrt, but apt found no pacakges.

---

### Post by SpaceTeddy on 2008-11-07
what is the output of
```
ifconfig
ifconfig -a
cat /etc/network/interfaces
```

The error would suggest that there is no network card called eth1...

---

### Post by SpaceTeddy on 2008-11-07
what is the output of
```
ifconfig
ifconfig -a
cat /etc/network/interfaces
```

The error would suggest that there is no network card called eth1...

---

### Post by rhcm123 on 2008-11-07
It's strange, somtimes I can ssh to the server with no problems, other times it refuses to work. I would post the results, but, as I have no way too with out hand copying...
But no, there is an iface called eth1. It's in both the /etc/network/interfaces list and it comes up when i run ifconfig.

---

### Post by rhcm123 on 2008-11-07
Never mind, I just rebooted and got the network systems working. For some reason, if you do /etc/init.d/networking restart or /etc/init.d/networking force-reload it dosent work and screws over your connection.

I shutdown, removed the eth1 card (i'm on a laptop and it's a pci card, so that was easy) rebooted, logged in, inserted the card, and as far as i can tell it's all still good, but the sharing dosent work yet.
Here are the outputs:

IFCONFIG:
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:37:70:48  
          inet addr:192.168.2.144  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe37:7048/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15562 (15.1 KB)  TX bytes:12457 (12.1 KB)
          Interrupt:20 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:09:5b:8c:68:e5  
          inet6 addr: fe80::209:5bff:fe8c:68e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:230 (230.0 B)
          Interrupt:16 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89636 (87.5 KB)  TX bytes:89636 (87.5 KB)

```

IFCONFIG -a:
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:37:70:48  
          inet addr:192.168.2.144  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe37:7048/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19678 (19.2 KB)  TX bytes:16585 (16.1 KB)
          Interrupt:20 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:09:5b:8c:68:e5  
          inet6 addr: fe80::209:5bff:fe8c:68e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:230 (230.0 B)
          Interrupt:16 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89636 (87.5 KB)  TX bytes:89636 (87.5 KB)


```

CAT:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.144
netmask 255.255.255.0
gateway 192.168.2.1

iface eth1 inet static
address 192.168.2.145
netmask 255.255.255.0
gateway 192.168.2.144


```

ANY IDEAS?

---

### Post by rhcm123 on 2008-11-07
BTW, i found these articles/threads related to SIOCADDRT, what ever that is. Apparently it's a bug in IFCONF or the default gateway systems:

[http://www.linuxquestions.org/questions/linux-networking-3/siocaddrt-no-such-process-601531/](http://www.linuxquestions.org/questions/linux-networking-3/siocaddrt-no-such-process-601531/)
[http://ubuntuforums.org/showthread.php?t=575512](http://ubuntuforums.org/showthread.php?t=575512)
[http://ubuntuforums.org/showthread.php?t=584521](http://ubuntuforums.org/showthread.php?t=584521)

The last one is particularly interesting, it gets the same error i do...

---

### Post by rhcm123 on 2008-11-07
As far as I can tell, eth0 is working, as I can access the interweb with it, but eth1 is not working, despite it being properly configured. Perhaps it is a driver error?

---

### Post by SpaceTeddy on 2008-11-08
both your network cards are in the same subnet - and worse, you have two default gateways, one of them being yourself. This cannot work !

When a computer sends a packet using ip, it looks for the "best" network to send it to. Since you have two network cards attached to the same network - which network card should your computer use to reach the internet. Furthermore, both network cards have a default gateway (network of last resource everything is send to when no other network fits) - which one to use since there are two.

You should move eth1 from 192.168.2.145 to 192.168.3.1 -> thus it will be a DIFFERENT network. Also, there should only be one default gateway - remove the one from eth1 and only leave the eth0 in. Then, reconfigure your client (attached to eth1) to use the net network (192.168.3.x) with a default gateway 192.168.3.1 and a dns server of 192.168.3.1.
Install dnsmasq on your ubuntu box with so your client can do dns lookups ```
sudo apt-get install dnsmasq
```
Since your router box does not know where the 192.168.3.x network is, it cannot send replies back to your client. to fix this, run this command:
```
iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE
```
that will "hide" the 192.168.3.x network behind the ubuntu box. 

The last step would be to acctually allow packets to be forwarded. This needs (possibly) two adjustments. 
the first one is turning ip forwarding on in the kernel. this is done by:
```
sudo sysctl -w net.ipv4.ip_forward
```
the second one is only needed if you messed around with iptables or have any kind of firewall loaded. it would be
```
sudo iptables -P FORWARD ACCEPT
```

and now your internet should be working on the client machine... or i would say. 

This is the most basic setup, and all the commands you ran are temporary (except the dnsmasq install and the network card configuration in /etc/network/interfaces). The rest needs to be made permanent later on. 
If this works, then i can tell you how to make these changed permanent.

hope it helps :)

PS: a guy gotta sleep at some point :)

---

### Post by rhcm123 on 2008-11-08
I did what you said, but it didn't work.

I set eth1 to 192.168.3.1 and deleted the default gateway entry, then restarted the interfaces.
I then set my server to 192.168.3.193 and the gateway to 192.168.3.1
and restarted those interfaces.
I connected eth1 and the server to a switch, but still, nothing.

I can't ping eth1 from the server. I can connect to the web from the gateway machine, but all the other machines on the eth1 side of the system can ping each other, but not the gateway. Got a clue why? :confused:

---

### Post by rhcm123 on 2008-11-10
<BUMP>
Sorry... still need help. :(

---

### Post by Iowan on 2008-11-10
Perhaps it would help (me, anyway) to re-establish where you stand.  The gateway machine is separate from the server?  The server is between the gateway and the clients? The other machines get their IP Addresses from DHCP  or are they static? If static, are they still in the same subnet as server (eth1)?

---

### Post by rhcm123 on 2008-11-11
> **Iowan said:**
> Perhaps it would help (me, anyway) to re-establish where you stand.  The gateway machine is separate from the server?  The server is between the gateway and the clients? The other machines get their IP Addresses from DHCP  or are they static? If static, are they still in the same subnet as server (eth1)?

Ok, i'll lay out my network for you.

-Really complex way of getting internet to server room (won't explain, know works)
-Router in server room with ip 192.168.2.2
-connected to firestarter/gateway machine of 192.168.2.144 (eth0)
-eth1 on gateway is connected to switch. eth1 is 192.168.3.1
-server ip is 192.168.3.193
-print system ip is 192.168.3.154
etc
all systems are static except for wi-fi clients

i think this answers your questions

---

### Post by SpaceTeddy on 2008-11-12
> **rhcm123 said:**
> -connected to firestarter/gateway machine of 192.168.2.144 (eth0)

firestarter ? uh-oh. This thing can mess with the firewall/fiter rules quite a lot.
Anyways... basvc connectivity has to be given before anything else can even try to work. Thus - turn off firestarter for now ! Leave everything to the default. Then try if your server can ping the gateway, and if the gateway can reach the internet. If this works, try my steps again WITHOUT turning firestarter on (it resets some defaults that i did not take care of in my commands)....

sorry for the delay in answering...

---

### Post by rhcm123 on 2008-11-12
> **SpaceTeddy said:**
> firestarter ? uh-oh. This thing can mess with the firewall/fiter rules quite a lot.
Anyways... basvc connectivity has to be given before anything else can even try to work. Thus - turn off firestarter for now ! Leave everything to the default. Then try if your server can ping the gateway, and if the gateway can reach the internet. If this works, try my steps again WITHOUT turning firestarter on (it resets some defaults that i did not take care of in my commands)....

sorry for the delay in answering...

firestarter has not yet been installed...

---

### Post by SpaceTeddy on 2008-11-13
ok, then we are back to square one. You gotta first figure out how to make the server ping the gateway - without that nothing will work. Also, make sure that the pings are not being blocked.
Any rules for blocking or filtering ports can be shown with this command
```
sudo iptables -L -vnx
```
see if that says anything about the icmp packets or if you drop/reject anything else.

Once you are sure that is not any port blocking, then see if the pinging works... what exactly can go wrong there i cannot help you with - i am not an expert on hardware or wiring issues... sorry

i know this answer is less than satisfying... but it's the only one i've got.

---

### Post by rhcm123 on 2008-11-13
> **SpaceTeddy said:**
> ok, then we are back to square one. You gotta first figure out how to make the server ping the gateway - without that nothing will work. Also, make sure that the pings are not being blocked.
Any rules for blocking or filtering ports can be shown with this command
```
sudo iptables -L -vnx
```
see if that says anything about the icmp packets or if you drop/reject anything else.

Once you are sure that is not any port blocking, then see if the pinging works... what exactly can go wrong there i cannot help you with - i am not an expert on hardware or wiring issues... sorry

i know this answer is less than satisfying... but it's the only one i've got.



Thanks for the help. I'll post the output just in case, but i don't see anything wrong:
```
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      42     3810 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      eth0    0.0.0.0/0            255.255.255.255     
     506    38838 ACCEPT     all  --  *      eth0    192.168.2.144        0.0.0.0/0           
       0        0 ACCEPT     all  --  *      eth0    192.168.2.255        0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           
root@USSR-CORE:~# iptables -L -vnx
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      42     3810 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  !lo    *       127.0.0.0/8          0.0.0.0/0           LOG flags 0 level 4 
       0        0 DROP       all  --  !lo    *       127.0.0.0/8          0.0.0.0/0           
       0        0 ACCEPT     all  --  eth0   *       0.0.0.0/0            255.255.255.255     
     826  1014760 ACCEPT     all  --  eth0   *       0.0.0.0/0            192.168.2.144       
      82    13865 ACCEPT     all  --  eth0   *       0.0.0.0/0            192.168.2.255       
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1           
      13     4137 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 
      13     4137 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      42     3810 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      eth0    0.0.0.0/0            255.255.255.255     
     539    44522 ACCEPT     all  --  *      eth0    192.168.2.144        0.0.0.0/0           
       0        0 ACCEPT     all  --  *      eth0    192.168.2.255        0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0   
```

I just can't see what is the problem :(

---

### Post by SpaceTeddy on 2008-11-14
ok - this explains a few things. There are a LOT of rules in there that should not really be existing. Acctually, my guess was that your whole iptables filter is empty (i.e. everything allowed). Obviously, it is NOT.
But... to the rules. There is nothing in your INPUT or OUTPUT that would accept anything on eth1 - it is entirely and completely dropped - your ipfilter is configured to not accept anything on eth1 - no matter what it is. Find out where these rules are from and why they are loaded... 

Ok, do my steps from a few posts back again. but, before your run them, run these commands:

```
sudo iptables -F 
sudo iptables -F --table nat
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

This will reset your iptables configuration to the standard (everything is allowed) - then try if you can ping the gateway. If so, try if it forwards packets now.
Acctually, if dnsmasq is already installed, then you only need to run these commands:

```
sudo iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE
sudo sysctl -w net.ipv4.ip_forward=1
```

lets hope this gets some progress now...

---

### Post by rhcm123 on 2008-11-16
It still isn't working. I noticed somthing, though, on my ifconfig output.
```
eth1      Link encap:Ethernet  HWaddr 00:09:5b:8c:68:e5  
          inet6 addr: fe80::209:5bff:fe8c:68e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0xa400 

```

It has no inet address! It has an inet6 address (aka ipv6) but no ipv4 adress?! What could be causing this (my server dosen't support ipv6 yet).

---

### Post by SpaceTeddy on 2008-11-17
you didn't configure it... that is what is causing it. 

1.) you edit it somehow via the gnome interface (don't ask me where, i have no idea)
2.) you set it manually with the ifconfig command. This is only temporary until you reboot, but good for testing if you don't want any permanent changed in case you screw something up.
```
sudo ifconfig eth1 192.168.3.1
```
3.) you add the proper statement to your /etc/network/interfaces
```
gksu gedit /etc/network/interfaces
```
and add
> 
auto eth1
iface eth1 inet static
address 192.168.3.1
netmask 255.255.255.0

that should do the trick. I did not include the network configuration before since i assumed that your network was already working, since you put down ip-addresses. Sorry for the confusion :)

---

### Post by rhcm123 on 2008-11-17
> **SpaceTeddy said:**
> you didn't configure it... that is what is causing it. 

1.) you edit it somehow via the gnome interface (don't ask me where, i have no idea)
2.) you set it manually with the ifconfig command. This is only temporary until you reboot, but good for testing if you don't want any permanent changed in case you screw something up.
```
sudo ifconfig eth1 192.168.3.1
```
3.) you add the proper statement to your /etc/network/interfaces
```
gksu gedit /etc/network/interfaces
```
and add


that should do the trick. I did not include the network configuration before since i assumed that your network was already working, since you put down ip-addresses. Sorry for the confusion :)

I tried everything you suggested but it still didn't work!! I'm starting to suspect a larger problem. Aargh.

Now ifconfig says eth1 does not have an ip!!! AGAIN!! I did what you said to temporarily set the address, and it said I had one then, but i still could not ping. I restarted the interfaces... nothing. i rebooted the entire machine - IP GONE!!!
what could be causing this!?!

---

### Post by SpaceTeddy on 2008-11-18
if you set the ip via ifconfig and then reboot the computer, the address is gone. If you set the ip via the interfaces you will need to restart networking. Also, restarting the network will cause any ip set via ifconfig to be reset. 

What i think is happening is that you (somehow) have your network restarting combined with your iptables. Of course nothing is working even with an IP address if your iptables rules forbit the network card to do anything... 

run
```
sudo ifconfig eth1 192.168.3.1
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F 
```

the first one will set your interface, the other four will empty out iptables. BOTH need to be set in order for the interface to work properly. Again, my assumption was wrong that you fixed the iptables problem once we identified it :(

---

### Post by rhcm123 on 2008-11-18
> **SpaceTeddy said:**
> if you set the ip via ifconfig and then reboot the computer, the address is gone. If you set the ip via the interfaces you will need to restart networking. Also, restarting the network will cause any ip set via ifconfig to be reset. 

What i think is happening is that you (somehow) have your network restarting combined with your iptables. Of course nothing is working even with an IP address if your iptables rules forbit the network card to do anything... 

run
```
sudo ifconfig eth1 192.168.3.1
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F 
```

the first one will set your interface, the other four will empty out iptables. BOTH need to be set in order for the interface to work properly. Again, my assumption was wrong that you fixed the iptables problem once we identified it :(

You, my friend, get an internet hug. It worked! I did the commands above, then i ran
```
sudo iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE

```
to get gateway working and my server can access the internet now!!!

Yay!
However, you said this was only temporary. Is there any way to make this permanent?

---

### Post by SpaceTeddy on 2008-11-19
well - the hard part is finding where the iptables get loaded. That i do not know, but i suspect/hope that this is done via /etc/network/interfaces. If you could be so kind as to check in that file if there is any preup or postup commands being run anywhere that would be the iptables. Otherwise... you're in for a search through your system why these iptables rules get loaded. As long as you do not find them, it will be pretty hard to get a stable environment that surely loads anything you need.

So, step one. Find the iptables rules and remove them from where they are loaded. You need an empty (or at leat well defined) iptables ruleset.

second - configure your networkcard via the /etc/network/interfaces. I explained earlier what you could/should put in the /etc/network/interfaces to make the ip permanent. Please remember that a change to that file is only picked up if you ifdown/ifup the device, restart networking or restart the system. 

third - i guess you have ip_forwarding already enabled, but better to check that again. In your /etc/sysctl.conf there should be a line that is described as ip_forwarding. uncomment it.
it should read as follows:
```
net.ipv4.ip_forward=1
```
this will reliably enable ip_forwarding upon booting the computer. If you've done that already, there is no need to do any changed in this step.

fourth - load the iptables - again. For that, the easiest way is to acctually make the system work and then dump the iptables into a file. To do this, make sure that all your forwarding/firewalling/filtering works as you want, and then run
```
sudo iptables-save > /etc/iptables.up.rules
```
there should now be a file in /etc/ that holds your filewall rules. 
go into your /etc/network/interfaces, and add this line to the eth1 configuration:
```
post-up iptables-restore < /etc/iptables.up.rules
```
this will load your iptables configuration upon boot right after the interface eth1 comes up.

that should be all... i think. After these changes, reboot the computer and see if everything works as expected.

cheers :)

---

### Post by rhcm123 on 2008-11-19
THANK YOU SO MUCH!!! IT Worked!!
I also figured out why my network card was not configured from /etc/network/interfaces even when i restarted networking/the computer. I forgot to put a line auto eth1 before my configuation info. I added that line, and the machine has worked through several reboots now.
THANKS FOR THE HELP!!!
:popcorn::popcorn::popcorn:

---

