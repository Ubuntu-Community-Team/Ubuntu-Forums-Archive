---
title: "Problem with pptpd and internet connection sharing"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by Astigma on 2008-02-24
I didn't find any match for my problem so I decided to start new thread.

I have Xubuntu 7.10 running on my laptop. Next sentences may sound stupid but here it goes: My two computers are connected to internet through my router and now I want to route my other (Windows XP) computer's IP traffic through the laptop (Xubuntu). So basically I need to get Windows to believe that it connected to internet only through the laptop and Xubuntu to route the traffic.

I have installed pptpd to Xubuntu and I can connect to it with Windows XP VPN client but no traffic goes through the tunnel (neither through the default adapter in Windows). I guess I have to make some iptables to Xubuntu but I am not an expert in it. I have found howtos to share internet connection when you have two network adapters but now I am using the same network adapter for Windows XP to Xubuntu traffic and also for Xubuntu to Internet traffic. The only difference between those connections is that Windows XP to Xubuntu traffic is going through the pptp VPN tunnel.

So, what I have to do to get my weird system to work? Should I could create a new network interface for pptp connection in Xubuntu in able to get system to work?

---

### Post by SpaceTeddy on 2008-02-25
if you just want to use your laptop as a gateway, there is no real need to use any vpn at all... 

all you need is to set your default gateway of the winxp to the ip of the ubuntu desktop. Then enable ip_forwarding.that should be all... 

or am i misunderstanding you ?

---

### Post by Astigma on 2008-02-25
No, you are not misunderstanding me. I tried to forward the ipv4 traffic in my laptop and I set the default gateway to my laptop in Windows machine but it did not work. Somehow the laptop won't route the traffic from the internet back to my Windows machine.

The final situation I want to create is that also my friend can connect to internet through my Xubuntu server. That because our houses are connected together with 100Mbps connection and I have 100Mbps connection to internet but my friend has only 1Mbps. That is why I also tought that VPN would be good? idea but now I am not sure how to get this working.

Thank you for helping and if you or anyone else have any other/better ideas to create such a network, please help.

---

### Post by SpaceTeddy on 2008-02-25
ok... slowly... let me try to understand this

Internet <---> laptop <---> windows

is that the setup ?

or what does it look like ?

---

### Post by Astigma on 2008-02-25
Setup is almost that, but this figure would be better:

Internet
  /\
   |
  \/
Internet connection provider router <-> Friend's computer, Windows XP (CPU2)
  /\
   |
  \/
My router <-> Xubuntu (Server)
  /\
   |
  \/
My other computer, Window XP (CPU1)


As I said the connection speed between CPU1 and CPU2 (computer names from the figure) is 100 Mbps. My friend's internet connection is only 1 Mbps but my internet connection is 100 Mbps. 

Now, I want to route both CPU's IP traffic through the Xubuntu Server. Also I want to create secure LAN between CPU1 and CPU2 and here I need somekind of VPN system, am I right? This kind of system allows my friend to have 100Mbps internet connection too. Of course the routing make the connection slower but it still much faster than 1 Mbps.

In the first message I asked help for simplified situation where there is only my computer connecting to internet through the Server because if I can get it working with VPN it does not matter where the client computer locates.

---

### Post by SpaceTeddy on 2008-02-25
i am dumb... :)

i still don't get it... what do you mean by Internet connection provider router. is that a piece of hardware at your house ? something like a switch with internet connection ?
or is it that thing in the internet ?

but here is how i see it... or what i *THINK* has to be done to get it working...

take your Xubuntu box, and enable IP-Forwarding. you can set that permanently in /etc/sysctl.conf (uncomment the line which says enable ip-forwarding) or load it upon each boot with this command (need to be root for that, sudo DOES NOT work)
> echo 1 > /proc/sys/net/ipv4/ip_forward

this will let your xubuntu-box forward ip traffic. Also, in your setup, there are two connections to the router - one to the Internet connection provider router (will call it ICPR now) and one to your Computer. i would therefore assume that you have two (?) network cards in your computer which have a *different* ip subnet. If that is the case, you will need to tell your ICPR where that subnet BEHIND your xubuntu-box is to be found, since it does not know where your computer is (i.e. add a router for the subnet there). The other option is that you hide your computer behind the router. 

so, lets put some numbers in

> Internet
/\
|
\/
Internet connection provider router <-192.168.2.0/24-> Friend's computer, Windows XP (CPU2)
/\
|   192.168.0.0/24
\/
My router <-> Xubuntu (Server)
/\
| 192.168.1.0/24
\/
My other computer, Window XP (CPU1)
    

so,with these Networks, you will either have to add a router to the 192.168.1.0/24 network in your ICPR, or you have to hide the network 192.168.1.0/24 behind the Router. you can do that with iptables with 
> sudo iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE
eth0 is here the interface which is connected to the 192.168.0.0/24 network

If, by any chance, i understood something wrong, then just tell me. i'll try to adapt to the changes... :)

---

### Post by Astigma on 2008-02-25
Hmm... this is getting hard :)

Internet connection provider router is device which locates somewhere here nearby my and my friend's apartments. It is owned by our internet connection provider and we cannot make any changes to it. All apartments here connect to internet through it. So I think I can say it is device in Internet. My friend must connect to my Xubuntu server basically through the "internet" even tough we know that the connection comes only through the ICPR.

My router means my wlan/lan-router device. My both computer are connected to it (no wireless).

I don't know how to describe the setup better... 

But if I am right, I need VPN to create secure LAN between our computers because my friend has to connect to my server through the internet?

---

### Post by SpaceTeddy on 2008-02-25
AHHH... i think i understand it :) hooray for me

ok, my guess was not all that wrong, but i had a few quirks in there... i guess your router is a switch too, so it is in the same network as your Computers ?

This is what i would do.

first, you should get your VPN up and running. I am a big fan of OpenVPN, since it is fairly easy to configure and gets has good help on the internet. for a setup howto, check [this]("http://ubuntuforums.org/showthread.php?t=239219") thread. If you get stuck, i can help you there too.

after the VPN works (i.e. your friend can connect to the vpn and ping the remote computer over it), you still need to enable port forwarding with the rule from my last post.> sudo su
echo 1 > /proc/sys/net/ipv4/ip_forward

then you need to create a masquerade rule which will hide your friend behing the VPN
> sudo iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE 
and that should be all - that is the whole trick to it.

Also, if you want your friend to be "integrated" into your network (i.e. have layer 2 support to allow multicasts and broadcasts in your network) you should look at ethernet bridging with openvpn. But i would leave that until the first setup works...

---

### Post by Astigma on 2008-02-26
I did what you said and I can ping server from my other computer and vica versa. But the internet connection from my other computer doesn't go through the laptop because it is straightly connected to wlan/lan-router which is connected to internet.

How can I get Windows XP to route IP traffic through VPN tunnel? I think that when I manage to do so, system would work correctly.

EDIT:

I have tested to use push "redirect-gateway" in my OpenVPN server configs, but when I do so my other computer says "Warning: route gateway is not reachable on any active network adapters: x.y.z.5".

---

### Post by SpaceTeddy on 2008-02-26
on the windows, can you please do a
> route print

the connect the openvpn and do another
> route print

also, an > ipconfig /all would be great and a copy of your openvpn config files (server and client) - **do not put the keys here, just the conf**

thanks

---

### Post by Astigma on 2008-02-26
I am definetly getting closer. I can ping internet domains (i.e. [www.google.com](www.google.com)) now from my other computer and I am sure that those ping packets goes through the tunnel because I watched the tun0 traffic with iftop.

This is my server setting:
> port 1194
proto udp
dev tun0
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway local def1"
push "dhcp-option DNS 10.8.0.1"
client-to-client
keepalive 10 120
comp-lzo
persist-key
persist-tun

And this is my client setting:
> client
dev tun
proto udp
remote x.y.z.q 1194
resolv-retry infinite
nobind
comp-lzo
persist-key
persist-tun
mute-replay-warnings

---

### Post by SpaceTeddy on 2008-02-26
i think the dns option is wrong, or does your xubuntu server have a dns server running ?
also, use a tracert on the windos machine to see if it takes you over the vpn or directly to your router

---

### Post by yuckamuk on 2008-03-03
I'm actually running into a similar issue with pptpd. 
I want to run the server so i can VPN in with an iphone and connect to my apache server without a password (i don't think safari supports even basic auth).

all traffic is going to be forwarded through the vpn since the two servers might not be on the same LAN. 

i can auth with the server, which is good but doesn't mean much.
i can ping both ways, which is also good. i can resolve DNS requests but that's because I'm running a DNS server on the same box as the pptp server.
when i go to connect to a site i get the server not responding error.

i'm guessing this is an iptables issue.
i'm positive that ip_forwarding is set correctly.
i've flushed the iptables, and tried the masquerade command with no luck. 
when i do iptables -L nothing is listed, but i don't know if that's normal for masquerading. 

i've seen a couple scripts out there for setting up iptables with input, output and forward chains, but they haven't been working for me, does anyone have a suggestion or even a link for a good method?

---

### Post by SpaceTeddy on 2008-03-04
mhm - this is way off topic, but you might want to have a look at the output of the command
```
iptables -L --table nat
```
since masqueradeing is in the NAT table and does not show on a normal iptables -L

also, the generic command for masquerading is
```
iptables --tabe nat -A POSTROUTING -o $DEVICE -j MASQUERADE
```
where $DEVICE gets replaced by the network interface which the machine that forwards utilizes to connec to the internet itself.

---

### Post by vampirodolce on 2008-03-06
> **Astigma said:**
> I did what you said and I can ping server from my other computer and vica versa. But the internet connection from my other computer doesn't go through the laptop because it is straightly connected to wlan/lan-router which is connected to internet.

How can I get Windows XP to route IP traffic through VPN tunnel? I think that when I manage to do so, system would work correctly.

EDIT:

I have tested to use push "redirect-gateway" in my OpenVPN server configs, but when I do so my other computer says "Warning: route gateway is not reachable on any active network adapters: x.y.z.5".Have you been able to solve the issue? I have exactly the same problem. As a workaround I think we could try:
-ssh with x-forwarding inside the tunnel. We could then open Konqueror or Firefox remotely and browse from there.
-install a proxy server on the remote PC and configure the local browser to use that proxy.

But I was hoping for something easier, just NAT and routing. Any suggestions?

---

### Post by SpaceTeddy on 2008-03-06
> **vampirodolce said:**
> Have you been able to solve the issue? I have exactly the same problem. As a workaround I think we could try:
-ssh with x-forwarding inside the tunnel. We could then open Konqueror or Firefox remotely and browse from there.
-install a proxy server on the remote PC and configure the local browser to use that proxy.

But I was hoping for something easier, just NAT and routing. Any suggestions?

as a side note - when the option "redirect-gateway" is set in openvpn, it will overwrite your default gateway to go through the vpn tunnel to the other side, the only traffic that is not redirected are those to the locally connected Networks and the route to the vpn server itself.
So after you have connected to the VPN server, have a look at your routing table to see if that might be the problem - the route for the VPN server MUST NOT be attached to any VPN device...

if i get the time, i will post my setup + configs so you can see how it works for me

---

### Post by vampirodolce on 2008-03-06
I'll have a go with the option you mentioned and will get back to you.
Cheers.

---

### Post by vampirodolce on 2008-03-13
> **SpaceTeddy said:**
> as a side note - when the option "redirect-gateway" is set in openvpn, it will overwrite your default gateway to go through the vpn tunnel to the other side, the only traffic that is not redirected are those to the locally connected Networks and the route to the vpn server itself.
So after you have connected to the VPN server, have a look at your routing table to see if that might be the problem - the route for the VPN server MUST NOT be attached to any VPN device...

if i get the time, i will post my setup + configs so you can see how it works for me
Hi SpaceTeddy, I would really like to thank you... your suggestion definitely made the trick :-)
Specifically, I am using push "redirect-gateway def1" which, according to the man page, is the preferred approach.
I can now share the internet connection between the server and one or more clients.

Cheers.

---

