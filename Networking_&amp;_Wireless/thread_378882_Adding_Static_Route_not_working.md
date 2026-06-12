---
title: "Adding Static Route not working"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by rfulcher on 2007-03-07
I have read over several posts and have not been able to get this to work.  I have a server that I am setting up and am having to add a static route to our gateway.  First of all I have not idea why because I have several RedHat servers that I didn't have to add any static routs to.  Maybe someone knows how to solve the static route issue.  Anyway I can add the route from the command line with route -add.  Then everything seems to work just fine.  I then try and add it to the /etc/network/if-up.d folder with the static-routs file and as well adding the static route to the interfaces file.  Neither actually add the route when I restart the interfaces or when I restart the servers.

Any ideas..

Thanks very much for any info.

---

### Post by lloyd_b on 2007-03-07
Sorry, but I'm going to have to ask for some clarification. 

I do not understand what you mean by "having to add a static route for the gateway" - if you've got a "gateway" line in "/etc/network/interfaces", it *should* take care of everything.

It would be helpful if you could post the following:

1. The contents of "/etc/network/interfaces"
2. The output from running the "ifconfig" command.
3. The output from running the "route -n" command.

Lloyd B.

---

### Post by rfulcher on 2007-03-07
Yeah I thought so to.  When the server is setup as DHCP everything works fine.  I look at the route table and everything is ok with a route to the gateway.  When I setup the server as static, including the gateway in the interfaces file.  The actual route for the gateway goes away. 

I will retrieve the files and post them.

---

### Post by Mr. C. on 2007-03-07
Please also describe or show what your desired network looks like.

Ubuntu/Debian handle many things differently.

Static routes:

[http://www.ubuntuforums.org/showthread.php?t=234207&highlight=static-routes](http://www.ubuntuforums.org/showthread.php?t=234207&highlight=static-routes)

MrC

---

### Post by rfulcher on 2007-03-08
Here is the info from the server

interfaces file

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.17.40.228
netmask 255.255.240.0
gateway 172.170.40.1
up route add -net 0.0.0.0 netmask 255.255.240.0 gw 172.17.40.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



```


ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:19:BB:2C:33:E6  
          inet addr:172.17.40.228  Bcast:172.17.47.255  Mask:255.255.240.0
          inet6 addr: fe80::219:bbff:fe2c:33e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49803 (48.6 KiB)  TX bytes:492 (492.0 b)
          Interrupt:169 Memory:f8000000-f8011100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60000 (58.5 KiB)  TX bytes:60000 (58.5 KiB)



```

route -n : (when set to static ip)

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.17.32.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0


```


route -n : (when set to dynamic ip)
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.17.40.1     255.255.240.0   UG    0      0        0 eth0
172.17.32.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         172.17.40.1     0.0.0.0         UG    0      0        0 eth0


```

Thanks for your help.

---

### Post by lloyd_b on 2007-03-08
One thing that really jumped out at me:

```
address 172.17.40.228
netmask 255.255.240.0
gateway 172.170.40.1
```

Is that gateway *supposed* to be 172._**170**_.40.1?  I would have *expected* 172._**17**_.40.1.

I'm assuming that that's a typo.  The question is was it a typo in the post, or a typo in the interfaces file.  If the latter, then I think we've identified the problem...

Lloyd B.

---

### Post by rfulcher on 2007-03-08
lloyd_b,

Thanks for the reply.  I would love to say that the typo was just in the post.  Embarrassingly it is not.  Words and smilies can not express how stupid I feel.

Thanks so much for all the great support and replies.  Sorry to waist your time on something that I should have cough and never posted in the first place.

Thanks

P.S. I love the picture of the puppy...very funny.

---

### Post by Mr. C. on 2007-03-08
Glad its all working.  Incidentally, you do not need to install the static route:

up route add -net 0.0.0.0 netmask 255.255.240.0 gw 172.17.40.1

It will be done for you, as that's the default.

MrC

---

### Post by lloyd_b on 2007-03-08
> Thanks for the reply. I would love to say that the typo was just in the post. Embarrassingly it is not. Words and smilies can not express how stupid I feel.

Thanks so much for all the great support and replies. Sorry to waist your time on something that I should have cough and never posted in the first place.

I can't remember exactly how it goes, but there's one of the Murphy's Law type quotes that explains that an error will be immediately spotted by the first innocent bystander who looks at the problem:) 

One nice thing about these forums - there are PLENTY of innocent bystanders to immediately spot such mistakes (trust me - I speak from experience).

Lloyd B.

---

### Post by Mr. C. on 2007-03-08
Indeed.  And this is precisely why we ask that people show the actual results of commands output, rather than interpret or manually type the output.

Cheers,
MrC

---

