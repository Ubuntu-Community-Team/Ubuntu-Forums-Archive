---
title: "Problem connecting Remote Desktop (Vinagre)"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by swarup on 2009-04-03
We have three computers in our home office, all connected to the internet and each other via a router (Kyocera KR1 mobile router). All three computers use Ubuntu. All three computers are currently on line and using the internet. But only two of the three computers can identify each other using Remote Desktop. The third computer cannot see the other two, and those two (which can see each other), cannot see the third one. 

When I open Remote Desktop in the third computer and click "connect", then "find", it does not find any other computers available to connect to. One of the other two computers' address is "john-desktop:0". So in the third computer, in a terminal window I did "vinagre john-desktop:0", and then Remote Desktop opened and gave the error message "Connection to host 'john-desktop:0' was closed". 

I already have all three computers configured (via preferences -> Remote Desktop) to allow other computers to see them via Remote Desktop.

Can someone tell me the solution, so that the third computer can see the other two and connect using Remote Desktop. Thanks!

---

### Post by yeats on 2009-04-03
Are you able to ping each station by IP/Hostname?  SSH?

---

### Post by swarup on 2009-04-03
Kindly remind me how to do it. What is the command? I have been instructed to do this in years past, but it has been a long time. One first needs to know the address in order to ping it, right? And what is "SSH"?

---

### Post by swarup on 2009-04-03
I'm sure there is a very simple solution to this. If one of you experienced folks could just give me a push in the right direction, we'll surely get this thing solved in no time. Thanks!

---

### Post by asmoore82 on 2009-04-04
A little bit of automagic is done to translate addresses on the local network for you;
for more detail on that you could see
[http://en.wikipedia.org/wiki/MDNS](http://en.wikipedia.org/wiki/MDNS) and [http://en.wikipedia.org/wiki/Bonjour_(software](http://en.wikipedia.org/wiki/Bonjour_(software))

long story short, try this in a terminal on the 3rd computer:
```
ping -c 4 john-desktop.local
vinagre john-desktop.local
```

---

### Post by asmoore82 on 2009-04-04
> **swarup said:**
> And what is "SSH"?
SSH is Secure Shell - the much preferred way of providing several
network features because it uses secure public-key cryptography

In a nutshell, you can install the openssh-server package on a machine:
```
sudo apt-get install openssh-server
```

and then any other computer on the local network can
"Places -> Connect to Server -> Service Type -> SSH" to it
and it will "Just Work"

also, secure and super-fast rsync will "Just Work" - like grsync:
```
sudo apt-get install grsync
```

---

### Post by swarup on 2009-04-04
> **asmoore82 said:**
> long story short, try this in a terminal on the 3rd computer:
```
ping -c 4 john-desktop.local
vinagre john-desktop.local
```

Here is the output:

```
:~$ ping -c 4 john-desktop.local
ping: unknown host john-desktop.local
:~$ vinagre john-desktop.local
```

Then Remote Desktop opened, and on its screen appeared "john-desktop.local:5900". I then clicked on the "connect" button, and the error message came:

> Connection to host desktop "john-desktop.local:5900" was closed

This third computer is connect via LAN to the router, while the other two (including "john-desktop") are connected via wireless. But that shouldn't matter, should it? This very same third computer has working fine with Remote Desktop in the past.

So for some reason, it did not work this time. What is my next step?

---

### Post by paradigm2 on 2009-04-04
> **swarup said:**
> Here is the output:

```
:~$ ping -c 4 john-desktop.local
ping: unknown host john-desktop.local
:~$ vinagre john-desktop.local
```

Then Remote Desktop opened, and on its screen appeared "john-desktop.local:5900". I then clicked on the "connect" button, and the error message came:



This third computer is connect via LAN to the router, while the other two (including "john-desktop") are connected via wireless. But that shouldn't matter, should it? This very same third computer has working fine with Remote Desktop in the past.

So for some reason, it did not work this time. What is my next step?

It technically should not matter that the one is connected via LAN as long as the connection goes directly into the same router which the other wireless clients are using.  If it uses another router or switch, then it might be what is called within its own subnet.

On the computer which you are NOT able to connect to, go to terminal and type:

```

ifconfig

```

And paste it here.

Then do the same on one of the other computers and also paste it here.

I suspect they may be on different subnets or at least there is some hardware in between isolating them.

Privacy Note:  This will give us your MAC, which is not a big deal but if you want to X out everything appearing right after "HWaddr" then you can do that and it will prevent that info from being given out.

---

### Post by swarup on 2009-04-04
> **paradigm2 said:**
> It technically should not matter that the one is connected via LAN as long as the connection goes directly into the same router which the other wireless clients are using.  If it uses another router or switch, then it might be what is called within its own subnet.

All three computers are connected directly to the same router-- my Kyocera KR1 router. And there are no switches or anything else that should get in the way. I've set it all up myself. And this third computer used to be able to see the other two-- I just haven't used the Remote Desktop for about three months.

> **paradigm2 said:**
> On the computer which you are NOT able to connect to, go to terminal and type:

```

ifconfig

```

And paste it here.

```
:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr xxxxxxxxxxxxx  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fed4:5990/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2817067 (2.8 MB)  TX bytes:601234 (601.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr xxxxxxxxxxxxxxxxxxxxxx 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0

```
> **paradigm2 said:**
> Then do the same on one of the other computers and also paste it here.

That will be coming up in a minute-- I'll go to the other computer now.

> **paradigm2 said:**
> :KSI suspect they may be on different subnets or at least there is some hardware in between isolating them.

I could be wrong, but I do not think there is any hardware or anything else isolating them. All three computers are connected directly to my Kyocera KR1 router.

---

### Post by swarup on 2009-04-04
> **paradigm2 said:**
> On the computer which you are NOT able to connect to, go to terminal and type:

```

ifconfig

```

And paste it here.

Then do the same on one of the other computers and also paste it here.

Here is the ifconfig for the third computer-- the one that connot see the other two.

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xxxxxxxxxxxxxxxxxxx  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe64:6a66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:252452 (246.5 KB)  TX bytes:24487 (23.9 KB)
          Base address:0xecc0 Memory:dfde0000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105000 (102.5 KB)  TX bytes:105000 (102.5 KB)
```

Now you have the ifconfig of both computers. I anxiously look forward to your thoughts-- thanks so much!

---

### Post by asmoore82 on 2009-04-04
try on the 3rd computer:
```
ping -c 4 192.168.0.100
vinagre 192.168.0.100
```

If that works, it sounds like you've disable the Avahi Service on the 3rd computer -
that is the software that does the automagic *.local name resolution.

---

### Post by swarup on 2009-04-04
> **asmoore82 said:**
> try on the 3rd computer:
```
ping -c 4 192.168.0.100
vinagre 192.168.0.100
```

If that works, it sounds like you've disable the Avahi Service on the 3rd computer -
that is the software that does the automagic *.local name resolution.

You are absolutely right!!
It is my colleague's computer, and it seems that the Avahi Service must have been disabled. Because using the address as you have it, Remote Desktop opened right up. 

Do you know have to enable the Avahi Service? If you can tell me how to re-enable it, then that should take care of the matter so he won't have to enter the address each time.  Thanks!!

Here is the terminal output, just for information:

```
:~$ ping -c 4 192.168.0.100
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
64 bytes from 192.168.0.100: icmp_seq=1 ttl=64 time=1.35 ms

64 bytes from 192.168.0.100: icmp_seq=2 ttl=64 time=2.06 ms
64 bytes from 192.168.0.100: icmp_seq=3 ttl=64 time=1.77 ms
64 bytes from 192.168.0.100: icmp_seq=4 ttl=64 time=1.46 ms

--- 192.168.0.100 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 1.357/1.663/2.063/0.279 ms
:~$ vinagre 192.168.0.100
```

---

### Post by swarup on 2009-04-04
Actually, I thought the problem was taken care of, as the first time I tried "vinagre 192.168.0.100", it promptly requested a password from me and upon giving it, in the host computer the request came for permission for a remote viewer. Upon giving permission, the host screen opened in the Remote Desktop Viewer. The screen was black, but I just thought the host must have gone into sleep mode from being idle. I assumed everything had worked fine, and thus wrote you the above post.

But now, after closing Remote Desktop when I again try to open it with "vinagre 192.168.0.100", the Remote Desktop Viewer opens, but no request for password comes and nothing happens. I cannot get the john-desktop screen to open again in the Remote Desktop viewer. 

Perhaps if we enable the Avahi software, the whole Remote Desktop will start to work properly?

---

