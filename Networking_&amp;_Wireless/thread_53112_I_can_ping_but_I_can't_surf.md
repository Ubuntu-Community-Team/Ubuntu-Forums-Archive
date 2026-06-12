---
title: "I can ping but I can't surf"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by dexter on 2005-07-30
Hey,

I installed Ubuntu about 2 weeks ago, don't have a lot of linux experience and i'm facing a network problem. I'm not able to surf (neither with Opera of Firefox) like it should. I can see some webpages partially but most webpages don't load at all. For instance [www.standaard.be](www.standaard.be) is nog visible for me, however pinging it is not a problem :
```

pieter@bart:~$ ping www.standaard.be
PING www.standaard.be (212.113.82.182) 56(84) bytes of data.
64 bytes from www.standaard.be (212.113.82.182): icmp_seq=1 ttl=54 time=20.3 ms
64 bytes from www.standaard.be (212.113.82.182): icmp_seq=2 ttl=54 time=19.7 ms
64 bytes from www.standaard.be (212.113.82.182): icmp_seq=3 ttl=54 time=19.7 ms

--- www.standaard.be ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 19.703/19.933/20.343/0.312 ms

```

When i try surfing to the IP adress i have the same problem so it is not a DNS problem. Some more info : 

```

pieter@bart:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1 0.0.0.0         UG    0      0        0 eth0
pieter@bart:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:ED:35:B8:15
          inet addr:192.168.0.116  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe35:b815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:128909 (125.8 KiB)  TX bytes:103725 (101.2 KiB)
          Interrupt:18 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20270 errors:0 dropped:0 overruns:0 frame:0
       

```

Surfing goes through a router (192.168.0.1). I have win XP installed on the same machine and internet is not a problem there. Any idea's how to get online with linux ?

---

### Post by routerstu on 2005-07-30
i have the exact same problem!!!!!!

i can ping google.com but cant use firefox to access it.  i can substitute the ip in the browser and it works, but this is not really a solution.

also are the repositories having issues?

---

### Post by dexter on 2005-07-30
[QUOTE=routerstu]i have the exact same problem!!!!!!

i can ping google.com but cant use firefox to access it.  i can substitute the ip in the browser and it works, but this is not really a solution.

also are the repositories having issues?[/QUOTE]

surfing to ip's doesn't work here, connecting to some repositories also fails

---

### Post by routerstu on 2005-07-30
so if you put 66.94.234.13 it doesnt pull up google?

for repositories, i pinged archive.ubuntu.com and security.ubuntu.com then ran apt-get update and it worked.  but only for a short time as watever is happening must also timeout this workaround

---

### Post by routerstu on 2005-07-30
after poking around, i typed dmesg at prompt looking for anything and may have found something:



pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 0c c0 c3 assigned IRQ 18.
eth0: registered as PCnet/PCI II 79C970A
pcnet32: 1 cards_found.
NET: Registered protocol family 17
ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 19
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth0: duplicate address detected!
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
mtrr: your processor doesn't support write-combining
eth0: duplicate address detected!
Disabled Privacy Extensions on device ce6e0c00(sit0)
eth0: duplicate address detected!
eth0: duplicate address detected!
admin@ubuntu:~$








what is "eth0: duplicate address detected!"


i changed ip, but i still get it?  is it mac address related?

again this is all under vmware, thinking about resizing ntfs and just dual booting

---

### Post by cwaldbieser on 2005-07-30
Can you "wget" the page?  What if you try to traceroute to it?  Anything suspicious there?  You could try using tcpdump or ethereal to watch the packets and see if anything odd is going on.

---

### Post by routerstu on 2005-07-30
it seems addresses resolve in applications to 1.0.0.0, unless i ping them 1st.  for instance, apt-get update tries to connect to 1.0.0.0 unless i ping archive.ubuntu.com and get the real ip?  so i think its safe to say it is dns.  does anyone know of any public dns servers? or any way i can uninstall this clients dns piece and reinstall it?

---

### Post by routerstu on 2005-07-30
this is to an address that i have not connected to before this wget, and it works.
going to download packet sniffer next to see what firefox is doing, if anything.






admin@ubuntu:~$
admin@ubuntu:~$
admin@ubuntu:~$ wget cnn.com
--10:35:56--  [http://cnn.com/](http://cnn.com/)
           => `index.html.1'
Resolving cnn.com... 64.236.16.52, 64.236.16.84, 64.236.16.116, ...
Connecting to cnn.com[64.236.16.52]:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.cnn.com/](http://www.cnn.com/) [following]
--10:35:57--  [http://www.cnn.com/](http://www.cnn.com/)
           => `index.html.1'
Resolving [www.cnn.com](www.cnn.com)... 64.236.16.52, 64.236.16.84, 64.236.16.116, ...
Connecting to [www.cnn.com](www.cnn.com)[64.236.16.52]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 57,427 [text/html]

100%[====================================>] 57,427        80.20K/s

10:35:58 (79.91 KB/s) - `index.html.1' saved [57,427/57,427]

---

### Post by dexter on 2005-07-31
I've been playing around with Ethereal and seems like it is a DNS problem, the websites that don't show up have DNS ip answer 1.0.0.0. However surfing to ip adresses themselves doesn't help here...

---

### Post by cwaldbieser on 2005-07-31
[QUOTE=dexter]I've been playing around with Ethereal and seems like it is a DNS problem, the websites that don't show up have DNS ip answer 1.0.0.0. However surfing to ip adresses themselves doesn't help here...[/QUOTE]

Have you tried using "nslookup" or "dig" to see if you can resolve the names that way?  Maybe the DNS server you are using has a problem and you need to contact the admins.

What happens if you "hard-code" one of the web-site addresses in your /etc/hosts file?

---

### Post by routerstu on 2005-08-06
ok, i think i have something that works, found from google.


first, dont use the dns ip handed out via dhcp, use a real resolving nameserver, ask a friend for the IP.  apparently some models of dsl routers choke and just hand out 1.0.0.0 for any queries.

second, open firefox type in address bar "about:config", then filter by ipv6 and set to true (which should disable ipv6).

---

### Post by mr_stabby on 2005-08-08
[QUOTE=routerstu]ok, i think i have something that works, found from google.


first, dont use the dns ip handed out via dhcp, use a real resolving nameserver, ask a friend for the IP.  apparently some models of dsl routers choke and just hand out 1.0.0.0 for any queries.

second, open firefox type in address bar "about:config", then filter by ipv6 and set to true (which should disable ipv6).[/QUOTE]

I's currently sharing Dexter's problem. I can ping my router and other machines on my network but can't do much else. Still can't resolve this problem. Anybody managed to get round it?

---

### Post by aqua26 on 2006-01-10
PPL 
lets cheat the system here is what i did for the same issue

 
```

# su -
#  vi /etc/apt/source.list

```
then copied the server name like in my case it was "in.archive.ubuntu.com"
then i did
```
#ping in.archive.ubuntu.com 
PING in.archive.ubuntu.com (82.211.81.151) 56(84) bytes of data.
64 bytes from in.archive.ubuntu.com (82.211.81.151): icmp_seq=1 ttl=50 time=178 ms
64 bytes from in.archive.ubuntu.com (82.211.81.151): icmp_seq=2 ttl=50 time=178 ms

```
then copied the same ipaddress to the /etc/apt/source.list file
```
deb http://82.211.81.151/ubuntu breezy main restricted
```
& the problem is solved then u can do the 
```
 #apt-get update
```

Have fun 
Loves Linux ;)

---

### Post by muffie on 2006-03-24
[QUOTE=routerstu]ok, i think i have something that works, found from google.


first, dont use the dns ip handed out via dhcp, use a real resolving nameserver, ask a friend for the IP.  apparently some models of dsl routers choke and just hand out 1.0.0.0 for any queries.

second, open firefox type in address bar "about:config", then filter by ipv6 and set to true (which should disable ipv6).[/QUOTE]

Just doing this worked a treat for me. Cheers

---

### Post by albesan on 2006-11-28
hello team,

totally new to linux even newer to ubuntu.
But I was using SUSE and had the same problem and I found a pretty cool solution wich involved adding at the end of " /etc/modprobe.conf " the lines:

" alias ipv6 off "
" alias net-pf-10 off "

I tried to do the same in xubuntu but there is no " modprobe.conf " file.
There is a " modprobe.d " directory and there is a file called aliases wich I tried to add the above mentioned lines to but it didn't do it.

Does anyone know/can guess if this method would be applicable and wich would be the file to edit to include the lines?

any help would be appreciated, although I realised this is a prety old posting.

a.

---

### Post by catchbubbles on 2007-10-20
I did these two things which worked for me

1. Opened "about:config", filter by ipv6 and set it to true
2. /etc/hosts changed (IPv6 section)

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

---

