---
title: "HOWTO: Using openvpn to bridge networks"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2008-04-11
[SIZE="3"]Prerequisites[/SIZE]
You should have basic knowledge of how routing works, what routes are and how to install/configure programms in ubuntu/debian. Also, some understanding about iptables helps

[SIZE="3"]Scope if this Howto[/SIZE]
This tutorial describes how network bridging can be done using openvpn to connect protected network to each other. 

The First part will focus on creating direct connections between the gateways and setting up the routing so that each network can find the others. The purpose is to simulate a trusted internal network which uses the Internet to connect. This setup will only support Layer-3 (IP) and higher routing. 

The second part will go one step further and support layer-2 (MAC) forwarding. With this, even DHCP-leases, broadcasts and games can be played over the internet by truely joining two network together to become one. However, this setup is very resource intense and should only be used in small environments.

Layout of the example network (the terms in Brackets are the shortnames i will be using during the explanation)

Network A (nA) 192.168.0.0/24
|
Router A (rA) 192.168.0.1, rA.example.net
|
Internet
|
Router B (rB) 192.168.1.1, rB.example.net
|
Network B (nB) 192.168.1.0/24

[SIZE="5"]PART 1[/SIZE]

[SIZE="3"]prerequisite[/SIZE]

Both routers rA and rB have ip forwarding enabled. If they NAT or not does not matter. Both Network go THROUGH the router to the internet. (it can be done without this, but requires more setup which is beyond the scope of this howto)

[SIZE="3"]1.) Installing openvpn[/SIZE]

first off, openvpn needs to be installed. this can be accomplished via the packet Repositories. simple do
```
sudo apt-get install openvpn
``` 
on both routers.

[SIZE="3"]2.) Creating a shared Key[/SIZE]

Since the Connection is going to be Point-to-Point from rA to rB we do not need any fancy Certificates or multiple clients. Instead, we will use a static key which both routers will have to know. We will focus on rA for now and set that one up first.
change into the /etc/openvpn directroy, and create a key which will be shared.
```
cd /etc/openvpn
sudo openvpn --genkey --secret /etc/openvpn/static.key
``` 
Once the key is generated, it is time to configure the openvpn server. I will not use the most simple configuration at the start, since we do need some extra options later on anyway.

[SIZE="3"]3.) Configuring router A[/SIZE]

first off, we need to create a new configuration in the /etc/openvpn directory which we can then start the openvpn server on. Create the file (and open an editor) with this command (i always name the files after what they are connected to. Since this is a static link to one host, i will name it after the host that the connection it to go to):
```
sudo nano /etc/openvpn/rB.example.net.conf
```

into this file, copy the following configuration:
```
dev tun0
remote **rB.example.net**
ifconfig 10.0.0.1 10.0.1.1
secret /etc/openvpn/static.key
daemon

lport 15000
rport 1194

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/rB.example.net-status.log
log-append /var/log/openvpn/rB.example.net.log

ping-restart 60
ping 20

```
The bold bits need to be changed to your acctual setting, the rest can stay the same for now. anything below the daemon can be ommited (for now) as it is tweaks, security enhanchement and setting we will need later on, but i would suggest you leave it in anyway.
This config in short does not following (line by line):
 * it will create a new network device tun0
 * it will connect to the host rB.example.net
 * tun0 will have the IP address of 10.0.0.1 - the remote partner is expected to have the IP addres 10.0.1.1
 * there is a static key to be used, found in /etc/openvpn/static.key
 * openvpn shall run as a daemon - i.e. go into the background after the connection is established
 * locally, openvpn will bind to port 15000
 * the remote server is bound to port 1194
 * openvpn shall drop its privilegdes to the user nobody
 * openvpn shall drop its group to nogroup
 * keep the static key in the memory, even upon reconnect
 * keep the tun device open, even upon reconnect
 * log status of the connetion to the given file
 * log messages to the given file
 * assume the connection to be dead if no ping was recheived for 60 seconds (trigger reconnect)
 * try to ping the remote host every 20 seconds
 
This was almost it for the openvpn, just a few minor things remain. First, the directory for the log files does not yet exist. create it and then change it's owner to nobody and group nogroup so the openvpn process can write to it
```
sudo mkdir /var/log/openvpn
sudo chown nobody.nogroup /var/log/openvpn

```

[SIZE="3"]4.) configuring rB[/SIZE]

This is going to be almost exactly the same as rA for the config file. There are just three changes to the file. 
 1.) the remote statement has to be changed to hold the fqdn of rA instead of rB
 2.) the ifconfig statement needs to be reversed, as the local IP of rA is the remote IP of rB and vice versa
 3.) the ports in rport and lport need to be swapped for the same reason the ifconfig has to be swapped.

open file for editing on rB
```
sudo nano /etc/openvpn/rA.example.net.conf
```

and put this content in:
```
dev tun0
remote **rA.example.net**
ifconfig 10.0.1.1 10.0.0.1
secret /etc/openvpn/static.key
daemon

lport 1194
rport 15000

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/rA.example.net-status.log
log-append /var/log/openvpn/rA.example.net.log

ping-restart 60
ping 20

```
remember to change the bold bit to the real name, the rest can be copied if you want to keep as close to the tutorial as possible

now, create the logging directory again and all is set for a first testrun.
```
sudo mkdir /var/log/openvpn
sudo chown nobody.nogroup /var/log/openvpn

```

Lastly, copy the static.key file from rA to rB. it has to be the same one. I would suggest you use ssh/sftp to copy this file, but how does not matter. What does matter is that you cannot, by any circumstance ever, transmit this file over an unprotected line. 

** Do not use email, ftp, http, telnet or any other unencryped channel to transfer that file. If need be, copy it to a usb drive, carry it over to rB, copy it back and format the usb drive a million times afterwards** (ok, i am overreacting)

If anyone ever get their hands onto this key, they can listen in on anything passing over the protected line - or do worse things to it. Since the VPN connection is assumed to be secure, it would pose a huge security risk if that key ever go out to anyone with less than honorable intent.

[SIZE="3"]5.) getting the firewall right[/SIZE]

If you have your own scripts for the filewall or any programm running that manages your firewall, DO NOT RUN THESE COMMANDS. I cannot take into account any configuration that was made previsouly. In that case, try to understand what i am doing, and configure your script/programm accordingly.

As for plain iptables, there are two things we need to do. First off, we need to allow connections to the ports specified in the configuration of the openvpn files. Which means, opening port 15000 (udp) on rA and 1194 (udp) on rB.

sample command for this would look like this on rA:
```
sudo su
iptables -A INPUT -p udp --sport 1194 --dport 15000 -j ACCEPT
iptables -A OUTPUT -p udp --sport 15000 --dport 1194 -j ACCEPT

```

likewise, the command would like the following on rB
```
sudo su
iptables -A INPUT -p udp --sport 15000 --dport 1194 -j ACCEPT
iptables -A OUTPUT -p udp --sport 1194 --dport 15000 -j ACCEPT

```

With these, you are able to connect the openvpn processes. However, it does not yet allow any connections to utilize this link from the attached networks.
NOTE: i have chosen the stateless approach as they are easier to understand. Even though the kernel can handle the Openvpn Connection statefull (despite the fact that we utilize udp at the moment) i thought it to be less confusing. 

[SIZE="3"]6.)firing up the connection[/SIZE]

on Both hosts, issue this command to start the openvpn connection
```
sudo /etc/init.d/openvpn start
```
in the logs, you should now see how the connection is being established. A sample log (on rA) would look like this after the connection is up:
> Thu Apr 10 11:27:35 2008 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] bui
lt on Sep 20 2007
Thu Apr 10 11:27:35 2008 TUN/TAP device tun0 opened
Thu Apr 10 11:27:35 2008 ifconfig tun0 10.0.0.1 pointopoint 10.0.1.1 mtu 1500
Thu Apr 10 11:27:35 2008 GID set to nogroup
Thu Apr 10 11:27:35 2008 UID set to nobody
Thu Apr 10 11:27:35 2008 UDPv4 link local (bound): [undef]:15000
Thu Apr 10 11:27:35 2008 UDPv4 link remote: x.x.x.x:1194
Thu Apr 10 11:27:45 2008 Peer Connection Initiated with x.x.x.x:1194
Thu Apr 10 11:27:46 2008 Initialization Sequence Completed

using ifconfig, there should be a device called tun0 now which would look like this
> someone@server:# ifconfig tun0
tun0      Protokoll:UNSPEC  Hardware Adresse 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet Adresse:10.0.0.1  P-z-P:10.0.1.1  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:100 
          RX bytes:14740 (14.3 KiB)  TX bytes:10705 (10.4 KiB)


also, from rA you should now be able to ping rB by it's internal ip address - 10.0.1.1. from rB. the same going the other direction.

**it is essential that this connection is up and running. Anything that follows now will need to reachability over this connection now. So make sure you can ping with the internal IP addresses**

[SIZE="3"]7.) Setting the Routes[/SIZE]

The Routers can now reach each other, but have yet no clue where what network lie behing them. So we need to supply some more information. This means, telling rA that the network 192.168.1.0/24 is now to be found behind the tun0 device, at the ip 10.0.1.1.
Also, we need to tell rB that the 192.168.0.0/24 network is also found on tun0 but at the ip 10.0.0.1

forteunatly, openvpn brings a nice feature for this. You only have to add the routes to the config and they will be generated upon creating the device. 

on rA, add this line to the rB.example.net 
> route 192.168.1.0 255.255.255.0 
it tells openvpn that this connection holds connectivity to the specified network. Openvpn will worry about the rest and set it up correctly.

similarly, add this line to the rA.example.net.conf on rB
> route 192.168.0.0 255.255.255.0

Now, tell the openvpn processes on Both routers to restart.
```
sudo /etc/init.d/openvpn restart
```

[SIZE="3"]8.) Allowing traffic to pass from an internal network to the other[/SIZE]

Depending on your firewall configuration, this step might not even be neccesassry. However, i'd like to point out the iptables rules needed to explicitly allow traffic to pass between the two network over the vpn connection. Again, if you have self written scripts of a programm running manageing this for you, adapt these commands to your need, and do not run them. 

These commands are run on rA and rB. in both cases, it is assumed that your internal network is attached to eth0. adapt this if needed
```
sudo su
iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

```

you should now be able to ping and access any host on nB from nA and vice versa. The Bridge us up and running, the networks have been joined via a virtual direct link between the routers.

[SIZE="5"]Part 2[/SIZE]

Most of what has been done in Part One is unsuable in the setting we are after now. We will join the two Networks, nA and nB together to use a single IP Range. Clients on either network will not be able to distinguish anymore if the remote computer is on their physical Network or on the other side of the VPN. Naturally, only one default gateway can be set in this scenario, resulting in ALL traffic going over the VPN from one to the network. **Only apply these settings if there is no other way and you understand what it means to join two networks on MAC layer!** [SIZE="3"]Consider yourself warned[/SIZE] :)

Also i must warn you - again - that this setup is only to be used with caution as it can produce a lot of unneccessary traffic between the networks. If you have already done Part 1, you can ommit step two, but must turn off the bridge setup done in part 1. it will be in the way and confuse the routing.

Only Step 2 can be taken from Part 1. All other steps have changed or they do something completly different now... so, i will start at point 1, skip point 2 and work my my way from three onwards.

[SIZE="3"]1.) Installing the neccessary tools[/SIZE]
In order to get everything working smoothly, there are a few packets which need to be installed. In Part 1, we only needed openvpn. This time, we also need the bridge-utils as well as iproute for configuring the network cards during boot.

```
sudo apt-get install openvpn bridge-utils iproute
```

[SIZE="3"]2.) Creating the Shared Key[/SIZE]
see Part 1, step 2

[SIZE="3"]3.) Bridgeing the Interfaces[/SIZE]

NOTE: doing this step can break your entire internet connecton ! Be sure you know what you are doing and you know how to UNDO the changes if neccessary. Also i would strongly suggest you test them in a non-critical environment first!!!

for now, i will assume that your internal network is bound to the network card eth1. Thus, your network card (eth1) should have the IP address 192.168.1.1. In order to get this bridge setup working, we will use the bridge control to create a device container (br0) to join a physical network card (eth1) with the the tap device of your openvpn connection (tap0). So, open then file /etc/network/interfaces and search for a configuration of the device eth1. it should look like something similar to this
> auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0


now, change where you see the eth1 into a br0. This will case a bridge to come up at boot time with the configruation of your previous configuration of eth1. After that is done, you also need to tell the bridge that it should contain the device eth1 - this can be done with the line
> bridge_ports eth1

so, when you are done with changeing the entries, your full entry for br0 should look like this
> auto br0
iface br0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        bridge_ports eth1

**make sure you have chosen the right interface. If your internal network is not bount to eth1, change any apperance of eth1 into the appropriate device**

The last thing to do is to also configure eth1 upon boot to not have any ip, but to use promisc mode and to come up so we can see/hear anything that comes in on that device. So, right after configuration of br0 we will define a new block for eth1, looking like this:
> auto eth1
iface eth1 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down


the network configuration should be done now. To really check if these settings worked you will need to reboot your machine. so, lets do exactly that. 
Once the reboot is done, first check your network devices with ifconfig - your output should now look like this

```
test:~# ifconfig
**br0**       Protokoll:Ethernet  Hardware Adresse 00:0C:29:77:B1:6A  
          inet Adresse:**192.168.1.1**  Bcast:172.16.64.255  Maske:255.255.255.0
          inet6 Adresse: fe80::20c:29ff:fe77:b16a/64 Gültigkeitsbereich:Verbindung
          **UP** BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:14239 (13.9 KiB)  TX bytes:18581 (18.1 KiB)

eth1      Protokoll:Ethernet  Hardware Adresse 00:0C:29:77:B1:6A  
          inet6 Adresse: fe80::20c:29ff:fe77:b16a/64 Gültigkeitsbereich:Verbindung
          **UP** BROADCAST RUNNING **PROMISC** MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:16409 (16.0 KiB)  TX bytes:19049 (18.6 KiB)
          Interrupt:177 Basisadresse:0x1400 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
the bold bits mark the crucial settings. br0 now has your ip address, while eth1 is unconfigured (as no ip) and is in promisc mode. Both networkcards should be marked as up. The last thing to check is if eth1 really got added to br0. This can be checked via brctl show br0 - the output should look like the following:
```
test:~# brctl show br0
bridge name     bridge id               STP enabled     interfaces
br0             8000.000c2977b16a       no              **eth0**

```

if all the settings are correct, and you run into trouble with the network connectivity, check your iptables/firestarter configuration if it is still expecting pakets on eth1 and change those rules to br0 as this is now your internal network card.

[SIZE="3"]4.) needed scripts for openvpn[/SIZE]

NOTE: part of these scripts have been taken from [here]("http://osdir.com/ml/network.openvpn.user/2003-06/msg00035.html") and [here]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/"). I also got my idea on how to make the persistant settings from those pages. Thanks goes to the original posters

When the openvpn connection comes up, we will need to add the newly created tap device to the bridge. unfortenualy openvpn does not bring any automated commands for that (as far as i know, at least), so we will need to do out own little scripts and make sure they are run when openvpn starts/stops.

first, we will create a file called up.sh which will handle the adding of the created tap device to the bridge. i think it goo to place it into the /etc/openvpn folder. so, create the file, and fill it with the following script
```
#! /bin/sh

BR=$1
DEV=$2
MTU=$3
/sbin/ifconfig $DEV mtu $MTU promisc up
/usr/sbin/brctl addif $BR $DEV

```

next is the file which will remove the tap device from the bridge. i'll call it down.sh, and it should also be placed into the /etc/openvpn folder. Content of it reads as follows:
```
#! /bin/sh

BR=$1
DEV=$2

/usr/sbin/brctl delif $BR $DEV
/sbin/ifconfig $DEV down

```

lastly, make both files exectuable with these commands (adding the +x bit)
```
sudo chmod +x /etc/openvpn/up.sh
sudo chmod +x /etc/openvpn/down.sh

```

[SIZE="3"]5.) Configuring openvpn[/SIZE]

This configuration of openvpn is very much similar to steps 3 and 4 of Part 1. There are only a few minor changed to the files. Since it was already explain what happened, i will only paste the config files for the two routes here. Again, make sure that both routers have the same static.key file and that it is transmitted securly between them:

confiuration for rA
> dev tap0
remote **rB.example.net**
secret /etc/openvpn/static.key
daemon

up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

lport 15000
rport 1194

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/rB.example.net-status.log
log-append /var/log/openvpn/rB.example.net.log

ping-restart 60
ping 20

configuration for rB
> dev tap0
remote **rA.example.net**
secret /etc/openvpn/static.key
daemon

up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

lport 1194
rport 15000

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn/rA.example.net-status.log
log-append /var/log/openvpn/rA.example.net.log

ping-restart 60
ping 20

note that the main difference is the missing of the ifconfig statement. Since we now forward on layer 2, we don't need explicit ip addresses for the tap devices anymore. Otherwise, the config files are pretty much the same. Again, anything after the daemon can be ommited. Also, make sure to change the bold bits to th fqdn of the servers to connect to.
Lastly, note the up and down commands supplied in the config. These entires will run the scripts we created in step 4 and make sure that the tap device is added to the bridge properly. if you chose a different name than br0 for your bridge, you will need to change these commands. Otherwise, leave them untouched.

[SIZE="3"]6.) starting the connection[/SIZE]

If you now start the openvpn connection, nothing should happen (except the thing loading. Check step 6 in Part 1 to see what the log output looks like).

start the connection with (on rA and rB)
```
sudo /etc/init.d/openvpn start
```

first check (on both routers) if the tap0 device got added to your bridge. Do this with the brctl show br0 command. The otuput should now look like this:
> test:~# brctl show br0
bridge name     bridge id               STP enabled     interfaces
br0             8000.000c2977b16a       no              eth0
                                                        tap0


If both bridges look like that your networks are now joined. If you place a host in nB with an address of nA , you can reach it from anywhere as if it were in nA.

Another way of testing it would mean placing a computer with the IP 192.168.2.1 in nB , placing a computer with the IP 192.168.2.2 in nA and then try to ping each other. (the IP's can of course be freely chosen).
I have chosen IP's that do not match either network (nA or nB) to show the power of the bridge. Even tho neither rA nor rB know about any 192.168.2.0/24 network, the two hosts which are in two seperate networks can ping each other over the bridge. If this works, your basic setup is complete and the bridge is working normally.

[SIZE="3"]7.) Gotchas with the bridge[/SIZE]
In general, your setup is finished here. However, i would like to point out a few gotchas that you might run into:

 a) if both, nA and nB have a working DHCP server which considers itself to be authoritive you must shut down one of them, or block any dhcp-request/lease from passing the bridge. Otherwise you might run into some very strange results, possibly not know anymore where one network ends and the other starts. ONLY have one dhcp server per network - ever
 
 b) if you wish to block pakets in uptables, you must now use the br0 device. This means you will have rules for pakets that come in and go out on the br0 device. This may sound silly, but sooner or later you will run into this problem :)
 
 c) if you have joined the network together, and you chose to have one ip-range over both networks, be aware that this will put a lot of stress on the other router. So, if you chose that nB should now go into the ip-range of nA, it would mean that any paket to the internet from nB would first travel to rA and then go to the net from there. With fast internet connection this might be possible, but especially with adsl links this i NOT a desired behaviour. 
 
I hope i made myself clear (at least a little) and that this tutorial helps some people understand how to setup a bridge (either routed or bridged) between their networks. So long, and good luck. May the pakets be with you.
[SIZE="5"]ENDE[/SIZE]

---

### Post by dissdigg on 2008-04-15
Thanks,

but,

I'm getting an error in the log on rA:

Mon Apr 14 22:11:07 2008 TCP/UDP: Incoming packet rejected from exampleB.net:64447[2], expected peer address: exampleB.net:1194 (allow this incoming source address/port by removing --remote or adding --float)



rB's log just shows it restarting after timeout:

Mon Apr 14 22:12:59 2008 Inactivity timeout (--ping-restart), restarting


I am running gutsy 7.10 on both systems, and am using the exact configs (with modified IP address, but SAME ports)

EDIT: I added "float" to the config on rA and now the vpn is working, but this doesn't seem right.

---

### Post by SpaceTeddy on 2008-04-15
> **dissdigg said:**
> EDIT: I added "float" to the config on rA and now the vpn is working, but this doesn't seem right.

if two openvpn proccesses connect, they expect the answer pakets from the host specified in the remote opention. If an ip address is given there, they expect the anwers from the ip which is supplied when doing a lookup of the hostname. If the ip's don't match, openvpn will  not accept the pakets.

Adding the float option will supress this check and thus accepting any paket which has the right signature, even if from the wrong ip-address. This option is usually used if servers are behing a nat and use port-forwarding to be rechable.

what exactly to do you mean by "it doesn't look right" ?

---

### Post by kevdog on 2008-04-15
I take it that if router A and router B are physical devices that you would forward the appropriate ports to a computer behind the router on each side.  What if you wanted to add more computers in this example? Would a similar setup work with ddwrt flashed with the OpenVPN firmware version?

---

### Post by SpaceTeddy on 2008-04-15
> **kevdog said:**
> I take it that if router A and router B are physical devices that you would forward the appropriate ports to a computer behind the router on each side.  What if you wanted to add more computers in this example? Would a similar setup work with ddwrt flashed with the OpenVPN firmware version?

the idea for this howto came into action, because i have several routers (including openWRT) all over the city which form an internal network over the internet between the routers. Currently, i am joining six different network. 4 are connected with debian etch server, one ubuntu 7.10 server and one OpenWRT: so yes, you can do it just like that. 

However, how you set this up is up to you. Since you always have the point-to-point connection, you either add intermediate host (i have one server that everyone else connections to, and any connections runs over that one server), or you would cross connect them and then set the routing accordingly. 
The tricky bit here is NOT the openvpn, but the routing. I've been wanting to use zebra to get the routing figured out by itself, but did not get around it it.

As for the forwarding - no. All routers are directly (!) connected to the internet. i do not have any port forwarding setup, as stated at the start of the howto. The reason is not that it cannot be done, but rather that getting the routes right for the internal network would either involve adding routes to every client on the network (ugly !) or adding a route to your default gateway (which gets hard to explain when there are one million different home routers out there to deal with). If the server running the openvpn IS the default gateway, this problem can be avoided all together.

i hope this answers your questions :)

---

### Post by kevdog on 2008-04-15
With this particular situation, if setup appropriately as you described, would you need an internal proxy server to access the internet, or how would this work?  Basically does this setup just setup an internal LAN only?

---

### Post by SpaceTeddy on 2008-04-15
this will only setup an internal lan - the internet is not affected by it (as long as you stick with the 192.168.0.0/16 and 10.0.0.0/8 ranges for your internal network).

Each network connected will always use their internet connection directly, the openvpn bridges will only be used if one network needs to talk to the other. There is no proxy of something else needed. 
If you want name resolution within your network (like i have it setup) you will also need to run at least one dns server - or a distributed set of internal nameservers that do the name resolution - but that is optional !

essential is - this setup will ONLY affect the internal network, does not need any further setup and does not touch the internet connection... or so it worked for me :)

[EDIT]
my routers are setup according to this [tutorial]("http://ubuntuforums.org/showthread.php?t=713874") - in other words, they use ip_forwarding/nat to connect the internet. the openvpn connections just utilize this link to create the internal network

---

### Post by SpaceTeddy on 2008-04-15
added part 2 describing how to do layer 2 (MAC) bridging of networks.
Enjoy, folks :)

---

