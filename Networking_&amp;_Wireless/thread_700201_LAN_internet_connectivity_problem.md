---
title: "LAN internet connectivity problem"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by msferoz85 on 2008-02-18
Hello folks!'

I am using internet through a LAN. The server is Windows-based, while I have recently switched to Ubuntu. 
Now the problem is that, Firefox is the only application that is accessing internet. No other applications are able to connect to the internet. I can only ping the LAN addresses. Any internet connection don't reply to my ping requests. 

I am pretty clueless about networking (I started Linux so that I can learn something about it), but from other threads I got an idea of what commands you guys would need to see. So here is the output of some terminal commands:


```

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:13:8F:19:CD:A9  
          inet addr:192.168.0.237  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::213:8fff:fe19:cda9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34640830 (33.0 MB)  TX bytes:4822084 (4.5 MB)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139024 (135.7 KB)  TX bytes:139024 (135.7 KB)


route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0




```



Please help me with this one.

---

### Post by msferoz85 on 2008-02-18
knock knock!!

any suggestions???

---

### Post by Iowan on 2008-02-18
I'm still pretty ignorant of routing tables...
Which other apps are (not) accessing internet?  Is your IP address static - or are you using DHCP?  Does your LAN use a proxy server for internet access?  Is there a firewall?

---

### Post by msferoz85 on 2008-02-18
I can only access internet with Firefox or the "Add/Remove Programs" downloads. All other apps (pidgin, xchat, art gallery, etc are unable to connect. i can only ping the computers on my lan, but not the internet addresses like yahoo or google.

the LAN server is Windows-based, and runs through ISA client. IP is static. I hope its helps you in diagnosing the problem.

Thanks for help.

---

### Post by Iowan on 2008-02-18
I'm even less familiar w/ ISA client (How's that for a confidence booster?)
Can you ping internet by IP address? (64.233.187.99)(66.249.93.99)
(BTW, I can't ping internet from my work computer, although it accesses OK)

---

### Post by mnemosyne on 2008-02-18
Can you post the output of this command:
```
cat /etc/network/interfaces
```

---

### Post by msferoz85 on 2008-02-18
here is the out put:
```

auto lo
iface lo inet loopback




iface eth0 inet static
address 192.168.0.237
netmask 255.255.0.0
gateway 192.168.0.1

auto eth0

```

What does it tell you?? I am clueless! Just a guess: i shows my hardware, and network configuration? :confused:

---

### Post by Rogers on 2008-02-18
How about /etc/resolv.conf  ,  I don't see any DNS info.

try: nslookup google.com

---

### Post by msferoz85 on 2008-02-19
please pardon me, as i could not reply promptly because of connection problems.

cat /etc/resolv.conf responded something like the file could not be edited and stuff. my network administrator does not provide DNS, since it's not required according to him. nslookup is unable to access google or any other site. 

A recent development has been that my network devices show a new ethernet device by the name of "Avahi", but cannot access it. my route -n and ifconfig info has also changed. And I am not even able to access Internet through Firefox (AARGGHHHH!!!). 

Sorry for being unable to post the new output of these commands, since Ubuntu is not accessing Internet, and I am writing this post through Windows.

---

### Post by msferoz85 on 2008-02-19
Okie, Firefox is back on Ubuntu, and so my older output. (whew!!!) 

route -n:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```

cat /etc/rolv.conf:

```

# generated by NetworkManager, do not edit!

```


cat /etc/network/interfaces:

```

auto lo
iface lo inet loopback





iface eth0 inet static
address 192.168.0.237
netmask 255.255.0.0
gateway 192.168.0.1

```

---

### Post by msferoz85 on 2008-02-19
any idea what could be going wrong?? :confused:

---

### Post by msferoz85 on 2008-02-19
anybody home??

---

### Post by peabody on 2008-02-19
Have you tried just pining random websites such as google?

---

### Post by Iowan on 2008-02-19
My server's **resolv.conf** has the address of it's nameserver.

---

### Post by comorbid on 2008-02-20
I would like to preface this post by stating that I'm a complete Linux n00b, and know very little about networking, but I was actually having a similar problem under basically similar circumstances; I'm connected to the network @ the apartment complex in which I currently reside - it's horrible, but it's free, and it works... usually... until the middle of the day just yesterday, while I was out. I appear to have fixed it this way, so it may very well be as simple as doing the following.

System -> Administration -> Network:
[INDENT]Connections Tab:
[INDENT]Choose your connection, click the Properties button.
Disable Roaming, set configuration to DHCP.[/INDENT]
General Tab:
[INDENT]Change your hostname to workgroup.[/INDENT][/INDENT]
Reboot.

I looked around the settings window, and "workgroup" was in the Search Domains list under the DNS tab, and I decided "eh, why not?" After a good half hour of trial and error, I ended up with these settings and a working connection. I tried setting my hostname back to what it was, but that screwed it up, so I set it back to "workgroup" and now I'm back online. Also, there's no longer anything in the Search Domains list. Hopefully, I haven't done something incredibly stupid. ^_^;

Like I said, I have *no clue *why it works. However, it's working for me, so maybe it'll work for you.

Of course, if you've already done this and it's still not working, I dunno what to tell you. :/

---

### Post by msferoz85 on 2008-02-20
Interesting, comorbid! I'll just log off my windows, and do these things in my Ubuntu. 

Moreover, someone just told me that Linux closes all ports except HTTP (80, 8080, etc) for security reasons, and you need to open these ports manually. Any comments on this??

---

### Post by msferoz85 on 2008-02-20
Okie .. my MSN logged in through Pidgin! WohoooO!!! 
How?? I have NO CLUE WHATSOEVER! :P
But I have not succeeded in other applications as yet.

---

### Post by msferoz85 on 2008-02-20
Please someone help me understand this thing!! :(

---

### Post by Sim_one on 2008-06-06
Has anybody solved it? I'm in the same situation, I'm in the company cabled lan and I can only use firefox or aptitude (or apt-get).
I tried Comorbid's solution but it doesn't work for me.

If someone can help me I will appreciate it

---

