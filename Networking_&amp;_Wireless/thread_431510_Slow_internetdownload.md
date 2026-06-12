---
title: "Slow internet/download"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by thedragon4453 on 2007-05-03
Ive recently switched to a dual boot config in ubuntu, and i am having a problem with internet speeds. right now i connect to a cable modem through a hardwire router. in a similar post someone asked for the output of ifconfig, and a ping to google, so here are both:

eth0      Link encap:Ethernet  HWaddr 00:11:5B:7B:20:BA  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe7b:20ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:243212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163787899 (156.2 MiB)  TX bytes:10645182 (10.1 MiB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27476 (26.8 KiB)  TX bytes:27476 (26.8 KiB)

PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=238 time=333 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=239 time=339 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=238 time=333 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=238 time=334 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 16048ms
rtt min/avg/max/mdev = 333.592/335.416/339.137/2.282 ms

anyway, of all the things ive been frustrated with so far in switching, this has got to be top of the list. i usually see around 3 seconds of page load time on xp, and now its gone up to as much as thirty, but averaging 20-25. the same with bittorrent files. i will sometimes get dl speeds of 1kbps on a well seeded file. i have already tried port forwarding on the router to help this problem, to no avail. i have problems with neither on xp, so if someone could help me out, id appreciate it.

---

### Post by RC211V on 2007-05-06
I am having the same problem. I have a university 10MB LAN and it works great on XP. But in edgy it is much slower in browsing and downloading as well. I run the test at [http://www.speedtest.net](http://www.speedtest.net) and I get slower results in Edgy. Someone help! :guitar:

---

### Post by pixar on 2007-05-08
same problem

---

### Post by ezrollers on 2007-05-13
I've got exactly the same problem

Downloads barely go over 40 KB/s and on windows i could easily get 400KB/s

Someone suggested disabling ipv6

hasn't worked for me though

add to /etc/modprobe.d/blacklist

blacklist ipv6

Reboot

ip a | grep ipv6 

should show nothing

Any other ideas?

Anyone

---

### Post by thedragon4453 on 2007-05-15
ok, for those still having this issue:

I disabled IPV6 by editing the aliases file. Then I disabled it in firefox using about:config. After that I was still having slow DNS lookups. The only thing I did to fix that was reset the router, and make sure that the dynamic dns setting was checked.

Now everything seems to work. Except torrents. Even with properly forwarded ports, I get crap speeds for torrents.

---

### Post by ezrollers on 2007-05-16
I turn my router off every night.

Interestingly I get good download speeds from usenet and bittorrent but crap speeds when I download using firefox or konqueror.

Mozilla bug??

Gonna try Opera this afternoon when I get home

---

### Post by ezrollers on 2007-05-16
I installed Opera and it works fine.

Tried to download an ubuntu iso and it was constant @ 450 KB/s

I'm a happy camper :guitar: 

Now, if kde could be as realiable as windows

---

### Post by likwid on 2007-05-25
Any ideas how to fix this as i have the same problem?

On my routed network there are two ubuntu 7.04 boxes one is fine, the other is problematic. When i try to open a webpage after booting up, browsing is quick and there are no problems. After a few minutes though i find that firefox is forever "looking up" addresses, for around 7-10 seconds a time. Obviously on sites where, for example, images are on an external servers, this results in very slow browsing.

My isp's virgin media (uk) and they wont give me their dns server addresses. I've completely disabled ipv6. A windows installation on the same machine has no problems.

Any help would be very much appreciated. I have a lot of work for uni to do on this machine and it's driving me insane the amount of time i'm wasting doing research.

---

### Post by mmdski on 2007-05-25
It may depend on what type of router you have.

I was having similar trouble before I purchased a new one.  On a Netgear MR814v2, Windows wireless and wired seemed to working fine, but the connection dropped every once in a while.  Ubuntu wired was ok, but the wireless was very slow.  After I setup a Linksys WRT54G, everything flies.

At first I blamed my crappy connection on Ubuntu, but it was a crappy router. :D

---

### Post by handaxe on 2007-05-25
[http://ubuntuforums.org/showpost.php?p=2378667&postcount=6](http://ubuntuforums.org/showpost.php?p=2378667&postcount=6)

May help and interesting stuff anyhow...

HA

---

### Post by p1977p on 2007-05-28
i recently installed xubuntu fiesty on my laptop (AMD 64 bit, 512 RAM) and find that internet speeds are woefully slow (as compared to that on Windows XP). i have found that this happens becoz the dns service takes a very long time despite having turned off ipv6. i connect by LAN to a Windows network. using 'dig' with TCP enabled and  the -4 option gives great improvement, but could someone tell me how i can have the DNS to automatically enable TCP during every search?

thanks

---

### Post by p1977p on 2007-06-05
> **thedragon4453 said:**
> Ive recently switched to a dual boot config in ubuntu, and i am having a problem with internet speeds. right now i connect to a cable modem through a hardwire router. in a similar post someone asked for the output of ifconfig, and a ping to google, so here are both:

eth0      Link encap:Ethernet  HWaddr 00:11:5B:7B:20:BA  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe7b:20ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:243212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163787899 (156.2 MiB)  TX bytes:10645182 (10.1 MiB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27476 (26.8 KiB)  TX bytes:27476 (26.8 KiB)

PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=238 time=333 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=239 time=339 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=238 time=333 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=238 time=334 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 16048ms
rtt min/avg/max/mdev = 333.592/335.416/339.137/2.282 ms

anyway, of all the things ive been frustrated with so far in switching, this has got to be top of the list. i usually see around 3 seconds of page load time on xp, and now its gone up to as much as thirty, but averaging 20-25. the same with bittorrent files. i will sometimes get dl speeds of 1kbps on a well seeded file. i have already tried port forwarding on the router to help this problem, to no avail. i have problems with neither on xp, so if someone could help me out, id appreciate it.
[COLOR=Black]
ok guys, i think i have achieved some success with that. i had the same problem. I installed ***"pdnsd"*** from the repositories. it creates a cache of dns queries (like dnsmasq, but it stores it to a file on shutdown... better for sites that are constantly up.... like google). you have to make some adjustments to the .conf file (see "man pdnsd" and "man pdnsd.conf" for that... the file's in the /etc  directory. hope this works for you too. here's my pdnsd.conf file contents:

// $Id: pdnsd.conf.in,v 1.4 2000/11/11 20:32:58 thomas Exp $

global {
    perm_cache=2048;
    cache_dir="/var/cache/pdnsd";
    max_ttl=604800;
    min_ttl=300;
    run_as="parag";
    paranoid=off;
    daemon=on;
### in my case i find that tcp queries are faster, hence the following
    tcp_server=on;
[/COLOR][COLOR=Black]    query_method=tcp_udp;[/COLOR]
[COLOR=Black]    verbosity=0;
## the following disables ipv6, you may also need to change firefox settings in "about:config">network.disable.ipv6 = true
    run_ipv4=on;
    tcp_qtimeout=2;
    timeout=5;
    randomize_recs=on;
#    next setting allows ppp/ip-up update the name servers -- ABa / 20040213
    status_ctl=on;
#    server_port=53;
    server_ip=any;
}

server {
    label="NetworkServer";
    ip= <<your LAN/ISP DNS server>> ;
#    file= "/etc/resolv.conf";   //tried using file as source of nameservers.... didn't work

    timeout=5;
    interval=30;
    uptest=query;
    ping_timeout=5;
    caching=on;
    purge_cache=off;
    lean_query=on;

}


# if you installed resolvconf, and status_ctl=on
server {
    label="resolvconf";
}

source {
    ttl=86400;
    owner="localhost.";
#    serve_aliases=on;
    file="/etc/hosts";
}

/*
neg {
    ttl=86400;
    name="foo.bar.";
    types=domain;
}

neg {
    ttl=86400;
    name="foo.baz.";
    types=A,AAAA, MX;
}
*/
/*
rr {
    ttl=86400;
    owner="localhost.";
    name="localhost.";
    a="127.0.0.1";
    soa="localhost.","root.localhost.",42,86400,900,86400,86400;
}

rr {
    ttl=86400;
    owner="localhost.";
    name="1.0.0.127.in-addr.arpa.";
    ptr="localhost.";
    soa="localhost.","root.localhost.",42,86400,900,86400,86400;
} */

[/COLOR]

---

