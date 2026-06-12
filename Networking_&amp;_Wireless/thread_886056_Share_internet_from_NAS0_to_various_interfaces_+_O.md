---
title: "Share internet from NAS0 to various interfaces? + Offtopic"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by PabloMDiez on 2008-08-10
Hi there! I own a Sony Ericsson K850 which installs usb0 network interface while connected.
I get internet from a damn Huawei SmartAX MT810 ADSL Modem via USB, installed as nas0.
But I also need to share to eth0, and Bluetooth PAN. And If possible, to VirtualBOX & VMWare (they work just when they want)

So

**NAS0**
Internet
Dynamic IP

it opens a

**PPP0**
Which is the same as NAS0, dynamic ip, etc.

And need to share to

**USB0**
Sony Ericsson K850i

**ETH0**
Physical network

and VMware / VirtualBOX.
VBox is working fine, don't know why and what did I do to make it work =P
VMware just don't get network, neighter with host.

What and How can I do this?

I tried so many times [this]("http://ubuntuforums.org/showthread.php?t=91370") but could'n get it working...

BTW: offtopic. Buttons on nautilus aren't working, if I press it so many times maybe it work. What can I do with this?

Excuse my english! I'm Argentinian! =)

---

### Post by SpaceTeddy on 2008-08-11
mhm - sounds like a classical inernet sharing problem. Try this [[COLOR="Blue"]howto[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") to share your internet through the ubuntu box to any other network device you want. 

if any question remains - just ask :)

---

### Post by PabloMDiez on 2008-08-11
Reinstalled Ubuntu, buttons problem gone away.

From fresh install, I followed your guide, but no success. Also tryed the "old" one, and nothing. Asked on IRC, nothing..

The worse of all is that Ubuntu receives the usb0 packets, but doesn't answers them.. =(

---

### Post by SpaceTeddy on 2008-08-11
what do you mean by "receive the usb0 packets" ??? how to do you know this ? And have you had a look at the howto ?

---

### Post by PabloMDiez on 2008-08-11
Yes, I read it..
I meant:
You know Network Monitor (Panel applet). Ok, I set up two.
One of them is for nas0 (to see my Internet activity)
And the other is for usb0 (to see if the connection with the phone is alive)

I can see that Received Packets is incrementing all the time, but Sent Packets not.
I think that there's something bad configured.. 

I tryed using Firestarter (fixing spanish bugs) but get an error while trying to share internet from NAS0/PPP0 to USB0.

Regards.

---

### Post by SpaceTeddy on 2008-08-12
ok - slowly. This should not be such a big problem - as Both network cards seems to be configured already.

I'll describe how to do a temporary setup - none of these changes will last if you reboot.

Firstly, i want you to run this command (it will turn ip forwarding on, which is needed if you want packets to pass through the machine)

```
sudo sysctl -w net.ipv4.ip_forward=1
```

Ok, now that is done, you'll need to masquerade your traffic from the internal network - so that the internet knows where to send the packets back to.
This can be done with
```
sudo iptables -A POSTROUTING --table nat -o ppp0 -j MASQUERADE
```
i am not sure if you need to use usb0 or ppp0 here - you can delete this rule again with:
```
sudo iptables -F POSTROUTING --table nat
```
and you can see the rules with:
```
sudo iptables -L POSTROUTING --table nat
```

ok - that should be it, really. 

Now, for the clients:

Make sure it's default gateway is set to your computer.
Make sure that it has the SAME DNS as your computer that is connected to the internet.
Make sure it can reach the gateway by ping and/or any other network means

If none of this works, check if you have any firewall loaded on the router.

That should be the most basic setup i can think of.

hope it helps :)

---

### Post by PabloMDiez on 2008-08-12
Still not working. I don't have any router. just a usb adsl modem.

IFCONFIG result:
```
eth0      Link encap:Ethernet  direcciónHW 00:17:31:1f:d2:0a  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:70400 (68.7 KB)  TX bytes:70400 (68.7 KB)

nas0      Link encap:Ethernet  direcciónHW 00:73:06:0f:3b:47  
          dirección inet6: fe80::273:6ff:fe0f:3b47/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:2318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2173 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2133197 (2.0 MB)  TX bytes:410415 (400.7 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:201.253.6.250  P-t-P:200.3.60.9  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:2200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2051 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:2112363 (2.0 MB)  TX bytes:339406 (331.4 KB)

usb0      Link encap:Ethernet  direcciónHW 02:80:37:1a:03:00  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::80:37ff:fe1a:300/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2758 (2.6 KB)  TX bytes:164 (164.0 B)

```

I set 192.168.0.1 as my PC IP.
Cellphone: 192.168.0.5, Gateway 192.168.0.1, DNS 208.67.220.220, Proxy: no.

I can't do any ping from the cellphone, and from the PC i don't get any responses.
What if I mount a proxy server?

---

### Post by SpaceTeddy on 2008-08-12
> **PabloMDiez said:**
> 
```
eth0      Link encap:Ethernet  direcciónHW 00:17:31:1f:d2:0a  
          inet dirección:**192.168.0.1**  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0xe000 

[..snip...]
usb0      Link encap:Ethernet  direcciónHW 02:80:37:1a:03:00  
          inet dirección:**192.168.0.1**  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::80:37ff:fe1a:300/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2758 (2.6 KB)  TX bytes:164 (164.0 B)

```

I set 192.168.0.1 as my PC IP.
Cellphone: 192.168.0.5, Gateway 192.168.0.1, DNS 208.67.220.220, Proxy: no.

that one i understood - and the config of the cell phone looks correct - but, notice the two bold ip's ? they're the same ! what means, your computer dos not know which device to use when contacting the 192.168.0.0/24 network. i guess that the usb is the dsl modem - that device does not need any ip as ppp0 is holding it. remove that ip from the usb device, or give it any other that is NOT in the 192.168.0.x range. 
example command (temporary):
```
sudo ifconfig usb0 0.0.0.0 up
```
after that, you should be able to ping the ubuntu from the mobile and vice versa
> **PabloMDiez said:**
> 
I can't do any ping from the cellphone, and from the PC i don't get any responses.
What if I mount a proxy server?
a proxy does not solve the basic connection problem. You gotta figure that one first before you can move on to the forwarding. Basic connectivity between the computers must be given for anything to work. 
So, remove the ip from usb0 and see if they can ping each other then

i hope i am on the right track :)

---

### Post by PabloMDiez on 2008-08-12
usb0 is the cellphone. eth0 is the physical network (not in use right now)
nas0 is the modem, and ppp0 is the "bridge" created for nas0.

I'll try to reset eth0 ip to another one. If it works, i'll tell you.

Thanks!

EDIT:
once shut down eth0, phone now try to download feeds when connected. ubuntu answered it with 31 packets, but can't get internet.
Maybe we are on right track =)

Now I'm trying to follow your guide again =)

EDIT2: Pinging to phone gets answered!

---

### Post by PabloMDiez on 2008-08-14
Still not working :(

---

### Post by SpaceTeddy on 2008-08-15
still not working is too little info to debug anything :(

What has changed since the last time ? can you ping the mobile from the computer now and can you ping the computer from the mobile ?
If the pinging works, where do you fail ? can you ping ip's in the internet ? can you resolve names ? what is your exact setup of the computer ad of the mobile now ?

also, i'd like you to run the following commands (again) and post the output for debug:
```
ifconfig
route -n
iptables -L -vnx
iptables -L -vnx --table nat

```

cheers

---

### Post by PabloMDiez on 2008-08-15
[QUOTE=IFCONFIG]eth0      Link encap:Ethernet  direcciónHW 00:17:31:1f:d2:0a  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1080 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:54000 (52.7 KB)  TX bytes:54000 (52.7 KB)

nas0      Link encap:Ethernet  direcciónHW 00:73:06:0f:3b:47  
          dirección inet6: fe80::273:6ff:fe0f:3b47/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:741 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:465611 (454.6 KB)  TX bytes:173062 (169.0 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:201.253.20.24  P-t-P:200.3.60.9  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:459227 (448.4 KB)  TX bytes:148675 (145.1 KB)

usb0      Link encap:Ethernet  direcciónHW 02:80:37:1a:03:00  
          inet dirección:10.8.16.1  Difusión:10.8.16.0  Máscara:255.255.255.0
          dirección inet6: fe80::80:37ff:fe1a:300/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:916 (916.0 B)  TX bytes:4372 (4.2 KB)

[/QUOTE]

[QUOTE=route -n] Command not found (something like that, I'm on Spanish Ubuntu [/QUOTE]

[QUOTE=iptables -L vnx]iptables: No chain/target/match by that name
[/QUOTE]

[QUOTE=iptables -L -vnx --table nat]
Chain PREROUTING (policy ACCEPT 17 packets, 1693 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 131115 packets, 7868036 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 MASQUERADE  all  --  *      nas0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 131109 packets, 7867646 bytes)
    pkts      bytes target     prot opt in     out     source               destination  [/QUOTE]

I don't know how to ping from phone, since it doesn't have that function included. Is there any java app or something to test it?

Mobile config:
IP: 10.8.16.2
Subnet mask: 255.0.0.0
Gateway: 10.8.16.1
DNS: 208.67.220.220
Proxy: No


Thanks!

---

### Post by SpaceTeddy on 2008-08-15
the subnetmasks of your devices don't match. i.e. usb0 is 10.8.16.1/24 while your mobile is 10.8.16.2/8. i don't know of that makes a difference, but just to be on the safe side i'd make them the same. AS for the failed commands - one is a typo from me, but the route command should have worked. 
Also, the masquerading should be set on ppp0 (as that is the device holding the internet ip) - not on the nas0. 

so, hopefully i am not doing any typos this time... i'd like you (again) to run a few commands and bring the output back :)
> sudo iptables -L -vnx
sudo /sbin/route -n
/sbin/sysctl net.ipv4.ip_forward

hopefully then i got everything together to gie detailed instructions on what to and not tell you only general things...

---

### Post by PabloMDiez on 2008-08-15
> **SpaceTeddy said:**
> the subnetmasks of your devices don't match. i.e. usb0 is 10.8.16.1/24 while your mobile is 10.8.16.2/8. i don't know of that makes a difference, but just to be on the safe side i'd make them the same. 
Fixed.

> **SpaceTeddy said:**
> AS for the failed commands - one is a typo from me, but the route command should have worked. 
 Now route works. I don't know why that didn't worked before..

> **SpaceTeddy said:**
> Also, the masquerading should be set on ppp0 (as that is the device holding the internet ip) - not on the nas0. 
Set.

> **SpaceTeddy said:**
> so, hopefully i am not doing any typos this time... i'd like you (again) to run a few commands and bring the output back :) Not a problem. Here it is =)

[QUOTE=iptables -L -vnx]Chain INPUT (policy ACCEPT 330846 packets, 100380643 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 3 packets, 195 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 312119 packets, 17613557 bytes)
    pkts      bytes target     prot opt in     out     source               destination    [/QUOTE]

[QUOTE=route -n]Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
200.3.60.9      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
[/QUOTE]

And IP forwarding is set to 1.
> net.ipv4.ip_forward = 1


Thanks!

---

### Post by PabloMDiez on 2008-08-17
Sorry for double-posting.

Installed SLAX on my pendrive. It works fine. I can share internet from ppp0 to usb0.

I see that in ubuntu when the phone needs something from internet. the modem "data" light blinks. I think that phone packets are delivered to internet, but when a answer is received, ubuntu doesn't deliver it to phone.. Am I wrong?

Regads.

---

### Post by SpaceTeddy on 2008-08-17
yep, that is what i tbought. Why is the route for the 10.8.16.0/24 network missing on your ubuntu ? Also, if you have that suspicion, run ```
sudo tcpdump -n -i ppp0
```
on the ubuntu and see if you can figure out of that is really the case. tcpdump will print the header of ANY packet running throught that interface. Also, the missing route is really the problem, you should see the replies bouncing - as they come back to your router and get send back to the internet as there is no matching network to send them towards internally.

>  Originally Posted by route -n
Tabla de rutas IP del núcleo
Destino Pasarela Genmask Indic Métric Ref Uso Interfaz
200.3.60.9 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 ppp0

there should be an entry in here that sends looks like this:
> 10.8.16.0 0.0.0.0 255.255.255.0 U 0 0 0 usb0
One possibilty why this is missing is the fact that your phone was not plugged in when you printed this out - the other is that the usb0 device does not set the route automatically. Either way - i think i know now what commands to run to get it working. Most of those you should know, and i am probably not telling you anything new - but this is for your confimation :)
```
sudo sysctl -w net.ipv4.ip_forward=1
sudo iptables -F 
sudo iptables -F --table nat
sudo iptables -P FORWARD ACCEPT
sudo iptables -A POSTROUTING --table nat -o ppp0 -j MASQUERADE
sudo ifconfig usb0 10.8.16.1 netmask 255.255.255.0 up
sudo route add -net 10.8.16.0 netmask 255.255.255.0 dev usb0
```

Now, what does each line do:
1.) enable ip_forwarding
2.) Flush all rules from the filter chains in iptables
3.) FLush all rules from the nat chains in iptables
4.) Set the FORWARD chain to ACCEPT. This lets any paket pass through your ubuntu.
5.) Add masquerading to iptables. this will rewrite any packet leavin on ppp0 to a source of ppp0 so that packets in the interent can find their way back to you
6.) configure the usb0 interface to the proper ip-address
7.) set the route on the usb0 so that your ubuntu can find the network

that is all i can think right now - with these commands you should be able to get anything that talks ip connected to and through your ubuntu.
The configuration of your phone would be the same as you already wrote. I'll note it down anyway:
```
ip: 10.8.16.2
netmask: 255.255.255.0
gateway: 10.8.16.1
DNS: 208.67.220.220
```

DNS is an opendns server :)
so... i hope this can be convinced to work now.

---

### Post by PabloMDiez on 2008-08-17
At least!! =)

When I wrote tcpdump I could read "wap.personal.com" which is my operator wap page. So connection between PC and phone is established. But phone didn't get responsed.

So after adding a route, it worked! =)

THANKS A LOT!


BTW: When connecting using VirtualBox, SLAX and now Ubuntu can't access from phone to GMail. Why? I can access normally to other sites, but don't know!. I just need to access to my ATOM feed of my mails!

---

