---
title: "Internet Connection"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by almostalive on 2007-09-11
hi, I don't know much about networking, so I need help,

I'm trying to access the internet on Ubuntu, and don't really know how to configure the network settings

I have an ethernet connection, and I'm connected to an ActionTec dsl modem/router, which uses DHCP
when I open firefox, the status bar says "Connecting to Google.com" it never times out, it just keeps trying to load (same with all websites)
also not able to connect to the internet via Gaim or other apps

yet, when I open the Terminal, and I ping websites, I get responses
I can also access my router fine, via 192.168.0.1

this is what I get when I use the 'wget' command;
```

jim@Jim-Ubuntu:~$ wget msn.com
--18:04:18--  http://msn.com/
           => `index.html'
Resolving msn.com... 207.68.172.246
Connecting to msn.com|207.68.172.246|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.msn.com/ [following]
--18:04:23--  http://www.msn.com/
           => `index.html'
Resolving www.msn.com... 1.0.0.0
Connecting to www.msn.com|1.0.0.0|:80... failed: Network is unreachable.

```

this is what I have in Network Settings;
**Connections tab** = Ethernet Connection is activated, configured for DHCP
**General tab** = Hostname "Jim-Ubuntu"
**DNS tab** = dns servers: 192.168.0.1, 205.171.3.65 (my router and public IP) Search Domains: domain.actdsltmp
**Hosts Tab** = I think this tab is irrelevant

I'm dual booting with Windows, and can access the internet fine there, so my internet line isn't the problem
can anyone help me out? I have no idea what I'm doing wrong.

bare with me, first day running Ubuntu,
thanks for any help :)

EDIT: apparently, I'm able to access some websites.. I just tried gov.org, and the page loaded. however, I still can't access yahoo.com, google.com, msn.com, ect... the connection just hangs and doesn't load
is there a way to clear DNS cache? maybe that will help?

---

### Post by almostalive on 2007-09-11
aw.. no response?

:( can't anyone help

---

### Post by noob12 on 2007-09-12
I'm not understanding why one of your DNS servers is returning 1.0.0.0 as the address of msn.com in your wget session.  That certainly breaks things.  The first resolution of the same name is fine.  I am not sure if this is due to the router's built-in DNS proxy or the second server in the list.  You could also have a lame proxy set.

Check that you have direct internet connection set in System | Preferences | Network Proxy.

Try typing **host [www.msn.com](www.msn.com)** a couple of times and seeing if you get a legitimate address back each time.

See if you get better behavior with **wget --no-proxy [http://www.msn.com/](http://www.msn.com/)**

If none of these work, try power-cycling the router.

If all of those don't work, try using the OpenDNS servers as in the first section of this HOWTO [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) and see if it improves things for you.

---

### Post by almostalive on 2007-09-12
> Check that you have direct internet connection set in System | Preferences | Network Proxy.
I do

> Try typing host [www.msn.com](www.msn.com) a couple of times and seeing if you get a legitimate address back each time.
I get this each time;
```
jim@Ubuntu:~$ host www.msn.com
www.msn.com is an alias for www.msn.com.nsatc.net.
www.msn.com.nsatc.net has address 65.54.152.126
;; Warning: Message parser reports malformed message packet.
www.msn.com is an alias for www.msn.com.nsatc.net.

```

> See if you get better behavior with wget --no-proxy [http://www.msn.com/](http://www.msn.com/)
this is what I get:
```
jim@Ubuntu:~$ wget --no-proxy www.msn.com
--13:43:32--  http://www.msn.com/
           => `index.html'
Resolving www.msn.com... 65.54.152.126
Connecting to www.msn.com|65.54.152.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38,545 (38K) [text/html]

100%[====================================>] 38,545       203.51K/s

13:43:35 (203.17 KB/s) - `index.html' saved [38545/38545]

```
 it seems to work.. does this mean I have a proxy on or something..? 'cause i only installed Ubuntu yesterday, I didn't mess with any proxy settings

> If none of these work, try power-cycling the router.
tried this also

I still can't access/browse websites, or connect to Gaim

I'm trying to follow the tutorial at: 
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)
to be able to setup Local DNS Caching. do you think this would really help me?
when I try to install it, it says the dnsmasq package cannot be found.

thanks for responding. I just want to get on the internet! :-/

---

### Post by almostalive on 2007-09-12
* bumping my thread cause it got knocked off the front page again.

can anyone help me?

I'm using Ubuntu 6.06 if that matters to anything

EDIT: I found this thread, it seems to be a similar problem to mine
[http://ubuntuforums.org/showthread.php?t=549516](http://ubuntuforums.org/showthread.php?t=549516)
I will try the solution they suggested, (using opendns.com) and see how that goes.

---

### Post by almostalive on 2007-09-12
okay, the problem is fixed. I'm typing this from Ubuntu :)
all I did was use opendns.com as my dns server

---

### Post by rujmah on 2007-09-26
Thanks for that Noob12. I was trying to figure out how to set up a system proxy for ages until I saw your post.

Cheers!
~R

> **noob12 said:**
> I'm not understanding why one of your DNS servers is returning 1.0.0.0 as the address of msn.com in your wget session.  That certainly breaks things.  The first resolution of the same name is fine.  I am not sure if this is due to the router's built-in DNS proxy or the second server in the list.  You could also have a lame proxy set.

Check that you have direct internet connection set in System | Preferences | Network Proxy.

Try typing **host [www.msn.com](www.msn.com)** a couple of times and seeing if you get a legitimate address back each time.

See if you get better behavior with **wget --no-proxy [http://www.msn.com/](http://www.msn.com/)**

If none of these work, try power-cycling the router.

If all of those don't work, try using the OpenDNS servers as in the first section of this HOWTO [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) and see if it improves things for you.

---

