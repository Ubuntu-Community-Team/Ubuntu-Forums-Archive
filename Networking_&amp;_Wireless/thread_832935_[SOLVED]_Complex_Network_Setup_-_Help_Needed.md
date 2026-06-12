---
title: "[SOLVED] Complex Network Setup - Help Needed"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by bludhound on 2008-06-18
This might not be an Ubuntu question, but here goes. I'm currently trying to implement the following network setup:
[[IMG]http://img110.imageshack.us/img110/9015/networkmapdu3.th.jpg[/IMG]](http://img110.imageshack.us/my.php?image=networkmapdu3.jpg)

As I only have experience with simple router-to-clients networks, I need some information to get started on this.

1) Is bridging required in this case?

2) Can network A and network B have different local subnets (like 200.180.1.x for A, 202.191.1.x for B), and at the same time workstations from both networks can access C?

3) I've done a little experiment by connecting C to both router A and B at the same time. However, C defaulted to using B's Internet access. How to I force C to use A's Internet access instead?

I'm not very good with my words, so my questions might sound a little illogical or vague. I will provide more information as needed.

Thanks in advance for your help!

---

### Post by SpaceTeddy on 2008-06-18
this setup is neither complicated nor hard to do (at least for me) - what you have are two subnets - the one connected to A and the one connected to B. If C is a network or a lonley computer/server being connected to both networks i don't know. But here is what i (think) you need to do in other to get full connectivity (i will see C as a fill network now, NOT as a single host. This will result in slightly more rules, but nothing really to worry about).

But before i start - there are some basic things i need to know from you.
1.) what is the address pool of the networks ? 192.168.0.0/24 ? 10.0.0.0/16 ? This is not really neccessary to know, but it helps me generate the right commands for you
2.) please clarify the setup of C.
3.) how much do you know about routes ?
4.) do you know what a default gateway is ?
5.) how much do you know about port forwarding ?


OK, and here is what i *think* you need to do in order to get this working. I will assume a yes from you to the questions 3-5. If this is not the case, i can clarify later.

Step 0.)
Make sure the networks A, B and C do not **collide**. They *must* have different IP ranges, otherwise you'll get in trouble unless you use briding (which i would advise against in this case - too much hassle)

Step 1.)
Both router only have two networks attached - their own (A or b) and the shared network C.
So the first thing you need to do is add routes at the routers to the missing networks. This means, that Router A needs a Route to B via the Network C and B needs a route to A via C. Once that is setup, you should have full internal connectivity.

Step 2.) 
Network C should have a default gateway set that points to A. If in doubt, you will need to set the manually. This will ensure that hosts in C do NOT use B to go to the internet.

that's pretty much it. 
If you cannot make head or tails of what i am talking about, just answer the questions and i will try to speak proper english instead of technical gibberish...

hope it helps a little :)

---

### Post by bludhound on 2008-06-19
Thanks for the detailed reply!

1) Network A is 217.190.1.0, while Network B is 215.188.1.0 . Computer C has an IP of 217.190.1.100 on network A, and an IP of 215.188.1.100 on network B.
2) C is basically a single computer which allows network A and B to interface with each other.
3) I do know how to use the 'route' command to add or remove routes. However, I'm not very sure when it comes to subnet masks. For connecting to Network A and B, C uses a subnet mask of 255.255.255.0 .
4) From what I understand, the default gateway is the router/machine which provides access to the network, or at least in this context?
5) Port forwarding is rather new to me. The only form of port forwarding I've ever done is SSH port forwarding using the -L switch.

Currently, I've managed to connect computer C to both network A and B simultaneously, and I can ping both routers from computer C. Computer C now uses the right Internet access, which is from network A. However, from computer C, I can't ping workstations from network B though I can ping workstations from network A.

Here is my 'sudo route' output:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
217.190.1.0     *               255.255.255.0   U     0      0        0 eth0
215.188.1.0     *               255.255.255.0   U     0      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         speedtouch.lan  0.0.0.0         UG    100    0        0 eth0

```

---

### Post by SpaceTeddy on 2008-06-19
ok - this should not be too hard to do. You are almost there anyway :)

for the internal configuration, you need to do the following things:

1.) add a Route from A to B via C. This has to happen on A's default gateway (or you modify every client on the Network A). the Route you need to add is:
```
sudo route add -net 215.188.1.0 netmask 255.255.255.0 gw 217.190.1.100
```
this command will work for linux boxes, and it must be run on the A's default gateway (as i said before). What you do here is tell the default gateway to NOT send pakets for the 215.x.x.x network to the internet, but send them to C instead.

The same things need to be done on B's default gateway, but reverse:
```
sudo route add -net 217.190.1.0 netmask 255.255.255.0 gw 215.188.1.100
```

Now your network has the knowledge of where to find the other part. 

2.) enable ip_forwarding on Computer C. 
In order for C to interface between the two, you must allow ip packets to pass through the computer. You can enable ip_forwarding with this command
```
sudo sysctl -w net.ipv4.ip_forward=1
```
Unfortunately, this is los upon reboot. To make this permanent, edit the /etc/sysctl.conf and remove the # from the line marked as port_forwarding. 

3.) filters on computer C
After port forwarding is enabled, you also need to make sure that C does not block anything. For that to check, i will need some more input from you. Run these commands, which will print out your iptables configuration:
```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
```
if they are empty and the default policies are on ACCEPT, then everything is fine since all packets can pass

i think that is about all that needs to be done (for now) to make this work. The routing table of C looks fine, as it does not network A (eth0) to connect to the internet. 

Just one more question - why do you use internet ip-ranges for your internal network ? were they specificially assigned to you, or did you just guess them ?
If you just guessed them, then i would suggest you change them, as they will overwrite a (small) part of the internet. You may never notice, but if you do it will be a real bitch to debug this. 
The ranged 10.0.0.0/8 and 192.168.0.0/16 are reserved for internal networks. I'd suggest you move your networks there.

Hope it helps :)

---

### Post by bludhound on 2008-06-19
Oh, those network ranges.. I picked them randomly.

Based on your instructions, everything is working perfectly fine now. This is much simpler than I thought. Thank you so much for your help!

---

