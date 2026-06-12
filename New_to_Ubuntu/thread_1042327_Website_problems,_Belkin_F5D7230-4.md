---
title: "Website problems, Belkin F5D7230-4"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by nonothing on 2009-01-17
Hey everybody...

I'm having problems connecting to certain websites with my router, but only in ubuntu (intrepid) and xubuntu (eeepc intrepid)...my roomate has a Vista laptop that connects to all sites properly.  When I try to connect to MSN, facebook, Myspace, yahoo or a few others, none of the formatting or images load, just the text and nothing more...almost as though it ignores the CSS or something.  Happens in firefox and opera.


If i remove the router entirely, and access straight from the wall, I can access fine...but my roomate can use the router fine so it's something with Ubuntu and the router... The router's a Belkin F5D7230-4, and I have no idea what's causing this.  I have two laptops, and this is happening with both of them.  I'm still pretty new at all this, so I'm not sure how to diagnose the problem...any help would be appreciated!

---

### Post by nonothing on 2009-01-17
bump...anybody?

---

### Post by zebbers on 2009-01-17
Did you try resetting?

---

### Post by chriscross93 on 2009-01-17
It could just be a coincidence that it always work for said roommate and not you.  I've had and seen the same problem with belkin routers (they overheat easily).  But lets assume that the router is fine and rule out the easier to diagnose stuff first...

Questions-

Are you plugged into said router or connected wirelessly?


Is your roommate plugged into said router or connected wirelessly?

What network manager are you using in ubuntu, is it something other than the default?

Open up the terminal (applications->accesories->terminal) and post the output if "ifconfig" (copy/paste whats in the quotes, leaving the quotes out).

---

### Post by nonothing on 2009-01-18
I did try resetting.  

My issue comes up whether hardlined to the router or not. 
He is able to access fine whether hardlined or not. 

I am not at home where the router is at the moment, I will be tomorrow.  Right now, I can access everything fine, wireless, using a Linksys router at a different location.  

Though I am not at home, this is my ifconfig output (i think should be default, I know I never changed on either laptop)

eth0      Link encap:Ethernet  HWaddr 00:1d:72:ce:6d:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27996 (27.9 KB)  TX bytes:27996 (27.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:69:7e:e3:bb  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe7e:e3bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:311077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:324578053 (324.5 MB)  TX bytes:126755121 (126.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-69-7E-E3-BB-33-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Again, though, this is while connected to a different router, if that matters...when I get back home will post the output (if different)

---

### Post by nonothing on 2009-01-19
Output was the same when connected to the other router...I don't actually know what that was, except it looked like hardware output so I wouldn't expect it to change anyway.  

Another note: it's a spotty problem, sometimes some pages that I want to go to will load once or twice, but eventually the site 'dies'.  I assume that's a cookie/cache issue, in a good way...my computer saving the correct format; it's not like I clear the cookies and cache when things are working right, you know?  

On a related note, yes, I've tried clearing cookies and cache, tried using a different browser, and like I said this happens on 2 different laptops...tried resetting the browser, tried changing router settings and tried resetting using the button back to factory defaults.  Normally it has WPA security, but I have everything that can be turned off turned off right now, so there is no security, nor firewall.  

I'm not really...competent with the terminal, which is part of why I can't really diagnose this on my own, so any thoughts would be appreciated!

---

### Post by nonothing on 2009-01-30
bump.  Anybody have any thoughts?

---

