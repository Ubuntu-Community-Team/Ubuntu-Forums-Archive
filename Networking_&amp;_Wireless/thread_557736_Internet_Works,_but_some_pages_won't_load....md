---
title: "Internet Works, but some pages won't load..."
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by Thunar on 2007-09-23
OK this is a weird problem: 

I installed Xubuntu 7.04 (Feisty Fawn) on an older P3 machine, and it originally had no network card so occasionally I would reboot my cable modem and plug it usb-style into my Xubuntu machine (rebooting allows the modem to learn a new mac address), and while connecting directly via usb the internet worked perfectly in every aspect. Since then I installed a 10/100 network card in the computer and connected it via Ethernet and switch to my Windows XP machine. The Windows machine now connects directly via the modem and the Xubuntu machine connects through it. To do this I had to assign static IP addresses to both NICs on both machines so they can talk through the switch. At first this caused me much trouble as very few pages would load. Then I disabled the Windows firewall and PRESTO! Internet. (I don't plan on leaving it that way, but for now the firewall is disabled while I troubleshoot the current issue) Now everything works, add remove programs, updates manager and most websites. But still there are a number of web pages that say "transferring data" and never load. A couple examples are "www.hotmail.com" and "www.myspace.com" These pages just load forever and stay blank. Java and IPv6 were both present when the Internet worked fine, so I don't think they are the problem. (even though I have since disabled IPv6 with no results) I have since installed samba and can share Windows to Linux just fine, but not Linux to Windows for some reason.  *Sigh* Another day for that one, too.  But right now I really want a fully functional internet on Xubuntu. Suggestions anyone?

kernel: 2.6.20-16-generic

ifconfig reads:
eth0      Link encap:Ethernet  HWaddr 00:00:E8:B3:59:78  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2002:47c3:a767:4:200:e8ff:feb3:5978/64 Scope:Global
          inet6 addr: fec0::4:200:e8ff:feb3:5978/64 Scope:Site
          inet6 addr: fe80::200:e8ff:feb3:5978/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3882625 (3.7 MiB)  TX bytes:358091 (349.6 KiB)
          Interrupt:5 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.3 KiB)  TX bytes:4496 (4.3 KiB)

Ping to [www.myspace.com:](www.myspace.com:)
PING [www.myspace.com](www.myspace.com) (216.178.38.129) 56(84) bytes of data.
64 bytes from 216.178.38.129: icmp_seq=1 ttl=243 time=24.2 ms
64 bytes from 216.178.38.129: icmp_seq=2 ttl=243 time=23.8 ms
64 bytes from 216.178.38.129: icmp_seq=3 ttl=243 time=25.3 ms

--- [www.myspace.com](www.myspace.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10138ms
rtt min/avg/max/mdev = 23.880/24.508/25.397/0.646 ms

Ping to [www.hotmail.com:](www.hotmail.com:)
PING [www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net) (66.35.214.30) 56(84) bytes of data.
64 bytes from 66.35.214.30: icmp_seq=1 ttl=53 time=20.1 ms
64 bytes from 66.35.214.30: icmp_seq=2 ttl=53 time=18.7 ms
64 bytes from 66.35.214.30: icmp_seq=3 ttl=53 time=31.9 ms

--- [www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10201ms
rtt min/avg/max/mdev = 18.700/23.627/31.998/5.951 ms

I'd appreciate any help!

(sorry such a long post but I wanted to answer the obvious questions so they need not be asked ;) )

---

### Post by Thunar on 2007-09-23
anybody? :(

---

### Post by noob12 on 2007-09-23
I can see a bunch of inet6 addresses on your eth0, so you haven't actually disabled IPV6.  That may or may not have anything to do with this issue, but whatever you did to disable it wasn't complete.  If you want to disable it, let me know and I'll post back instructions.

My guess is you are having trouble resolving one of the referenced hostnames on those pages, not the top-level one.  That's a pretty blind guess on my part.  But you could try using OpenDNS servers following this HOWTO and seeing if it helps at all:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by Thunar on 2007-09-24
well I don't think ipv6 is the problem anyway, because when I connected directly there was no problem, but now that I am connecting through my Windows machine there are problems. I have since reinstalled and am now using Ubuntu 7.04, and have the same exact problem. (I do like the ease of use of Ubuntu compared to Xubuntu, btw) Still no Myspace, still no Hotmail. I am kind of thinking the problem must be with Windows at this point, so anyone with experience running Linux on a Windows network? 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:00:E8:B3:59:78  
          inet addr:192.168.0.242  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2002:47c3:a767:4:200:e8ff:feb3:5978/64 Scope:Global
          inet6 addr: fec0::4:200:e8ff:feb3:5978/64 Scope:Site
          inet6 addr: fe80::200:e8ff:feb3:5978/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1932366 (1.8 MiB)  TX bytes:985844 (962.7 KiB)
          Interrupt:5 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80024 (78.1 KiB)  TX bytes:80024 (78.1 KiB)

I'm supposedly running DHCP though I don't see how that's possible through a switch, as they do not forward addresses... *sigh*

I haven't tried the DNS thing yet, but if I am connecting through the local network doesn't the server, in this case my Windows machine, act as the DNS?

---

### Post by Thunar on 2007-09-27
Ok so I am still having this problem of Myspace and Hotmail not loading. I really don't think my DNS is the problem, unless someone can give me a good reason why, because basically almost every web page loads just fine. Only a very few have the problem. Also I am connecting through windows, so it seems to me that the windows machine would make the dns requests for me, therefor making the windows machine my dns server. Sharing between the two operating systems is now flawless both ways, with effortless sharing in both windows and linux, and I can even print to the USB printer connected to my windows machine from Linux. I'm thinking that maybe there's some protocol or service that windows is not allowing Linux to use that these sites require.

SO

Any suggestions?

---

### Post by adamonduty on 2007-09-28
You could try something like

$ wget [www.myspace.com](www.myspace.com)

And see what error messages you get.

---

### Post by Thunar on 2007-09-29
Ok the results of 'wget [www.myspace.com](www.myspace.com)' were:

--00:35:34--  [http://www.myspace.com/](http://www.myspace.com/)
           => `index.html'
Resolving [www.myspace.com](www.myspace.com)... 216.178.39.16, 216.178.38.131, 216.178.38.129, ...
Connecting to www.myspace.com|216.178.39.16|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--00:40:20--  [http://www.myspace.com/](http://www.myspace.com/)
  (try: 2) => `index.html'
Connecting to www.myspace.com|216.178.39.16|:80... connected.
HTTP request sent, awaiting response... 

whenever it says "awaiting response" it sits there and does nothing for quite a while before it says "Read error (Connection reset by peer) in headers.
Retrying."

so I'm not sure if Myspace is not responding to the request or if windows never forwarded it, or why it's resetting the connection... hmmm

Ok so here I'll try [www.hotmail.com:](www.hotmail.com:)

--00:48:28--  [http://www.hotmail.com/](http://www.hotmail.com/)
           => `index.html'
Resolving [www.hotmail.com](www.hotmail.com)... 64.70.45.46
Connecting to www.hotmail.com|64.70.45.46|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://mail.live.com/](http://mail.live.com/) [following]
--00:48:28--  [http://mail.live.com/](http://mail.live.com/)
           => `index.html'
Resolving mail.live.com... 207.46.10.121, 207.46.8.121, 207.46.8.249, ...
Connecting to mail.live.com|207.46.10.121|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=10&ct=1191052092&rver=4.5.2130.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&id=64855](http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=10&ct=1191052092&rver=4.5.2130.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&id=64855) [following]
--00:48:29--  [http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=10&ct=1191052092&rver=4.5.2130.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&id=64855](http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=10&ct=1191052092&rver=4.5.2130.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&id=64855)
           => `login.srf?wa=wsignin1.0&rpsnv=10&ct=1191052092&rver=4.5.2130.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&id=64855'
Resolving login.live.com... 65.54.179.203
Connecting to login.live.com|65.54.179.203|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,688 (3.6K) [text/html]

100%[====================================>] 3,688          1.42K/s    ETA 00:00

00:48:42 (267.74 B/s) - `login.srf?wa=wsignin1.0&rpsnv=10&ct=1191052092&rver=4.5.2130.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&id=64855' saved [3688/3688]

This one is different, because it actually gets to "Done" on the browser, but the page is blank. doh!

Linux is nothing if not full of challenges eh?

So any more ideas?

---

### Post by Thunar on 2007-09-30
anyone? ](*,)

---

### Post by j.bunce on 2007-10-02
This is a windows issue, not a linux one. Google Windows ICS (Internet Connection Sharing).

---

### Post by Thunar on 2007-10-03
Well I guess that's an easy way to feel not obliged to help. 

Hate to be a Windows Problem on an Ubuntu Forum, but I am a Graphic Designer who uses Photoshop, Illustrator, InDesign, Quark, Flash and many other programs NOT on Ubuntu, and I am not about to try to run them through Wine thank you very much. It was all I could do to get Diablo II to run on Wine. So if Ubuntu can't do something as simple as sharing an Internet connection with my Windows computer then it is pretty useless to me, isn't it?

Also, I see many posts about people networking with Windows, OS X and even other distos of Linux, and no one ever tells them to google it. Sorry to sound so pissed, but I'm not an idiot, don't you think that by now that maybe, just maybe, I've ALREADY googled it? Don't get me wrong, I am troubleshooting on Windows just as much as Linux. 

Besides, how can you be so sure? Tell me how you can be 100% sure it has nothing to do with Linux. Maybe it's the new NIC card I bought on Ebay. Maybe it's the network setup (I was connecting through USB, now I'm on Ethernet, so the Network settings are NOT the same anymore) There are just too many variables to write it off as Windows fault. I came here thinking that maybe someone here has had some experience using Windows and Linux together, and could provide some helpful advice.

Again I apologize for the tone, but I came here for help, NOT Google. :lolflag:

---

### Post by Lambert on 2007-10-03
Instead of typing the domain name ([www.myspace.com](www.myspace.com)) have you tried to enter the ip address of the sites into the address bar to see if the page loads?

Also open up network (from system->Administration->network) and see what's entered under the dns tab.

---

### Post by Thunar on 2007-10-03
Hey thanks for the reply :)

Yeah, I did try typing the ip address directly into the address bar of Firefox, and I got the same results. I also tried installing Epiphany and even Opera (which I really don't care for, but hey: All in the name of scientific elimination!), but these yielded the same results. So that kind of rules out both DNS and Browser. 

The only clue I seem to have come across is I've had pages tell me my browser is not redirecting properly, or doesn't support redirection. But most pages give me no trouble at all. Even "Yahoo! Beta" works perfectly for me.  I'm not really sure what would cause that, but it could be a symptom...

As for my DNS tab on the Network Settings it shows "192.168.0.1" which is my Windows ip address, and under "Search Domains" it says "mshome.net" (MSHOME is my windows group name)

Thanks again!

---

### Post by Lambert on 2007-10-03
What kind of internet connection are you using? DSL with pppoe? If so check this site.

[http://www.annoyances.org/exec/show/article04-107](http://www.annoyances.org/exec/show/article04-107)

To temporarily change the mtu on the linux pc, you run this command from terminal.

sudo ifconfig eth0 mtu ____

Enter the lower number that you found going through the steps find the mtu on your winxp pc. If this solves it you'll have to search on setting mtu permanently. You can google search mtu ubuntu or debian.

If you're not running pppoe and dsl, someone with advanced networking skills with both linux and windows will need to step in. It does look like it's more of a problem with winxp but I'm not 100% sure.

You can research network tracing programs and log the network traffic and see what's happening with the packets that are being sent/rec'd. But this is more advanced and maybe something simpler can be done.

---

### Post by jcliburn on 2007-10-03
> **Thunar said:**
> anyone? ](*,)

Your symptoms aren't *quite* the same as I've seen, but try this:

sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

Then see if you can access your stalled sites.

---

### Post by kevdog on 2007-10-03
Have you disabled ipv6???  Not sure this will help but its worth a try.

---

### Post by Thunar on 2007-10-06
Hey guess what everybody? It was Linux... 

..AND Windows, lol.

It was the MTU all along as suggested by Lambert:

> **Lambert said:**
> What kind of internet connection are you using? DSL with pppoe? If so check this site.

To temporarily change the mtu on the linux pc, you run this command from terminal.

sudo ifconfig eth0 mtu ____

Enter the lower number that you found going through the steps find the mtu on your winxp pc. If this solves it you'll have to search on setting mtu permanently. You can google search mtu ubuntu or debian.

I changed the MTU to 1492 and every website works like a charm now. Just so everybody knows, I am connected through Windows XP Professional and a Cable Modem, so this is not just  dial-up or PPPOE problem apparently. Also, I made NO MTU changes on WIndows whatsoever, so let's all not try to blame everything on Windows:lolflag:. 
That being said, I did have to make some fancy changes to my firewall settings in Windows to allow Ubuntu access to the Internet through the venerable Windows Firewall. So if anyone wants to know more info about that let me know and I'll be happy to walk you through the changes I made.

Lambert also mentioned that the "sudo ifconfig eth0 mtu 1492" command would only change it temporarily. So, does anyone know how to make the change permanent???

btw, a BIG thank you to everyone who responded to this post, I am very grateful for everybody's helpful advice! (even google, heh) :)

---

### Post by Lambert on 2007-10-06
Open the file /etc/nework/interfaces and edit it depending on which ip method you're using

If you're using a static ip just enter a line under the interface section that says

```

mtu 1492

```If you're using dhcp then add this under the interface

```

pre-up /sbin/ifconfig $IFACE mtu 1492

```

---

### Post by Thunar on 2007-10-06
Hey thanks again! This one worked for me:

```

pre-up /sbin/ifconfig $IFACE mtu 1492

```

I put this under the 

iface eth0 inet dhcp

section of

/etc/network/interfaces

using gedit as root like this (in terminal):

```

gksudo gedit

```

Now I have a completely unfettered Internet experience with Ubuntu. :popcorn:

This rocks! :guitar:

Hope this thread can help someone else with the same problem someday! :)

---

