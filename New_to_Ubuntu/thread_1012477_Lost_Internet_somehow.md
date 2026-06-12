---
title: "Lost Internet somehow"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by wduve on 2008-12-15
All was working well with my dell insp 1501 laptop using Ubuntu 8.10 amd64 and Ndiswapper for about 3 wks and now I cannot access internet any longer. It appears that I am connected to WAP I can see packets are going in / out yet have no internet access through browser or update/insatller. Not sure what may have changed.

Any suggestions would be appreciated.
Im extremely new to linux so plz try to bear with me.

thank you

---

### Post by Tatty on 2008-12-15
can you ping somewhere?

try pinging ubuntu.com:
```
ping -c3 ubuntu.com
```


If not then try pinging your router.

---

### Post by Twilight in Zero on 2008-12-15
I am actually experiencing a very similar problem.

I can connect to my wireless network, but I have no internet access. I can go to the router's config page, but I can't even do a google search.

What's most distressing is that my brother's computer, running Windows XP, has perfectly good internet access. This is the computer I'm posting from.

What could have possibly happened?

---

### Post by ArcticWalrus on 2008-12-15
I was experiencing a similar but not that similar problem... whenever I restarted I would not be able to connect to the Internet... But when I press the power off button and hold it, log back in my Internet connects.

---

### Post by Tatty on 2008-12-15
> **Twilight in Zero said:**
> I am actually experiencing a very similar problem.

I can connect to my wireless network, but I have no internet access. I can go to the router's config page, but I can't even do a google search.

What's most distressing is that my brother's computer, running Windows XP, has perfectly good internet access. This is the computer I'm posting from.

What could have possibly happened?

Hi Twilight, It would probably be best if you started a new thread for this issue.  Although the problems sound similar, it may be that the underlying cause is different, and it could get confusing if we try to solve two issues on the same thread.

---

### Post by Twilight in Zero on 2008-12-15
> **Tatty said:**
> Hi Twilight, It would probably be best if you started a new thread for this issue.  Although the problems sound similar, it may be that the underlying cause is different, and it could get confusing if we try to solve two issues on the same thread.
I politely disagree. I shouldn't have used "similar"; it sounds like our problems are exactly the same. It could be that in helping to solve the thread creator's problem, mine could coincidentally be solved too. Besides, we don't need any more threads about the same problem.

---

### Post by Tatty on 2008-12-15
Firstly can you ping the outside world?
```
ping -c3 ubuntu.com
```

Secondly, what is the output from:
```
ifconfig
```

---

### Post by wduve on 2008-12-15
the 2 problems do sound the same to me also, the network monitor shows that i am connected to my network, assigned IP,subnet,dns 
packets moving

ping gave no results 

unfortunately i have to relog to windows and back to get here so my replys will be delayed.

---

### Post by HermanAB on 2008-12-15
Hmm, for a successful internet connection you need a number of things:
IP address
Netmask
DNS address
Gateway address
Default route


You can check things with these three commands:
$ /sbin/ifconfig

bash-3.2$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:8C:06:93:2C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20032 (19.5 KiB)  TX bytes:20032 (19.5 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-31-7A-4E-70-CA-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28912 errors:0 dropped:0 overruns:0 frame:1450
          TX packets:5169 errors:46 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:8631975 (8.2 MiB)  TX bytes:818648 (799.4 KiB)
          Interrupt:18

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:31:7A:4E
          inet addr:172.16.1.101  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe31:7a4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12649912 (12.0 MiB)  TX bytes:699031 (682.6 KiB)

bash-3.2$                                     

-------------------

and
$ /sbin/route

bash-3.2$ /sbin/route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.1.0      *               255.255.255.0   U     35     0        0 wlan0
link-local      *               255.255.0.0     U     35     0        0 wlan0
default         172.16.1.1      0.0.0.0         UG    35     0        0 wlan0
bash-3.2$


-----------

$ cat /etc/resolv.conf

bash-3.2$ cat /etc/resolv.conf
search gw3.aeronetworks.ca

nameserver 172.16.1.1
bash-3.2$           

---------------

Hope these examples help to clear things up.

Cheers,

Herman

---

### Post by wduve on 2008-12-15
I tried again no results on ping, I cant figure out ipconfig yet(tried as command...not found),is there a way to get the system to set up networking as it did when I first installed? or is that unneccessary?

---

### Post by wduve on 2008-12-15
lol still stuck in ms world IFconfig (think i need glasses):p

---

### Post by Twilight in Zero on 2008-12-15
Pinging ubuntu.com takes forever and then returns "unknown host ubuntu.com". I can, however, ping my router, at 192.168.1.1. And even visit the config page.

ifconfig returns a lot of stuff, and I can't find any practical way to get that info from my laptop to my brother's computer. I was gonna try a samba share, but that's not working either.

---

### Post by wduve on 2008-12-15
this is what returns from ifconfig and route, i dont know how to verse the resolv.conf command.

wduve@wduve-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:74:2f:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:a7:8f:9f  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fea7:8f9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30139 (30.1 KB)  TX bytes:1674 (1.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-A7-8F-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wduve@wduve-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

btw pinging router returns as action not allowed(or permitted or something along that line)

and i also failed to mention that i cant get through on a wired connection either

---

### Post by Twilight in Zero on 2008-12-15
Sorry to double post, but if I do "dmesg | grep wlan" I get two "wlan0: duplicate address detected!" messages for each time I connect to a network. I don't know if it has anything to do with the issue at hand.

EDIT: I've determined that these messages have nothing to do with it. I have a customized Hardy LiveCD installed with ndiswrapper + rtl8187 drivers, and wicd, among other customizations. My internet connection works perfectly from that LiveCD. I checked "dmesg | grep wlan", and the same message about duplicate addresses appeared.

---

### Post by Twilight in Zero on 2008-12-16
I hate bumping, but this is a pretty serious problem. Our internet connections won't magically fix themselves.

EDIT: Solved on my end. I had a bad resolv.conf. I could get internet from a custom Hardy LiveCD I made, so I got the idea to compare resolv.confs. They were totally different. So I just replaced (manually; the resolvconf program just froze) the information in the bad resolv.conf with that from the good resolv.conf. I have internet access now.

---

### Post by wduve on 2008-12-16
resolvconf wont run as its not installed on my system and I cant install at console. What should be my next step?

---

### Post by gordintoronto on 2008-12-18
> **wduve said:**
> resolvconf wont run as its not installed on my system and I cant install at console. What should be my next step?

You're not trying to run the file, you're trying to display it.  It's a text file with essential internet configuration information.

Please try again:

   cat /etc/resolv.conf

On my system, it contains two lines, 
   nameserver 111.53.48.23
   nameserver 111.53.60.10  
(Except I've changed the exact content)
Those lines point to my domain name server.  When they point to a bad location, I can't do web browsing, email or updates.

---

### Post by wduve on 2008-12-19
AHAH !
Both domain and search are blank.
Now onto finding those addresses.
 
Wish me luck !!

Thank you very much all.

---

### Post by Twilight in Zero on 2008-12-19
It's probably the ip of your router. That's what it was for me, at least. For example, 192.168.1.1.

So my /etc/resolv.conf looks like:
```
nameserver 192.168.1.1
nameserver 192.168.1.1
search myhome.westell.com
```
I don't know why I put the same nameserver twice. That's how it worked on my liveCD, so that's how I did it here. Only thing is that it breaks if I go to my university, connect to their wifi, and come home. Then I have to fix it myself.

---

### Post by wduve on 2008-12-19
So I looked at my router...came up with:

broadband ip address #s
default gateway address #s
dns servers #s

Tried these at network configuration and nothing!
are these not what I need? 

Is there a way to initiate a new auto config(whatever process configured it for me when I installed Ubuntu)?

---

### Post by Twilight in Zero on 2008-12-19
Well, what does your /etc/resolv.conf look like? Could you post it here?

---

### Post by wduve on 2008-12-20
my resolv.conf has only 2 lines:

domain 
search

(no #s following either)

Thank you

---

### Post by Peter09 on 2008-12-20
Have you a third party driver load. I am having a similar problem which I can resolve by:

Disabling the wireless driver in.

System->Admin->Hardware Drivers.

Then reboot the system and enable them again.

---

