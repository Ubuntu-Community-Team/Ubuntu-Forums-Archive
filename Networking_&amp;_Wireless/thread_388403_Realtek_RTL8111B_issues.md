---
title: "Realtek RTL8111B issues"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by kierskoe on 2007-03-19
Hi all, 

I have a basic 6.10 install, my mainboard is a MSIp965 and the onboard gigabit ethernet controller is a Realtek RTL8111B. 

Im experiencing very slow response times when trying to contact anything from my machine, when pinging the router or anything on the LAN response times are very slow and browsing etc is very slow. Pinging the local address/loopback is fine.

I installed the drivers held on the Realtek website:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

the driver is:
 # lsmod | grep r1000
r1000                  21004  0 

here its listed in dmesg

[17179654.236000] eth0: Identified chip type is 'RTL8168B/8111B'.
[17179654.236000] eth0: r10001.05, the Linux device driver for Realtek Ethernet Controllers at 0xd800, 00:16:17:d7:ab:4c, IRQ 177
[17179655.976000] Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet Network Adapter
[17179655.976000] Driver version:1.05
[17179655.976000] Released date:2006/10/25
[17179655.976000] Link Status:Linked
[17179655.976000] Link Speed:100Mbps
[17179655.976000] Duplex mode:Full-Duplex
[17179655.976000] I/O Base:0xD800(I/O port)
[17179655.976000] IRQ:177

I have tried disabling ipv6 as i thought that might be the problem but i had no joy there.
Any help is much appreciated. Thanks

---

### Post by Mr. C. on 2007-03-19
How did you try disabling IPv6 ?  For Firefox?  Or system-wide ?

Show some ping outputs.

Ping's to the loopback intrface will always be fast - there is no NIC involved.  Don't use that as a test - it tells you essentially nothing.

MrC

---

### Post by kierskoe on 2007-03-21
Thanks for the reply.

As i said above i have disabled ipv6 in both firefox and dhclient.conf. I have also made sure both the router and local dns settings are pointing to OpenDNS.

The reason i checked ping to local address 192.168.1.2 was to establish any static ip addressing problems and hardware failure, the network card also works fine when i boot up XP.

heres some ping results:
192.168.1.1 = Router
192.168.1.2 = Local machine


*******:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=1300 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=300 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=1317 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=304 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=979 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=328 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=254 time=1349 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=254 time=347 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=254 time=1370 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=254 time=357 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9036ms
rtt min/avg/max/mdev = 300.603/795.605/1370.241/479.148 ms, pipe 2

*********:~$ ping google.ie
PING google.ie (64.233.161.104) 56(84) bytes of data.
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=1 ttl=241 time=2020 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=2 ttl=241 time=1019 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=3 ttl=241 time=2037 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=4 ttl=241 time=105 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=5 ttl=241 time=106 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=6 ttl=241 time=1586 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=7 ttl=241 time=582 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=8 ttl=241 time=1523 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=9 ttl=241 time=520 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=10 ttl=241 time=962 ms

--- google.ie ping statistics ---
12 packets transmitted, 10 received, 16% packet loss, time 19189ms
rtt min/avg/max/mdev = 105.164/1046.532/2037.474/686.969 ms, pipe 3

---

### Post by Mr. C. on 2007-03-21
This is a terrible connection.  your response times to your router should be on the order of <10ms.

But the good news is that you have a case that narrows the problem down to the lowest levels.  Ignore DNS settings for now; the problems is much lower than that and DNS is not a factor.  Let's focus on the connection between the problematic host and your router.

I don't mean to press you, but I see that you've disabled IPv6 in two different ways than I would suggest.  Follow the instructions here:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

and try your router ping test again.  If this does not change the behavior, we'll go to the next steps.

Please use a different term than "local address", especially in the same sentence with loopback or your definition of "local machine".  In your contexts "local address" sounds like the IP address of the host itself, and not the IP of your router.  There is little value in ping either 127.0.0.1 or your host's own IP address.

MrC

---

### Post by kierskoe on 2007-03-22
sorry i meant 192.168.1.2 not 192.168.1.1 when referring to local address... rushed that post.


I tried disabling ipv6 in the way the link you posted states but theres no change in poor ping results.


I always thought pinging your own address (192.168.1.2) would verify the tcp/ip stack is functioning properly?



anyways back on topic, any suggestions?... thanks again for taking the time to help out.

---

### Post by Mr. C. on 2007-03-22
Hi kierskoe,

So this is an interersting issue.  I'm wondering if this is problem with your combination of router and this driver.

I looked over the driver code, and found that a new way of dealing with interrupt work was enabled.  What I noticed from your ping times is that they are very consistent in times, like 300, 900, or 1300 ms.  This seems too coincidental to me.

I presume you built the driver yourself.  If so, I have a suggestion for you to try something.

In the file r1000.h, find and change the lines:
```

#define R1000_BOTTOM_HALVES 
//#undef R1000_BOTTOM_HALVES
```

to

```
//#define R1000_BOTTOM_HALVES 
#undef R1000_BOTTOM_HALVES
```

Also change the version number

```
#define R1000_VERSION "1.05"
```

to

```
#define R1000_VERSION "1.05a"
```

so that you can ensure this module is installed later.

Rebuild and reinstall the driver, and reboot.  Try your pings again after that and let me know what you find.

MrC

---

### Post by kierskoe on 2007-03-27
Tried the above and on reboot i cannot get past the splash screen. :(

cheers for the suggestion though

---

### Post by Mr. C. on 2007-03-27
It was just a shot in the dark.  I do have another, easier suggestion.

A recent problem was discovered with new kernel versions and non-compliant routers.  See: 

Post 8: [http://ubuntuforums.org/showthread.php?t=383390&highlight=mrc+kernel+window](http://ubuntuforums.org/showthread.php?t=383390&highlight=mrc+kernel+window)

MrC

---

### Post by kierskoe on 2007-03-28
Im going to clean install ubuntu again and see what happens, i have a funny feeling thats its just one of those things that i will never figure out. I have used this router with other Ubuntu releases, Fedora Core and Gentoo and didnt get any problems....... however my mainboard w/ onboard NIC is the only thing that has changed since then.

Ill post back when i get time to install, fingers crossed. Cheers Mr.C

---

### Post by SikEnCide on 2007-04-04
ok i have the same pci-e card in my laptop and i here is hte link to my post where i got rid of the problem.

[http://ubuntuforums.org/showthread.php?t=388403](http://ubuntuforums.org/showthread.php?t=388403)

also dont forget to change firefox

[B]open the browser
type about:config in the address bar.
search for "ipv6"
make sure it says

network.dns.disableIPv6     
with a value of "true"[/B]

---

### Post by max0504 on 2007-04-08
I understand this is the Ubuntu forums but I thought the following would be interesting:

I have a P5B motherboard with an integrated RTL8111B PCI-E Gb LAN 
Installed Fedora Core 6 and used the driver from the Realtek website (r1000v1.05.tgz)

I am also experiencing slow ping responses at times and browsing experience is very slow. 
System is setup for duel boot to Windows XP and browsing within XP is fine.

---

### Post by kierskoe on 2007-04-22
Ok, problem sorted.


I waited for feisty fawn to come out but had problems with the Jmicron controller and GRUB. So i installed Kubuntu Edgy and it worked from scratch... no disabling ipV6 or building drivers... so all is well. Thanks for all the input.

---

