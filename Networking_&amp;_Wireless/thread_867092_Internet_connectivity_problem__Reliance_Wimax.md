---
title: "Internet connectivity problem : Reliance Wimax"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by guhanr on 2008-07-22
Ubuntu 8.04 on a Dell Dimensions Desktop

Used to have a wired PPPoE connection through an ISP provider. Bunch of issues, so gave up on that and moved to a ISP provider called Reliance, who is offering wired connectivity via WiMax (basically an antenna and a PoE switch, with an ethernet connection directly to my computer). 

Works great on Windows (used to have a problem getting an IP because of my firewall - Comodo, but now I added that as a trusted zone and all is well. 

Bascially is supposed to be a zero configuration - plug, get IP and go. On Ubuntu 8.04, cant seem to get this connection to work at all. Am working on a Dell Inspiron Desktop, 

```
ifconfig
```results in 
> 
eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:107 dropped:0 overruns:0 frame:107
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7861 (7.6 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          inet addr:169.254.4.211  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6348 (6.1 KB)  TX bytes:6348 (6.1 KB)
So, from one of the forum posts ([http://ubuntuforums.org/showthread.php?t=692902](http://ubuntuforums.org/showthread.php?t=692902)), I learnt that Avahi (Ipv6) might be the problem, so I disabled using 
```
sudo /etc/init.d/avahi-daemon stop
```and my ifconfig reads

> 
eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:60 dropped:0 overruns:0 frame:60
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4837 (4.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6348 (6.1 KB)  TX bytes:6348 (6.1 KB)
And when I choose Ipv4LL in networking options, my avahi comes back up and I get this

> 
eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:107 dropped:0 overruns:0 frame:107
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7861 (7.6 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          **inet addr:169.254.4.211  Bcast:169.254.255.255**  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6348 (6.1 KB)  TX bytes:6348 (6.1 KB)Interestingly, the IP address I get for Avahi is the same one I got with windows when I had firewall problems and got a "Limited connectivity". But when I down avahi, I cant seem to get the IP on eth0. 

Ubuntu without internet, doesn't feel right... Sigh. Any ideas on what I can do to get back online? 

Many thanks...

---

### Post by guhanr on 2008-07-23
Updates:

I spoke to a friend and realized that my old PPPoE connection may have something to do with it. So, my /etc/network/interfaces had the following lines, which I ended up deleting completely 

> auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
I also did 
```
alias net-pf-10 ipv6
``` to
```
alias net-pf-10 off
```and I'm left with just the default. 

Then changed Networking to roaming (to let Network manager get control completely)- The little icon on top right dances around for a while and then ifconfig is:

> eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:15 dropped:0 overruns:0 frame:15
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8484 (8.2 KB)
 
eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          inet addr:[169.254.4.211]("http://169.254.4.211/")  Bcast:[169.254.255.255]("http://169.254.255.255/")  Mask:[255.255.0.0]("http://255.255.0.0/")
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
           inet addr:[127.0.0.1]("http://127.0.0.1/")  Mask:[255.0.0.0]("http://255.0.0.0/")
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:4524 (4.4 KB)  TX bytes:4524 (4.4 KB)
Bring eth0 down and up and ifconfig is  [INDENT] > eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:25 dropped:0 overruns:0 frame:25
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8648 (8.4 KB)

lo        Link encap:Local Loopback  
          inet addr:[127.0.0.1]("http://127.0.0.1/")  Mask:[255.0.0.0]("http://255.0.0.0/")
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5624 (5.4 KB)  TX bytes:5624 (5.4 KB)[/INDENT]After it comes up, there is no IP address for eth0...then I rebooted and no real change, except Avahi comes up as well. 


[COLOR=#666666]> guhanr@Guhan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4184 (4.0 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          inet addr:[169.254.4.211]("http://169.254.4.211/")  Bcast:[169.254.255.255]("http://169.254.255.255/")  Mask:[255.255.0.0]("http://255.255.0.0/")
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:[127.0.0.1]("http://127.0.0.1/")  Mask:[255.0.0.0]("http://255.0.0.0/")
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2924 (2.8 KB)  TX bytes:2924 (2.8 KB) [/COLOR]

Then I stopped the avahi daemon, which just got rid of eth0:avahi. 

[COLOR=#999999]> [COLOR=#666666]eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  [/COLOR]
[COLOR=#666666]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR]
 [COLOR=#666666]          RX packets:0 errors:7 dropped:0 overruns:0 frame:7[/COLOR]
[COLOR=#666666]          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
 [COLOR=#666666]          collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=#666666]          RX bytes:0 (0.0 B)  TX bytes:4348 (4.2 KB)[/COLOR]
 
[COLOR=#666666]lo        Link encap:Local Loopback  [/COLOR]
[COLOR=#666666]          inet addr:[127.0.0.1]("http://127.0.0.1/")  Mask:[255.0.0.0]("http://255.0.0.0/")[/COLOR]
 [COLOR=#666666]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/COLOR]
[COLOR=#666666]          RX packets:54 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
 [COLOR=#666666]          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=#666666]          collisions:0 txqueuelen:0 [/COLOR]
 [COLOR=#666666]          RX bytes:3532 (3.4 KB)  TX bytes:3532 (3.4 KB)[/COLOR][/COLOR]


In an inspired burst, I put it back on wired network, roaming and then c**hanged the modprobe ipv6 from off to what it was before**. One more reboot later, here is what I see. The big difference is that my eth0 is now getting an IPv6 address, whereas it never got an address before - atleast not that I know of. I guess its because I turned the v6 thing on. Doesn't help my cause, because I still cant connect.:mad: [INDENT]guhanr@Guhan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          **inet6 addr: fe80::216:76ff:fe30:4e68/64 Scope:Link**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:309 dropped:0 overruns:0 frame:309
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:18724 (18.2 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:30:4e:68  
          inet addr:[169.254.4.211]("http://169.254.4.211/")  Bcast:[169.254.255.255]("http://169.254.255.255/")  Mask:[255.255.0.0]("http://255.255.0.0/")
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:[127.0.0.1]("http://127.0.0.1/")  Mask:[255.0.0.0]("http://255.0.0.0/")
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11505 (11.2 KB)  TX bytes:11505 (11.2 KB)

[/INDENT]Anything else I should be doing? 

Ideas...? HAAALP! Err...someone? Please? :(:(

---

### Post by pk_rulz on 2008-07-25
Very busi now ... please chech this if it helps .. .

[http://broadbandforum.in/reliance-broadband/22473-reliance-wimax-ubuntu-7-10-a/3/](http://broadbandforum.in/reliance-broadband/22473-reliance-wimax-ubuntu-7-10-a/3/)

Will get back 2 U

---

### Post by pk_rulz on 2008-07-25
Plz chk this 1 also
[http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-2.html](http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-2.html)

I know its frustating ... I have gone through that ...

There are some things that need to be tested 1st

1. Hope ur machine is a dual boot machine
2. 1st login to windows and get an  IP. remember dont login ... ot u can login and then logout point is u should not have a login just an IP
3. Then boot into linux
4. Go 2 cmd prompt 
5. Then follow this [http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-3.html#post18508](http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-3.html#post18508)

Lets c if that works ... will get back later

---

### Post by guhanr on 2008-07-26
PK Rulz, 
Many thanks for your resposne. My replies below and a few questions follow... 

> Plz chk this 1 also
[http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-2.html](http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-2.html)Stopped avahi daeomon many times, but if I pick IPV4LL or Roaming it comes back up. I tried removing the avahi-daemon from init.d and I ended up deleting the file [I did sudo nautilus] - I cant even find it in trash..Dumb me. Net effect, I cant stop the daemon that way. At any rate, even stopping the daemon didnt give me a valid IP anyways. 

> 1. Hope ur machine is a dual boot machineYes. Dual boot with GRUB loader, primary.

> 2. 1st login to windows and get an  IP. remember dont login ... ot u can login and then logout point is u should not have a login just an IP 
Did that. Have wireshark installed on Windows so I can see all the packets. Nothing out of the ordinary that I can see, except that a DHCPDISCOVER gets a DHCPOFFER, whereas a dhcpclient in Ubuntu doesnt get a DHCPOFFER. 

> 3. Then boot into linux | 4. Go 2 cmd prompt  | 5. Then follow this [http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-3.html#post18508](http://www.indiabroadband.net/reliance-broadband/4390-new-problem-reliance-wimax-3.html#post18508)
I added the MSFT5.0 in the conf line. Didnt make a difference - still no valid IP. 

From the links you sent, the only thing I havent done is try it for 2 hrs or the likes. I try it for about 30minutes or so, and then throw in the towel. Maybe I shd leave it on for a night? [SIZE=1][I]I dont see how that will make a difference, but at this point, I will try anything! (Lucky amulets, good luck charms, whatever...):mad:
[/I][/SIZE]
_I have a few questions :_


[LIST=1]
[*]What should the network connection option be at?
[LIST=1]
[*]Roaming (where then the network manager takes over completely) or
[*]DHCP?
[*]I dont know if IPv4LL will work?
[/LIST]
 
[*]Do let me know what I can do for the avahi thing? How do I to get it back? (If I need to?)
[*]I am trying to get wireshark for ubuntu by downloading deb from windows.. but I seem to have 6 dependencies - is there some place I can get the whole thing as a deb file, at one go? Since I cant get to the internet from Ubuntu...
[/LIST]

---

### Post by Red-Shield on 2008-07-29
i just read all that wow linux can get so complicated some times what i think is that you should manualy config the /etc/network/interfaces and then kill the nmapplet it seems to interfere but i am no expert it just works for me let me know how it works out it can be a bitch sometimes.

---

### Post by guhanr on 2008-08-03
> **Red-Shield said:**
> ... just read all that wow linux can get so complicated some times what i think is that you should manualy config the /etc/network/interfaces and [COLOR=sienna]then kill the nmapplet it seems to interfere[/COLOR] but i am no expert it just works for me let me know how it works out [COLOR=sienna]it can be a bitch sometimes[/COLOR]. 
 
How true. Havent tried killing the nmapplet yet - will try and keep you posted. 
 
**[SIZE=3]More updates:[/SIZE]**

Since XP is getting an IP and Ubuntu isnt, a pal of mine did a compare of the DHCPDISCOVER packets on XP and Ubuntu using *wireshark *and found 2 key differences btwn the Windows and Ubunut packets on DHCP request. [LIST=1]
[*]Request parameters options [both number of and type of are differnet] and
[*]*DHCP auto configuration *that Windows sends and Ubuntu is not able to send.
[/LIST]
[INDENT]**1. Request parameters. **
From what I have seen and compared, Windows sends 11 request parameters; Ubuntu sends only 9. So, I removed the following (since XP was not sending these)
* 28 [broadcast address]
* 2 [Time offset]
* 12 [hostname]
 
and added the following from reading the RFC for options in DHCP
 
* 31 [perform router discover]
* 33 [static route]
 
also added ```
 send dhcp-client-identifier 01:MY:MAC:AD:DR:ESS
``` to dhclient.conf 
 
 

Now, I am trying to add these options to be sent by Ubuntu. XP sends them, but am not able to. 
[LIST]
[*]249 [classless static route (microsoft)]
[*]43 [Vendor specific information]
[/LIST]
[/INDENT][COLOR=red]Any idea what I can do to send option-249 and opiotn-43 as part of my request list? Googling wants me to add script to my dhcpclient.exit.d hooks?[/COLOR]

 
**2. The mysterious DHCP Auto-Configuration**
The windows parameter looks like: 
[SIZE=1]Quote:
[INDENT][SIZE=1]Option: (t=116,l=1) DHCP Auto-Configuration[/SIZE]
[SIZE=1]Option: (116) DHCP Auto-Configuration[/SIZE]
[SIZE=1]Length: 1[/SIZE]
[SIZE=1]Value: 01[/SIZE]
[/INDENT][/SIZE]I cant get Ubuntu to send it in the dhclient.conf - Any ideas on how I can send option116?
 
I think if I manage to get these 2 things sorted (#1,#2), should be able to connect. Err - as you can tell, I've spent many hours on trying to get this to work- Its gone beyond an actual need - its more like an itch that wont go away... I'm sure most of you know what it feels like? :) 
 
As always, Any help will be appreciated.
 
PS - I **dont have dhcpcd**.. I use /etc/dhcp3/dhclient - Does that matter?
 
*dhclient.conf *- my current file reproduced in full below - my additions in [FONT=Fixedsys][COLOR=red]red font[/COLOR][/FONT]; 
*/etc/network/interfaces* after that
 
**dhclient.conf **
 
> 
[SIZE=1][SIZE=1]# Configuration file for /sbin/dhclient, which is included in Debian's[/SIZE]
[SIZE=1]# dhcp3-client package.[/SIZE]
[SIZE=1]#[/SIZE]
[SIZE=1]# This is a sample configuration file for dhclient. See dhclient.conf's[/SIZE]
[SIZE=1]# man page for more information about the syntax of this file[/SIZE]
[SIZE=1]# and a more comprehensive list of the parameters understood by[/SIZE]
[SIZE=1]# dhclient.[/SIZE]
[SIZE=1]#[/SIZE]
[SIZE=1]# Normally, if the DHCP server provides reasonable information and does[/SIZE]
[SIZE=1]# not leave anything out (like the domain name, for example), then[/SIZE]
[SIZE=1]# few changes must be made to this file, if any.[/SIZE]
[SIZE=1]#[/SIZE]
 
[SIZE=1]#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;[/SIZE]
[SIZE=1]#send dhcp-lease-time 3600;[/SIZE]
[SIZE=1]#supersede domain-name "fugue.com home.vix.com";[/SIZE]
[SIZE=1]#prepend domain-name-servers 127.0.0.1;[/SIZE]
[SIZE=1]##The original line for *request* [/SIZE]
[SIZE=1]##request subnet-mask, broadcast-address, time-offset, routers,[/SIZE]
[SIZE=1]## domain-name, domain-name-servers, host-name,[/SIZE]
[SIZE=1]## netbios-name-servers, netbios-scope;[/SIZE]
 
[SIZE=1]#Sending specific information that Reliance seems to be looking for[/SIZE]
 
[SIZE=1][FONT=Lucida Console][COLOR=red][FONT=Fixedsys]send host-name "XXX-XXXX";[/FONT][/COLOR][/FONT][/SIZE]
[FONT=Lucida Console][SIZE=1][FONT=Lucida Console][COLOR=red]send vendor-class-identifier "MSFT 5.0";[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Lucida Console][COLOR=red]send dhcp-client-identifier 01:01:MY:MAC:AD:DR:ESS;[/COLOR][/FONT][/SIZE]
[/FONT]
[SIZE=1]#send dhcp-lease-time 7200;[/SIZE]
 
[SIZE=1][FONT=Fixedsys][COLOR=red]request subnet-mask, routers, router-discovery, static-routes, domain-name, domain-name-servers, netbios-name-servers, netbios-scope, netbios-node-type;[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Fixedsys][COLOR=red]timeout 60;[/COLOR][/FONT][/SIZE]
 
[SIZE=1]#require subnet-mask, domain-name-servers;[/SIZE]
 
[SIZE=1]#retry 60;[/SIZE]
[SIZE=1]#reboot 10;[/SIZE]
[SIZE=1]#select-timeout 5;[/SIZE]
[SIZE=1]#initial-interval 2;[/SIZE]
[SIZE=1]#script "/etc/dhcp3/dhclient-script";[/SIZE]
[SIZE=1]#media "-link0 -link1 -link2", "link0 link1";[/SIZE]
[SIZE=1]#reject 192.33.137.209;[/SIZE]
[SIZE=1]#alias {[/SIZE]
[SIZE=1]# interface "eth0";[/SIZE]
[SIZE=1]# fixed-address 192.5.5.213;[/SIZE]
[SIZE=1]# option subnet-mask 255.255.255.255;[/SIZE]
[SIZE=1]#}[/SIZE]
[SIZE=1]#lease {[/SIZE]
[SIZE=1]# interface "eth0";[/SIZE]
[SIZE=1]# fixed-address 192.33.137.200;[/SIZE]
[SIZE=1]# medium "link0 link1";[/SIZE]
[SIZE=1]# option host-name "andare.swiftmedia.com";[/SIZE]
[SIZE=1]# option subnet-mask 255.255.255.0;[/SIZE]
[SIZE=1]# option broadcast-address 192.33.137.255;[/SIZE]
[SIZE=1]# option routers 192.33.137.250;[/SIZE]
[SIZE=1]# option domain-name-servers 127.0.0.1;[/SIZE]
[SIZE=1]# renew 2 2000/1/12 00:00:01;[/SIZE]
[SIZE=1]# rebind 2 2000/1/12 00:00:01;[/SIZE]
[SIZE=1]# expire 2 2000/1/12 00:00:01;[/SIZE]
[SIZE=1]#} [/SIZE]
[/SIZE]
 
**/etc/network/interfaces**
> 
[SIZE=1][SIZE=1]auto lo[/SIZE]
[SIZE=1]iface lo inet loopback[/SIZE]
[SIZE=1]auto eth0[/SIZE]
[SIZE=1]iface eth0 inet dhcp [/SIZE]
[/SIZE]

---

### Post by vishal khialani on 2011-01-14
Hi guhanr,
I got the reliance wimax connection today and it does not seem to work with my linux laptop neither my belkin router.

I am quiet suprised that one could have so many problems with an ethernet connection.

Anyways I was wondering if you found out a way around this ? if so do share your tips.


Cheers,
Vishal

---

