---
title: "[SOLVED] Internet Connection Problems"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by doodah52 on 2006-11-08
I am very new to Ubuntu 6.06 just having installed it on my desktop machine (dual boot w/ Win XP).  I have tried editing '/etc/network/interfaces and 'resolv.conf' - to no avail.  I am unable to get the Internet connection to work. I have put the DNS servers in 'resolv.conf' and manually edited 'etc/network/interfaces' to include DHCP on eth0 and IP Address, Subnet Mask, and Default Gateway.  Nada, Niente, Nothing.  No Internet.  I have a motherboard with an integrated NIC equivalent (NVIDIA).  My DSL modem is a Paradyne Model 6381-A3-200.  Any help would be greatly appreciated!

---

### Post by jamesr on 2006-11-08
Lets start at the beginning how are you connected to the internet?
PC==>NIC==wire==>Router===>Modem===internet 
or
PC==>NIC==wire============>Modem===internet
also post the output of ```
sudo ifconfig
```

---

### Post by doodah52 on 2006-11-08
Thanks JamesR, here is the information (I think) you are wanting ...

'ifconfig -a' information

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:E3:D6:20
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fee3:d620/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1240 (1.2 KiB)  TX bytes:1240 (1.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

PC - NIC - Wire - Router - Internet

---

### Post by jamesr on 2006-11-08
The part> inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0 show that it seeing the router and also getting an address from the router. Could you post the output of ```
ashteq@Ashteq:~$ cat /etc/resolv.conf
search oawh2.on.xxxxxx.ca
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
ashteq@Ashteq:~$ 

``` where the addresses of xxx.xxx.xxx.xxx are the servers of your ISP. Their web page should provide these. You do not need the search address initially although does help.

You also try ```
ping www.google.com
``` which will fail but once I find the numerical address I will post and hopefully that will work.

---

### Post by doodah52 on 2006-11-09
Sorry for the delay in getting back to you. I really appreciate your assistance on this.

I was unable to get the information you requested in terminal mode.  When I pinged 'www.google.com' I received 'host not found'

Being a newbie, I hope I did this right.]](*,)

BTW:  I have also tried sudo pppoeconf, and got an error, access concentrator did not respond.

---

### Post by jamesr on 2006-11-09
The reply > When I pinged 'www.google.com' I received 'host not found'
is more or less what I expected but why were you unable to get the information that I requested was there an error or did not work at all. Also since you are using the router to access the internet you do not need to use ppoeconf. All of the access setup will within the router.

---

### Post by doodah52 on 2006-11-09
Stupid me!  I am not used to the terminal mode.  I did get some info for you:

gregg@gregg-desktop:~$ cat /etc/resolv.conf
nameserver 67.14.192.2
nameserver 67.14.192.3
gregg@gregg-desktop:~$

gregg@gregg-desktop:~$ search oawh2.on.xxxxx.ca
bash: search: command not found
gregg@gregg-desktop:~$

I hope this was done right on my part; again, I sure appreciate your help!

---

### Post by jamesr on 2006-11-09
Hi,> regg@gregg-desktop:~$ search oawh2.on.xxxxx.ca
bash: search: command not found the search line is part of the resolv.conf file and is the name of the search server on my ISP with the XXXXX changed appropriately. I have seen various comments that it is not necessary, but I have always found it necessary. I am also intrigued that you  have a duplicate entry in the nameserver list normally they are independant addresses.

---

### Post by doodah52 on 2006-11-09
That is all the information I had.  The nameservers were cut and pasted from the terminal.  I will put the search command in resolv.conf and see what happens.

Thx!


Nope, didn't work.  Thanks.

---

### Post by jamesr on 2006-11-10
Sorry about the delay but I have been very busy work wise today.

That search command is using my ISP so there is good probability that it will not work.
To confirm that the problem is with the name resolution. Try ```
sudo ping 72.14.203.99
``` This is the numerical address for google.com

---

### Post by doodah52 on 2006-11-11
No troub, you have a job to do.

Here's the output of the ping request -

PING 72.14.203.99 (72.14.203.99) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable
From 192.168.1.100 icmp_seq=6 Destination Host Unreachable
From 192.168.1.100 icmp_seq=7 Destination Host Unreachable

and so forth ...

Hope this helps figure out what's up with my connection woes.

Thanks!

---

### Post by jamesr on 2006-11-11
Hi,

Lets try pinging the router```
ping 192.168.1.255
``` What type is your router? or is a combined router and modem?

---

### Post by loclei on 2006-11-12
```

user@user-desktop:~$ ping 192.168.157.255
Do you want to ping broadcast? Then -b
user@user-desktop:~$ ping -b 192.168.157.255
WARNING: pinging broadcast address
PING 192.168.157.255 (192.168.157.255) 56(84) bytes of data.

```
it just freezes there
i connect to the internet using a proxy that is like [http://***.***.***.***:8080](http://***.***.***.***:8080)
can someone help me on this one

```

user@user-desktop:~$ ping google.com
ping: unknown host google.com

```

also my resolv.conf is 0b

---

### Post by doodah52 on 2006-11-12
Hi JamesR:

I am using a Paradyne 6381-A3-200 RBridge/Router

desktop:~$ sudo ping 192.168.1.255 -b
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

And so on ...

Thanks

---

### Post by jamesr on 2006-11-12
Hi Doodah52,

Sorry That was my fault the ping address should have been ```
192.168.1.xxx
``` where xxx would normally be 254 or 1 depending on the router but since it is a router that I do not know I could be wrong. 

Also if you are having to use a proxy address try pinging the proxy address.

Also it seems that now the resolv.conf is empty ie 0kB

---

### Post by doodah52 on 2006-11-12
Hello JamesR:

Here you go:

PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.046 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=0.043 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=0.043 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=0.043 ms


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=10 Destination Host Unreachable
From 192.168.1.100 icmp_seq=11 Destination Host Unreachable
From 192.168.1.100 icmp_seq=12 Destination Host Unreachable
From 192.168.1.100 icmp_seq=14 Destination Host Unreachable
From 192.168.1.100 icmp_seq=15 Destination Host Unreachable
From 192.168.1.100 icmp_seq=16 Destination Host Unreachable

Thanks

---

### Post by jamesr on 2006-11-12
Hi,

Did you try the proxy address?

Is not the address 192.168.1.100 your address? see the output of the ifconfig previously. 

I will be away on business for the rest of the week but I will able to access the web in the evening, Luckily the hotel has high speed and I will be taking my laptop.

I have also downloaded the manuals for your router and if I remember, I will take them with me.

---

### Post by jamesr on 2006-11-12
Hi,

Have you tried pinging the nameserver that you gave me in the resolv.conf file.

I tried```
ping 67.14.192.2
ping 67.14.192.3
```
and got following output> ashteq@Ashteq:~$ ping 67.14.192.2
PING 67.14.192.2 (67.14.192.2) 56(84) bytes of data.
64 bytes from 67.14.192.2: icmp_seq=1 ttl=45 time=67.1 ms
64 bytes from 67.14.192.2: icmp_seq=2 ttl=45 time=76.6 ms
64 bytes from 67.14.192.2: icmp_seq=3 ttl=45 time=70.5 ms
64 bytes from 67.14.192.2: icmp_seq=4 ttl=45 time=54.8 ms
64 bytes from 67.14.192.2: icmp_seq=5 ttl=45 time=58.9 ms
64 bytes from 67.14.192.2: icmp_seq=6 ttl=45 time=57.3 ms

--- 67.14.192.2 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5000ms
rtt min/avg/max/mdev = 54.845/64.255/76.617/7.808 ms
ashteq@Ashteq:~$ ping 67.14.192.3
PING 67.14.192.3 (67.14.192.3) 56(84) bytes of data.
64 bytes from 67.14.192.3: icmp_seq=1 ttl=45 time=60.8 ms
64 bytes from 67.14.192.3: icmp_seq=2 ttl=45 time=65.8 ms
64 bytes from 67.14.192.3: icmp_seq=3 ttl=45 time=55.0 ms
64 bytes from 67.14.192.3: icmp_seq=4 ttl=45 time=67.5 ms
64 bytes from 67.14.192.3: icmp_seq=5 ttl=45 time=53.3 ms
64 bytes from 67.14.192.3: icmp_seq=6 ttl=45 time=57.0 ms
64 bytes from 67.14.192.3: icmp_seq=7 ttl=45 time=56.0 ms
64 bytes from 67.14.192.3: icmp_seq=8 ttl=45 time=56.4 ms
64 bytes from 67.14.192.3: icmp_seq=9 ttl=45 time=53.4 ms

--- 67.14.192.3 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 7994ms
rtt min/avg/max/mdev = 53.376/58.429/67.584/4.922 ms
ashteq@Ashteq:~$

---

### Post by jamesr on 2006-11-12
Hi Loclei,

Normally it considered impolite to jump into a thread with a different problem even if it a similar problem. > 
Code:

user@user-desktop:~$ ping 192.168.157.255 Do you want to ping broadcast? Then -b user@user-desktop:~$ ping -b 192.168.157.255 WARNING: pinging broadcast address PING 192.168.157.255 (192.168.157.255) 56(84) bytes of data.

it just freezes there
i connect to the internet using a proxy that is like [http://***.***.***.***:8080](http://***.***.***.***:8080)
can someone help me on this one

Code:

user@user-desktop:~$ ping google.com ping: unknown host google.com

also my resolv.conf is 0bI will try and answer your queries as well. Unfortunately I may confused myself and as consequence, DooDah52 in my answers because I did not note at first this was a different problem. But I say I will try and answer your queries as well. But I need some background info ie the same as I asked DooDah52 ie output of ifconfig, network setup. Output of resolv.conf etc. If your resolv.conf is 0KB that will need resolving.

---

### Post by doodah52 on 2006-11-13
JamesR:

Road Warrior eh?  Don't miss it at all, but I wish you good luck and a safe journey.

Better luck than I have had for sure.  Here are the DNS ping results:

PING 67.14.192.2 (67.14.192.2) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable
From 192.168.1.100 icmp_seq=6 Destination Host Unreachable
From 192.168.1.100 icmp_seq=7 Destination Host Unreachable
From 192.168.1.100 icmp_seq=11 Destination Host Unreachable
From 192.168.1.100 icmp_seq=12 Destination Host Unreachable

PING 67.14.192.3 (67.14.192.3) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable
From 192.168.1.100 icmp_seq=4 Destination Host Unreachable
From 192.168.1.100 icmp_seq=6 Destination Host Unreachable
From 192.168.1.100 icmp_seq=7 Destination Host Unreachable
From 192.168.1.100 icmp_seq=8 Destination Host Unreachable

Guess I picked the wrong day to quit drinking ...

Thanks again for your help!

---

### Post by jamesr on 2006-11-13
Hi Doodah52

> Guess I picked the wrong day to quit drinking ...I know the feeling well.
I think we are not seeing the NIC properly and as a consequence :- We will have go back several stages.

This laptop is XP based so I cannot test out the code lines but I have an old klucker of a laptop with me that runs Xubuntu. I will fire it up later and check somethings on it. I have not set up wireless on it so I cannot use in this hotel for direct access of the internet.

---

### Post by doodah52 on 2006-11-14
JamesR:

Okay.  I am using an AMD64  3200+ with 1 gb of RAM.  The motherboard is a Biostar with a built-in NIC card using NVIDIA drivers.

Thanks!

G

---

### Post by jamesr on 2006-11-15
Puts all of my PCs to shame. Are you running a 64bit version or the  standard 32bit.

Sorry about the slow reply but the day has been long. As an aside I got the other  laptop to work and its network card but could not connect to the hotels wireless network. Now I do not see the hotel network. So the problem is catching. Though have to admit a lot of these hotspots are orientated to Windows XP and IE, ie the startup download.

---

### Post by doodah52 on 2006-11-15
Hi JamesR:

Any help is appreciated!!!!

Running the 32 bit version of Ubuntu.  

I have been sniffing around some of the other network connection problem threads and seeing the NIC seems to have a recurrent effect on a number of other people.  

I used to have a full head of hair ...

Thanks,

G

---

### Post by jamesr on 2006-11-15
I still have but it is grey and going white!!!

Any reason that you choose to use dapper 6.06, I know at the present I thinking seriously of reverting to Dapper on one system, it is running Ubuntu 6.10, because I have a lot of stupid problems and I am not getting any replies. It is old hardware all said and done. But I have noticed that the number of internet access problems has reduced significantly. Especially those, that are driver related.

---

### Post by UpsideDownFace on 2006-11-16
This thread is very simmilar to my difficulty with the internet.
I can ping [www.google.com](www.google.com) and get back an address like 216.239.56.104 ( but varies on different days )
If I put [www.google.com](www.google.com) in Firefox address bar it eventually says "not found", but if I put 216.239.56.104 it connects me to google, but then it won't go any further.
I have put 212.74. .66/67 into /etc/resolve.conf because that is what my isp says I use for windoze internet ( which is what I'm using for this )

---

