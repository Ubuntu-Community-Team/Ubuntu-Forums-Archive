---
title: "[SOLVED] Can't ping router/connect to net..."
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by ukblacknight on 2007-12-27
Hi folks,

There are similar posts to this however mine differs a little to the others.

Basically, we have a router that connects to the net (ADSL).  We've got two XP machines connected to the router and my Ubuntu machine.  The Ubuntu machine (wired), gets an IP address from the router, however I can't connect to the internet and I can't even ping the router!  The router can see my machine in it's Attached Devices list.

What's odd is that whenever I try a ping command, it says "ping: sendmsg: Operation not permitted".

```
tom@tom-desktop: ~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0
```


```
tom@tom-desktop: ~$ sudo ifdown eth0
ifdown: interface eth0 not configured
```

```
tom@tom-desktop: ~$ ifconfig eth0
eth0             Link encap: Ethernet  HWaddr 00:14:85:C8:58:CF
                  inet addr: 192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
                  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                  RX packets:33 errors:0 dropped: 0 overruns:0 frame:0
                  TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
                  collisions:0 txqueuelen:1000
                  RX bytes:6155 (6.0 KB)  TX bytes:1038 (1.0 KB)
                  Interrupt:16 Base address:0xc000

```

DNS is pointing to 192.168.0.1, which seems correct to me (although I doubt this is a DNS issue, I can't bring up the routers webpage using 192.168.0.1 in firefox).

I've come home for christmas, and was using the exact same router just on a different ISP before, and it worked flawlessly.  Then I used a usb adsl modem with usbadslmodemmanager up until we got a router.  Now it doesn't work :(

Anyone got any ideas?  Much appreciated :)

---

### Post by KCPokes on 2007-12-27
19.168.0.1 (or 192.168.1.1) would normally be your router IP address, not the IP address you'd allocate for DHCP.  What is the IP of your router and what does your routing table look like (netstat -rn)?  Compare your IP to the XP machines and I'll bet they have an IP address in the range of 192.168.0.1XX.

---

### Post by mellowd on 2007-12-27
Yeah 192.168.0.1 is your linux ip, not your router ip.

---

### Post by ukblacknight on 2007-12-27
Wrong.  The routers IP address is 192.168.0.1.  This machines IP (XP) is 192.168.0.2.  Ubuntu machine was given 192.168.0.5.

Forgot to mention, I'm dual booting with Vista, and that works fine too.

---

### Post by mellowd on 2007-12-27
Actually, ubuntu is telling you that 192.168.0.1 is your ip :

Link encap: Ethernet  HWaddr 00:14:85:C8:58:CF
                  inet addr: 192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0

That's the IP address of your ubuntu box, that means there is a misconfiguration, otherwise it would show the .5 address

---

### Post by ukblacknight on 2007-12-27
Sorry, thats my bad!! I typed out the output coz theres no way for me to pipe it to a file!  That address should be **192.168.0.5** - my apologies!!

---

### Post by mellowd on 2007-12-27
Ok, are you able to ping the router from within ubuntu?

---

### Post by ukblacknight on 2007-12-27
No.  I receive an error message:

```
ping: sendmsg: Operation not permitted
```

Running the command with sudo and pinging various other address has the same output.

---

### Post by KCPokes on 2007-12-27
Post the output of "netstat -rn".  Should be a simple routing table, but need to verify.

---

### Post by mellowd on 2007-12-27
Also, post the ouput of this:

```
route -n
```

I want to see if a default route is shown and is pointing to your router


EDIT: Which is actually the same as the previous command, no worries.

---

### Post by ukblacknight on 2007-12-27
```
tom@tom-desktop: ~$ netstat -rn
Kernel IP routeing table
Destination     Gateway          Genmask             Flags         MSS Window        irtt Iface
192.168.0.0   0.0.0.0            255.255.255.0   U                   0   0                   0   eth0
169.254.0.0   0.0.0.0            255.255.0.0       U                   0   0                   0   eht0
0.0.0.0           192.168.0.1    0.0.0.0               UG                 0   0                   0   eth0

```

apologies about formatting, I'm having to manually enter these outputs...

---

### Post by mellowd on 2007-12-27
could be a problem with your firewall. Try stopping iptables quick and see if you can pint to the net

---

### Post by mellowd on 2007-12-27
EDIT: posted twice

---

### Post by KCPokes on 2007-12-27
I agree with MellowD, seems like a firewall rule on your local machine.  Can you check your local rules, both in and out to ensure you don't have any DENY rules?

---

### Post by ukblacknight on 2007-12-27
How do I stop iptables?  Sorry to be such a n00b :)

---

### Post by ukblacknight on 2007-12-27
I checked my iptables using iptables -L and there was a list of stuff, so I flushed them with iptables -F.  This had no effect.

---

### Post by mellowd on 2007-12-27
what do you get now with a ping?

---

### Post by ukblacknight on 2007-12-27
Exactly the same result - "Operation not permitted".  Is there anything else I can check??

---

### Post by mellowd on 2007-12-27
It's odd because you have a default route, but its not allowing you to ping it. a quick google search shows me this is a iptables issue. Hmm, could you log onto the router and check if you see the ubuntu box as one of the connected devices?

---

### Post by mellowd on 2007-12-27
Are you able to ping 127.0.0.1 ?

---

### Post by ukblacknight on 2007-12-27
Yeah it's there.  The routers brand new, the port forwarding, NAT etc are all clear.

Seems odd to me, Ubuntu and the router are obviously talking otherwise I wouldn't have been assigned an IP and I wouldn't be able to see the Ubuntu machine attached to the router.

I don't have firestarter installed either.

---

### Post by mellowd on 2007-12-27
i havent configured iptables myself with firestarter, but I heard it is good. i would suggest to install it and then configure iptables using a gui, we might be able to root out the problem there

---

### Post by ukblacknight on 2007-12-27
Wtf!  I installed firestarter and it's working now!!  Pings started straight away!  Cheers for you help.  Would love to know how that fixed the solution.

How do I mark this thread Solved?

Cheers to those who helped.

---

### Post by mellowd on 2007-12-27
Firestarter might've allowed the routes. Either way, good to hear it's solved :)

---

