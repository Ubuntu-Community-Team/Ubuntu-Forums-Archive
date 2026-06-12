---
title: "openvpn - 8.04 vserver - tap device - lose connection to internet vserver"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by markusr on 2008-06-18
I just installed openvpn on my vserver (ubuntu 8.04).
I tested it in tun mode - both clients were able to ping the server and the other way round although they weren't able to ping each other. I decided to not chase that matter since i wanted tap mode anyways (some old lan games).

I read different howtos including [http://openvpn.net/index.php/documentation/miscellaneous/ethernet-bridging.html](http://openvpn.net/index.php/documentation/miscellaneous/ethernet-bridging.html) but everytime a start a briding script - i am losing the internetconnection to my server (which i have to restart to get a connection again)

since i am not even at the point to work with the openvpn config file - i'll just post the openvpn bridging script that creates the tap device (other cripts - same problem)


#!/bin/bash

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################

# Define Bridge Interface
br="br0"

# Define list of TAP interfaces to be bridged,
# for example tap="tap0 tap1 tap2".
tap="tap0"

# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth0"
eth_ip="192.168.8.4"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.8.255"

for t in $tap; do
    openvpn --mktun --dev $t
done

brctl addbr $br
brctl addif $br $eth

for t in $tap; do
    brctl addif $br $t
done

for t in $tap; do
    ifconfig $t 0.0.0.0 promisc up
done

ifconfig $eth 0.0.0.0 promisc up

ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast


i tried adding

route add default gw $gw $br

but that didnt change much...


th script doesnt give me any errors - but that doesnt help much since i lose any connection (ssh ...)

Is it right that i have to use eth0? isnt it possible to create an independant virtual device?

i'd be grateful for any specific link or help
howtos are pretty much all the same


Thanks

P.S: i should be able to use tun/tap device @ my vserver (at least thats what my isp tells me)

---

### Post by SpaceTeddy on 2008-06-18
ok, if you want to play lan games, you will need the tap device. Usually, i'd advise against it, as it uses lots of bandwith, but in your case it is needed. For the record - when using the tun device and you want client to client connections - you need to add the client-to-client option to the server :)

Unfortunately, i cannot see your problem. But i think i can *guess* why you loose the internet connection. I'd say you are overwriting your network configuration somewhere or you have multiple devices that are connectied to the same network. Here is how the bridges should work.

You have your eth0 - which is your physical network card. This one is UNCONFIGURED, meaning it has NO ip-address, it is just ON. Also, it must be in promisc mode for this to work. How you can do this via a ssh connection i am not sure, as you will (at least shortly) loose connection.
Then, eth0 is added to the bridge. Once that is done, the bridge (br0) will obtain the configuration that once belonged to eth0. So, instead of eth0 being configured, you now configure br0. Make sure that only one of these devices is configured !!! if both (eth0 and br0) get configured, you are running into problems - especially if they are on the same subnet.

Noticed that i did not talk about a tap device yet ? The reason is that you should get this working first - because once this works, the rest is a piece of cake. Now you can simply create the tap device and add it to the bridge (make sure that the tap device is unconfigured and in promisc mode aswell)...

i've just realized i've been explaining the wrong thing. If i understand you correctly, you don't want an embedded client, you just want layer 2 support (for Lan games) between the clients, right ?
If that is the case, you **do not need** a bridge at all. you just need the plain tap device and the tap device...

so, if i have not confused you completly, i hope you can make some sense... otherwise, just ask, and i will try to speak more plain and more to the point. 

hope it helps (a little) :)

---

### Post by markusr on 2008-06-21
thanks for your help

thats what i thought of too, but i got confused because openvpn didnt create a tap/tap0 device

when i test openvpn in tun mode - it creates an interface tun0 automaticly

ifconfig:

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

in this mode I can ping the server via the ovpn, what tells me that the whole auth-things are working
the tun0 devices disapears when I end the server...

but when i start it in tap mode ifconfig only shows eth0 an lo
nevertheless openvpn keeps telling me "Initialization Sequence Completed" and i still can connect my clients

Sat Jun 21 10:56:37 2008 TUN/TAP device tap0 opened
Sat Jun 21 10:56:37 2008 TUN/TAP TX queue length set to 100
Sat Jun 21 10:56:37 2008 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Sat Jun 21 10:56:37 2008 Socket Buffers: R=[106496->131072] S=[106496->131072]
Sat Jun 21 10:56:37 2008 UDPv4 link local (bound): [undef]:1194
Sat Jun 21 10:56:37 2008 UDPv4 link remote: [undef]
Sat Jun 21 10:56:37 2008 MULTI: multi_init called, r=256 v=256
Sat Jun 21 10:56:37 2008 IFCONFIG POOL: base=192.168.1.2 size=9
Sat Jun 21 10:56:37 2008 IFCONFIG POOL LIST
Sat Jun 21 10:56:37 2008 Initialization Sequence Completed
...
Sat Jun 21 10:58:49 2008 84.189.103.235:50168 [client1] Peer Connection Initiated with...
...


i'll add short versions of my servertap.conf and my clienttap.conf

servertap.conf:

port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.1 255.255.255.0 192.168.1.10 192.168.1.100
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status log
verb 3


clienttap.conf

client
dev tap
proto udp

remote XXX.XXX.XXX.XXX 1194
resolv-retry infinite

nobind

ca ca.crt
cert client1.crt
key client1.key

comp-lzo
verb 3

---

### Post by SpaceTeddy on 2008-06-21
if i am informed correctly about how the tap device works your setup should not really be the way to go. the tap device is (usually) used for embedding openvpn clients into the local network - which is, what i think, not what you want to do. I think what you want a pure VPN with layer 2 support, meaning lan-games can find themselves over the VPN (which needs broadcast, which essentially means you need layer 2 support).

I've just spent about half an hour testing your setup and reading on the openvpn man page. There is only a minor flaw in it... i will post my openvpn server configuration only, as i changed nothing on the client itself... 

```
port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key  server.key
dh dh2048.pem
ifconfig-pool-persist /etc/openvpn/ipp.txt
**ifconfig 192.168.1.1 255.255.255.0**
server-bridge 192.168.1.1 255.255.255.0 192.168.1.10 192.168.1.100
keepalive 10 120
comp-lzo
persist-key
persist-tun
# status openvpn-status log
verb 3

```

the bold line is all i changed. I am not 100% sure it is even needed, but in the end, this will configure the server tap0 device and bring it up so it shows on the server. If you do not have this line, the device will not show on a generic call to [COLOR="Blue"]ifconfig[/COLOR], but will show up in a specific call to [COLOR="Blue"]ifconfig tap0[/COLOR]

otherwise, your setup should be fine. The server should come up on 192.168.1.1, and clients will be configured from 192.168.1.10 upwards. I did NOT test the broadcast ability as i do not have two free vm's at the moment, but i think this should work normally. 

Also, i would suggest that you add the following lines to your server:
```
user nobody
group nogroup
```
as you already have the persist in your config, and these directives will drop the privileges on the openvpn process meaning if it is compromised it will not grant the attack straight root rights... or it's just me being paranoid.

hope this helps (a little)

---

