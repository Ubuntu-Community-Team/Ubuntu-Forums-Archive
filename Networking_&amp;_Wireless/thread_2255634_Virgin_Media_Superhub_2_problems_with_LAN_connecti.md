---
title: "Virgin Media Superhub 2 problems with LAN connection"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by cheapodonuts on 2014-12-06
Trying to install a Superhub 2 that arrived a short while back. 
 According to the install manual that came with the equipnent, all I had to do was connect the Virg cable, my LAN cable and switch everything on. The hub starts up and all the lights on it seem to work but the ' &#10004; ' sign keeps flashing.
 I called for assistance and explained that I didn't recall my VirgMed password, but I'm not certain if that was requirea anyway, because I never understood half of what was being said at the other end. :oops:
I wish they'd publish their instructions help online, like a Wiki.
 I'm partly deaf and have bad tinnitus, which doesn't help.

Can anyone give me some guidelines as to what might be going wrong?

Thanx in advance

Pete.

---

### Post by chili555 on 2014-12-06
Let's see if we can figure it out having never seen or used one!! I assume the cable coax is connected to the modem and an ethernet cable is connected from the computer to the modem. Let's see if the computer sees the modem. Please open a terminal Ctrl+Alt+t and run:```
ifconfig
```Do you see an ethernet interface, ideally eth0? Does it have an IP address, something like:```
inet addr:192.168.1.14
```Or any numbers at all?

Do you see the Network Manager icon at the top; something like this? [http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2012/05/u2.jpg](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2012/05/u2.jpg)

I believe the checkmark on the modem is solid blue if the Super Hub has completed its registration with the Virgin Media network. I assume that was what was supposed to happen when you called them. If it doesn't turn solid blue soon, I'd try calling them again.

Here is the manual, if it helps: [https://my.virginmedia.com/content/dam/virgoBrowse/docs/Discover_Broadband_quick_guide.pdf](https://my.virginmedia.com/content/dam/virgoBrowse/docs/Discover_Broadband_quick_guide.pdf)> have bad tinnitus, which doesn't help.Yeah, me, too. Isn't it lovely?

---

### Post by cheapodonuts on 2014-12-11
Dam, I posted a reply next day, with ifconfig results for both routers etc. Where did it go? Aargh! I'll have to do it again. Too tired now. Tomorrow.

---

### Post by cheapodonuts on 2014-12-29
Hi again chili. ):P
OK, better late than never. Been away for xmas.
Lol! VirgMed are jumping up and down asking for their equipment back. They probably think I've sold it or something. :rolleyes: Pffft, I paid their fee and they gave me the box. On the VirgMed forum someone mentioned that I can't connect without the phone call. [-(

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:25:dc:0a  
          inet addr:82.41.174.81  Bcast:82.41.174.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe25:dc0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:378663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:379668121 (379.6 MB)  TX bytes:33839908 (33.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:26641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2946202 (2.9 MB)  TX bytes:2946202 (2.9 MB)

Hopefully I'll get this sorted by the new year. I may have to get a friend to mak the call.

---

### Post by The Cog on 2014-12-29
Interesting - that's a virgin address you have there, and I can ping it from home. My superhub2 allocates private (192.168.1.x) addresses, but I wasn't involved in the setup - a pair of virgin engineers came and did it along with a set-top box for the TV.

---

### Post by chili555 on 2014-12-29
As The Cog notes, you have an IP address associated with your ethernet interface. Your computer is connected to the modem and the modem has received an IP address from Virgin. Have you tried to open a browser; Firefox, for example? It may open a page that says you haven't yet registered; like this: [http://www.crackunit.com/wp-content/uploads/image_well/virgin_media.jpg](http://www.crackunit.com/wp-content/uploads/image_well/virgin_media.jpg)

I believe if you call them, you'll be all set. Everything we see from the Ubuntu side looks fine.

---

### Post by cheapodonuts on 2014-12-29
Ah jeez guys!
 WTH? I just tested my old modem and forgot to connect the superhub2 in it's place! :lolflag::lolflag::lolflag:

FACEPALM!

f*K IT

I'LL TRY AGAIN

---

### Post by cheapodonuts on 2014-12-29
Superhub2

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:25:dc:0a  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe25:dc0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92130 (92.1 KB)  TX bytes:96969 (96.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162058 (162.0 KB)  TX bytes:162058 (162.0 KB)

---

### Post by chili555 on 2014-12-29
> inet addr:[COLOR="#FF0000"]192.168.0.2[/COLOR] Looks good to me! What do you see when you open a browser? Is everything working as expected?

---

### Post by cheapodonuts on 2014-12-29
"Cannot find server" error comes up on any browser page I try to open.

I've just been reading about the RogerVoice phone app. It converts incoming voice calls to text on smartphones. It seems to be exactly what I need in this situation, but, ironically, I don't have one yet. :rolleyes:

---

### Post by cheapodonuts on 2014-12-29
Everything else seemed normal. Wired connection was active and eth0 seemed connected too with packets being exchanged etc.

---

### Post by chili555 on 2014-12-29
I suggest you have a friend call them and help you complete the registration. I'm pretty confident that that's the only issue.

---

### Post by cheapodonuts on 2014-12-29
Yup, I don't seem to have a choice. :rolleyes:

---

### Post by chili555 on 2014-12-29
> **cheapodonuts said:**
> Yup, I don't seem to have a choice. :rolleyes:Please see my Private Message.

---

