---
title: "Attempted Break In"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by tjjhjr on 2009-05-28
[SIZE=5]Attempted Break In[/SIZE]
 
This IP address shows up in a forum on this site.  It is listed as having attempted an unsolicited connection to a UDP port on my computer. I have the dialog boxes with it and would like to know what would be the appropriate next step in an informal, non-legal, non-police way to approach the person.
 
[COLOR=red]169.254.5.132[/COLOR]
 
[SIZE=2]**Re: Wifi** [/SIZE]
[SIZE=2][/SIZE][SIZE=2]No, it doesn't work. Sorry.
I'm still making some tests (such as some ifdown/ifup interface). On the other hand I noticed 

manolo@manolo-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:17:31:fb:61:25 
inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::217:31ff:fefb:6125/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2797 errors:0 dropped:0 overruns:0 frame:0
TX packets:3473 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:2276644 (2.1 MB) TX bytes:499998 (488.2 KB)
Interrupt:219 Base address:0x6000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16111 errors:0 dropped:0 overruns:0 frame:0
TX packets:16111 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:805687 (786.8 KB) TX bytes:805687 (786.8 KB)

wlan0 Link encap:Ethernet HWaddr **00:13:02:ef:81:1f** 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet HWaddr **00:13:02:ef:81:1f** 
inet addr:[COLOR=red]169.254.5.132[/COLOR] Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

wmaster0 Link encap:UNSPEC HWaddr **00-13-02-EF-81-1F-00-00-00-00-00-00-00-00-00-00**
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Is it normal? I suppose it isn't, sice as I can remember when everything worked properly I didn't see all of those device names associated to the same mac address...
Could it be useful to remove some of them?

Thanks for your time!

PD: should I post some output in order to let you realize the present condition of my system after having applied those modifications you suggested above?
PD2: is [/SIZE][[SIZE=2][COLOR=#444444]this link[/COLOR][/SIZE]]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html")[SIZE=2] useful to me?[/SIZE]
[SIZE=2]*Last edited by manolomanolo; September 18th, 2008 at 09:25 AM.. *[/SIZE]
[SIZE=2][IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG][/SIZE]

---

### Post by Chalfont on 2009-05-28
Errrr
What does the first two lines of the post have to do with the rest of it?

---

### Post by Swerve1000 on 2009-05-28
You should look to employ MAC address filtering and limit the number of IP's your router will lease to the number of computers you have and set those lease time to 'forever'.


(unless you want to go on the offensive, ARP Poisoning would work well allowing you to see what this person is doing on your network).

---

### Post by tjjhjr on 2009-05-28
Our security system identified this IP as attempting an unsolicited connection to our Network.
 
I am trying to gather information.
 
The IP shows up in a forum on this site and therefore is semi-public, and I am trying to contact the message sender as well as members of the site to ---informally--- inquire about it.
 
Can't be any more polite about it at this time.

---

### Post by tjjhjr on 2009-05-28
Thank you.  We also wanted to make sure no one got into trouble for a typo. We don't need to have any un-deserved actions visited upon anyone who is not in fact trying to do this. However, should it be true, then we go from there.

---

### Post by aeiah on 2009-05-28
isnt that an internal IP address?

---

### Post by finer recliner on 2009-05-28
169.254.x.y IP addresses are assigned by the computer itself because it had a problem getting one from the router (or other DNS server). no one is hacking your network.

[http://ask-leo.com/why_cant_i_connect_with_a_169254xx_ip_address.html](http://ask-leo.com/why_cant_i_connect_with_a_169254xx_ip_address.html)

---

### Post by albinootje on 2009-05-28
> **tjjhjr said:**
> [SIZE=5]
wlan0:avahi Link encap:Ethernet HWaddr **00:13:02:ef:81:1f** 
inet addr:[COLOR=red]169.254.5.132[/COLOR] Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1


This is an ip address from a special network range, see here (Avahi, ZeroConf) :
[http://en.wikipedia.org/wiki/Classful_network](http://en.wikipedia.org/wiki/Classful_network)

When I use a wifi card, and it can't get a connection I also get an address in that range asigned.
It's your own address on your machine, I don't understand why you think that's some break in attempt.

---

### Post by wannadumpwindows on 2009-05-28
Misread the first post. And now that I read it right, it smells a little funny . . .

---

### Post by tjjhjr on 2009-05-28
possibly-but then that particular number only shows up at this site in a world wide search-so does that mean it is a number that is used by more than one system-?

---

### Post by tjjhjr on 2009-05-28
understood...range...not specific number.....thank you very much

---

### Post by tjjhjr on 2009-05-28
thank you

---

### Post by tjjhjr on 2009-05-28
Thank you all for the info---no further questions.

---

### Post by 3rdalbum on 2009-05-28
Haha, it reminds me of this Bash.org quote:

> 
<ruffkin2> HAHAHAH dat dude you sent me 127.0.0.1 iz enfected wit sub7 im screwin with him now
<andrw>  oh good, format his computer
<Testicular_One> format his computer
<TheGreaterZero> format him


His computer is 127.0.0.1.

I find it strange that you're complaining about an unsolicited connection to a port. It literally happens to everybody every day. Most people don't have overzealous security software that warns of it - instead, if there is no port listening, the computer doesn't respond to the connection. Simply attempting a connection to somebody's computer is not a crime, so the "non-police" bit is a certainty.

Plus, most people are on dynamic IP addresses. My router's current IP address has been in use by a million other computers in the past. So has yours.

I'm no expert but I'll trust those other people when they say that it's an internal IP address, and you either need to turn down the settings on your security software or ditch it as it's causing you needless worry.

---

### Post by PukingPenguin on 2009-05-28
From the relevant RFC:

> IANA                         Informational                      [Page 2]

RFC 3330               Special-Use IPv4 Addresses         September 2002


   169.254.0.0/16 - This is the "link local" block.  It is allocated for
   communication between hosts on a single link.  Hosts obtain these
   addresses by auto-configuration, such as when a DHCP server may not
   be found.


Don't panic.

---

### Post by iponeverything on 2009-05-28
Attempted Break In? -- For stray packet to a UDP port from an unrouteable IP address?

One might be forgiven for not knowing that that address was in private range - but please read up just tiny bit on network security, before you accuse anyone of breaking into your machine.

A few things to keep in mind. 

- Network scans are common and more often than not, are from an automated script where the owner of the machine has no clue that the machine is infected.

- Hitting UDP port on machine is not a break-in attempt. There are plenty of legitimate reasons you could be receiving a UDP packet from machine your not aware of. IF you had portmap running and it listening on 111 and the someone was testing it for a the long fixed exploit from 1994 -- then it might be considered  break-in attempt -- but a weak one.

- Now -- If you see in your log that you have 500 unsuccessful login attempts to ssh -- that is a break in attempt..

---

