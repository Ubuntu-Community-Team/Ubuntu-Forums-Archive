---
title: "Newbie at wits end - broadband problem"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by jesterz on 2005-08-13
Hi all,

I have a problem that is starting to drive me nuts.  I've installed Hoary onto an old laptop (Toshiba Satellite) - all went well.  I then went out and bought a network card for the PCMIA slot to connect up to my broadband connection via my ADSL modem.

The first time I did this - great all worked fine.  Downloaded updates and universe - looks pretty cool.   :smile: 

After that - nothing at all.  All websites just time out and any updates cannot connect.  I did not change any settings - it simply stopped being able to connect to the network.   ](*,) 

Any ideas?  Any further info I can post?

Thanks for any help you can give me.

M

---

### Post by cwaldbieser on 2005-08-13
Try posting the output of "ifconfig" and "route".  Also, can you ping an Internet address like 64.233.161.147?

---

### Post by varunus on 2005-08-13
Check the GNOME networking panel as well; are your settings still correctly stored?  Sometimes, DNS servers can get lost...

---

### Post by jesterz on 2005-08-13
Hi there,

Network settings seem all okay - DNS servers are correct.  Pinging just seems to hang waiting for a response.

Here is the output from **ifconfig**:

eth0      Link encap:Ethernet  HWaddr 00:10:60:5F:E4:47
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120 (120.0 b)  TX bytes:53010 (51.7 KiB)
          Interrupt:11 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5034833 (4.8 MiB)  TX bytes:5034833 (4.8 MiB)

and **route**:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

Thanks.

---

### Post by cwaldbieser on 2005-08-13
[QUOTE=jesterz]Hi there,

Network settings seem all okay - DNS servers are correct.  Pinging just seems to hang waiting for a response.

Here is the output from **ifconfig**:

eth0      Link encap:Ethernet  HWaddr 00:10:60:5F:E4:47
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120 (120.0 b)  TX bytes:53010 (51.7 KiB)
          Interrupt:11 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5034833 (4.8 MiB)  TX bytes:5034833 (4.8 MiB)

and **route**:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

Thanks.[/QUOTE]

Hmm.  From your settings it looks like your ADSL modem is IP address 10.1.1.1 on your side of the network, correct?  

+ Can you ping the modem (10.1.1.1)?
+ Do you have a firewall running on Ubuntu?  If you are not sure, run the following command:
```
$ sudo iptables -nL
```

this output means there is no firewall running:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

---

### Post by jesterz on 2005-08-13
[QUOTE=cwaldbieser]Hmm.  From your settings it looks like your ADSL modem is IP address 10.1.1.1 on your side of the network, correct?  

+ Can you ping the modem (10.1.1.1)?
+ Do you have a firewall running on Ubuntu?  If you are not sure, run the following command:
```
$ sudo iptables -nL
```

this output means there is no firewall running:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```[/QUOTE]



Yep I can ping the modem at 10.1.1.1 - the ave is 0.430 ms.  10.1.1.1 is also the address used by XP on my other computer - so this seems to be correct.

I've checked for a firewall on Ubuntu and no I don't have one runing - the output was the same as above.

Hope this gives you a few clues ...

---

### Post by cwaldbieser on 2005-08-13
[QUOTE=jesterz]Yep I can ping the modem at 10.1.1.1 - the ave is 0.430 ms.  10.1.1.1 is also the address used by XP on my other computer - so this seems to be correct.

I've checked for a firewall on Ubuntu and no I don't have one runing - the output was the same as above.

Hope this gives you a few clues ...[/QUOTE]

That is kinda weird.  OK, pick a web site and ping it from WinXP to get its IP address (I tend to use google).  Then do a "tracert" to that address on WinXP and a "traceroute" to that address on Ubuntu.  Where in the chain does Ubuntu seem to stop?

Also, are you using a router?  What are the physical connections for your home network?

---

### Post by jesterz on 2005-08-13
[QUOTE=cwaldbieser]That is kinda weird.  OK, pick a web site and ping it from WinXP to get its IP address (I tend to use google).  Then do a "tracert" to that address on WinXP and a "traceroute" to that address on Ubuntu.  Where in the chain does Ubuntu seem to stop?

Also, are you using a router?  What are the physical connections for your home network?[/QUOTE]

Okay, here is the output from "tracert" on XP:

```
Tracing route to 64.233.187.104 over a maximum of 30 hops

  1     *        *        *     Request timed out.
  2    51 ms   127 ms    50 ms  210-86-78-1.jetstream.xtra.co.nz [210.86.78.1]
  3    46 ms    48 ms    48 ms  210.55.205.187
  4    55 ms    56 ms    58 ms  fid-int.tkbr4.global-gateway.net.nz [202.50.245.
198]
  5    60 ms    59 ms    60 ms  vlan-283.tkbr4.global-gateway.net.nz [202.50.245
.197]
  6    58 ms    58 ms    58 ms  210.55.202.65
  7   180 ms   181 ms   182 ms  p4-5.sjbr1.global-gateway.net.nz [203.96.120.185
]
  8   183 ms   182 ms   182 ms  210.55.202.194
  9   182 ms   182 ms   185 ms  google.pabr3.global-gateway.net.nz [202.37.245.1
02]
 10   184 ms   182 ms   184 ms  66.249.94.8
 11   184 ms   184 ms   210 ms  66.249.94.162
 12   190 ms   190 ms   190 ms  216.239.49.251
 13   190 ms   190 ms   190 ms  66.249.95.95
 14   241 ms   244 ms   243 ms  216.239.47.129
 15   242 ms   244 ms   243 ms  66.249.95.124
 16   244 ms   260 ms   244 ms  216.239.46.142
 17   246 ms   246 ms   245 ms  216.239.43.154
 18   243 ms   242 ms   245 ms  64.233.187.104
```

and here is output from "traceroute" from Ubuntu:

```
1  10.1.1.48  10.1.1.48 0.918ms
2. no reply
3. no reply
...
31 no reply
```

I tried pinging this address as well and no reply - the only address I seem to be able to ping is the modem.  The modem control panel tells me that the internet is connected and working.

Finally, I'm not using a router - just a standard ADSL model (I'm literally swapping the cable over between computers at the moment).

Thanks

---

### Post by cwaldbieser on 2005-08-13
OK, now I have a clear picture of what you are doing.  One thing I noticed now going back over the info you have posted is that your "ifconfig" output doesn't seem to show a line indicating an IP address.

Do you know if you are supposed to use a static IP address or if your modem assigns it to you via DHCP?

Here is something quick you can try.  On WinXP, type "ipconfig" to get you IP address there.  Then connect the cable to Ubuntu and

```

$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 <ip-address> netmask 255.255.255.255 up
```
substitue the IP address you got from WinXP for "<ip-address>".  Now if you do an "ifconfig command, it should show that eth0's IP address is the one you just assigned.  You should be able to ping an outside address at this point.

EDIT: This might not actually be a good idea.  See my next post.

---

### Post by cwaldbieser on 2005-08-13
Acutally, I just tried my own advice, and I accidently cut myself off from the Internet.  Whoops!  It turns out I get my IP address via DHCP.  So if you are the same, you will nedd to do like me and run:

```
$ sudo dhclient
```

That should configure your IP address automatically for you and set up the routes, too.

Of course, since you are connected directly to the modem, whereas I have a router, you might need to use 
```
$ sudo pppoeconf
```
instead.

---

### Post by jesterz on 2005-08-13
[QUOTE=cwaldbieser]Acutally, I just tried my own advice, and I accidently cut myself off from the Internet.  Whoops!  It turns out I get my IP address via DHCP.  So if you are the same, you will nedd to do like me and run:

```
$ sudo dhclient
```

That should configure your IP address automatically for you and set up the routes, too.

Of course, since you are connected directly to the modem, whereas I have a router, you might need to use 
```
$ sudo pppoeconf
```
instead.[/QUOTE]

Actually tried both!  Running dhclient does seem to set things up but when I try to ping again still the same result - 100% packet loss.  I"m sure that I get my IP address via DHCP.

But still not working - any ideas on what to try next?

---

### Post by cwaldbieser on 2005-08-13
[QUOTE=jesterz]Actually tried both!  Running dhclient does seem to set things up but when I try to ping again still the same result - 100% packet loss.  I"m sure that I get my IP address via DHCP.

But still not working - any ideas on what to try next?[/QUOTE]

You could redirect the dhclient output into a file and read through it to see if there were any errors or anything that looks suspicious:

```
$ sudo dhclient > dhclient_log.txt 2>&1
```
This should redirect the output and the errors to a log file.

If that doesn't shed any light on what's going on I guess what I would try is to compare the Ubuntu settings with WinXP settings and see what is different.  "ipconfig" vs. "ifconfig", "route print" vs. "route".  Those are the basics.

The only other think I can think of is that maybe your DHCP settings need to be altered.  I don't know where the settings are in WinXP, though, so I can't tell you what to look for.  /etc/dhcp3/dhclient.conf is the config file on Ubuntu.  More than that, I don't really know.

The fact that "ifconfig" isn't showing you a line with an IP address like this:
```
eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:1C:AD  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:1cad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:131287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133809177 (127.6 MiB)  TX bytes:15700681 (14.9 MiB)

```
Makes me thing that your Ubuntu box just isn't being leased an IP address.  I wonder if your ISP is configured to only give you one per a given length of time for a particular MAC address (that is the machine address hardwired into the ethernet card-- unique to every card).  It might be that until your ISP reclaims the IP address (after say, an hour of non-use), you can't have a different NIC use the connection.

Who is your ISP?  Maybe you should give their customer support a call and ask if something like that would be a problem.  If you can pick up a cheap router for $20-$30, that might just be the way to go.  Or if you have an extra NIC lying around, you could turn one of your PCs into a router for the other.

---

### Post by jesterz on 2005-08-14
[QUOTE=cwaldbieser]You could redirect the dhclient output into a file and read through it to see if there were any errors or anything that looks suspicious:

```
$ sudo dhclient > dhclient_log.txt 2>&1
```
This should redirect the output and the errors to a log file.

If that doesn't shed any light on what's going on I guess what I would try is to compare the Ubuntu settings with WinXP settings and see what is different.  "ipconfig" vs. "ifconfig", "route print" vs. "route".  Those are the basics.

The only other think I can think of is that maybe your DHCP settings need to be altered.  I don't know where the settings are in WinXP, though, so I can't tell you what to look for.  /etc/dhcp3/dhclient.conf is the config file on Ubuntu.  More than that, I don't really know.

The fact that "ifconfig" isn't showing you a line with an IP address like this:
```
eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:1C:AD  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:1cad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:131287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133809177 (127.6 MiB)  TX bytes:15700681 (14.9 MiB)

```
Makes me thing that your Ubuntu box just isn't being leased an IP address.  I wonder if your ISP is configured to only give you one per a given length of time for a particular MAC address (that is the machine address hardwired into the ethernet card-- unique to every card).  It might be that until your ISP reclaims the IP address (after say, an hour of non-use), you can't have a different NIC use the connection.

Who is your ISP?  Maybe you should give their customer support a call and ask if something like that would be a problem.  If you can pick up a cheap router for $20-$30, that might just be the way to go.  Or if you have an extra NIC lying around, you could turn one of your PCs into a router for the other.[/QUOTE]

Here is the latest ... I have tried starting the computer and modem up from scratch and then running 'dhclient' - this seems to set things up correctly and when I run 'ifconfig' I now have a valid IP address.  Running 'ipconfig' in XP confirms that the settings are correct.

But ... still not able to ping any sites.

I will compare 'route print' and 'route' next and then get the output from dhclient.

All seems to be a bit of a mystery!

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=jesterz]Here is the latest ... I have tried starting the computer and modem up from scratch and then running 'dhclient' - this seems to set things up correctly and when I run 'ifconfig' I now have a valid IP address.  Running 'ipconfig' in XP confirms that the settings are correct.

But ... still not able to ping any sites.

I will compare 'route print' and 'route' next and then get the output from dhclient.

All seems to be a bit of a mystery![/QUOTE]
This one certainly is a puzzler!  I will be anxious to hear your results.

---

### Post by jesterz on 2005-08-19
[QUOTE=cwaldbieser]This one certainly is a puzzler!  I will be anxious to hear your results.[/QUOTE]

All sorted!!!  The problem was that the defailt gateway was not setting correctly ... I had assumed that IP was set automatically but when I switched to specifying the IP address and default gateway (i.e. the modem) it all works fine!

A big sigh of relief from me!  Thanks for all your advice on this.

 :smile:

---

