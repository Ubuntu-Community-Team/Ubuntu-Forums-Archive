---
title: "hosts file ad-blocking"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by stepore on 2005-04-15
just upgraded to hoary and for some reason i can't get the /etc/hosts file to block ads in any browser. i've always used the hosts file to block ads. but for some reason it's not working.

permissions on the file are thus:
-rw-r--r--  1 root root 43065 2005-04-14 22:20 /etc/hosts

and the file itself is like this, /etc/hosts:
127.0.0.1 localhost.localdomain localhost ubuntu-shine

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# Ad server list for use with hosts files to block ads
#
# last updated: 2005-04-06 16:59:37

127.0.0.1 007arcadegames.com
127.0.0.1 101order.com
127.0.0.1 123banners.com
127.0.0.1 123found.com
127.0.0.1 180searchassistant.com
127.0.0.1 180solutions.com

etc, etc. it keeps going on like that. why doesn't it work with ubuntu. neither firefox, mozilla or konqueror get ads blocked. i know there are other ways to block ads, especially for the mozillas, but i'd like to get this to work.

anyone get the hosts file to work, blocking ads?

---

### Post by heimo on 2005-04-15
I think what's going on here is that your system is using DNS as primary way to solve names and skips the hosts file. You can change the order in */etc/resolv.conf* with line something like: *order hosts, bind*
 
You can check the syntax with *man resolv.conf*
 
Hopefully this helps. :)

---

### Post by stepore on 2005-04-16
maybe you meant /etc/host.conf?

mine already reads:
ubudeshine@ubulin-shine:~$ cat /etc/host.conf
order hosts,bind
multi off

ubuntu still seems to ignore the hosts file. 
anything else i can try?

---

### Post by heimo on 2005-04-16
Hmm..  Yeah, it's the host.conf, not resolv.conf. I tried adding some hosts to /etc/hosts - then tried to ping those sites and got replies from localhost, as expected.  Then I added ubuntu.com to blocked sites and tried browsing in Firefox, and the site loaded normally.

Now what's happening here is dns resolver cache. Applications cache dns queries for better performance. It took couple minutes to take effect. (maybe there's a way to flush that cache, but it time takes care of it, too).

However, if those ads are fetched using IP addresses, this approach of ad blocking won't work - this approach requires host names to be used in urls. :-/

If you do 'ping 180solutions.com'. do you get responses from 127.0.0.1? You should. But if you do 'dig 180solutions.com' you'll still get the real ip address, as this bypasses hosts file.

Have you checked that those ads which still appear have hosts names in their urls and those host names are listed in your hosts file?

---

### Post by stepore on 2005-04-18
i added ubuntu.com and yahoo.com and it blocked them, so i guess it is working afterall, but lots of ads are still getting through. maybe i don't have the most updated hosts file. guess i need to keep looking.

cheers,
jb

---

### Post by JGJones on 2005-11-06
This remind me of this which you will find quite useful instead of updating yourself:

Ad blocking in hosts file:

[http://www.everythingisnt.com/hosts.html](http://www.everythingisnt.com/hosts.html)

(also available for windows)

---

### Post by poptones on 2005-11-06
Have you restarted your machine? Any domains with their DNS cached are still going to resolve until you restart (or at least flush the cache).

FWIW, all it takes is "sudo apt-get install privoxy" and you get a much more convenient solution. Pages display better and you still have the option of "going there" with a single click if a page you want to visit is blocked.

---

### Post by nixclusive on 2006-02-03
Looks like I've left MS for good now :)

I tested the hosts file which successfully blocked the specifies domain names but I ended up with a considerably slow performance as the browser keeps on waiting for the domain name to be resolved. It looks like it gets stuck whenever it a page points to an entry in the hosts file. Any solutions?

---

### Post by MttJocy on 2008-02-17
> **nixclusive said:**
> Looks like I've left MS for good now :)

I tested the hosts file which successfully blocked the specifies domain names but I ended up with a considerably slow performance as the browser keeps on waiting for the domain name to be resolved. It looks like it gets stuck whenever it a page points to an entry in the hosts file. Any solutions?

It's not the resolution that is making this slow, what is happening is you are directing these pages to your own computer which causes firefox to try to connect to your computer on port 80, this will fail unless you have a webserver running however it takes time before it fails, one way to fix this is to put a simple webserver on your machine that only listens on 127.0.0.1 (so it can't be exploited from the internet or otherwise be a security risk) this way when firefox tries to get the ad it will immediately receive a 404: Not Found HTTP error causing it to instantly give up and go on to load the next objects on the page.

---

### Post by HermanAB on 2008-02-17
The best solution to block crud, is Squid-cache and SquidGuard (or Dans Guardian).  If you set it up on a firewall machine, then it will clean up and speed up the internet for everybody on your LAN.

---

### Post by Arthur Archnix on 2008-02-29
> **nixclusive said:**
> Looks like I've left MS for good now :)

I tested the hosts file which successfully blocked the specifies domain names but I ended up with a considerably slow performance as the browser keeps on waiting for the domain name to be resolved. It looks like it gets stuck whenever it a page points to an entry in the hosts file. Any solutions?

I'm trying to figure out how to do to this myself. I read that if you point to 1.2.7.0.1 or whatever it will wait a bit hoping to hear a response. You need to change your hosts to point to 0.0.0.0 or something. Still looking into it.

---

