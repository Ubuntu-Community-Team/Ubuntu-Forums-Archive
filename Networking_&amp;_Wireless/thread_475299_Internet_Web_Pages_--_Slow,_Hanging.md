---
title: "Internet Web Pages -- Slow, Hanging"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by sondo2121 on 2007-06-15
I am a new convert to Ubuntu 7.04 as well as a new linux user.  I recently installed, and was trying to browse the internet, and decided to go to intel.com.  Well, the page hung.  This was interesting.

I looked up some similar issues on the internet and found some with firefox, ipv6 and DNS.

I have done all of these fixes, and nothing has worked.
Some of these fixes include:

alias ipv6 off
alias net-pf-10 off
in the /etc/modprob.d/aliases file

I have this issue in other browsers.
I have also found out that I cannot get to support.dell.com and many other websites.

It seems to 'hang' on pages akamai content on it (a hosting service, content delivery)

All of my windows boxes can access all of the sites, although with Ububtu, I cannot.  The reason why I switched, was because linux has always supported about 1000x more than windows, I guess not this time.

Does anyone know what is going on?  Is this a DNS issue?  Ubuntu config issue?  IPV6 issue?


EDIT: I have this issue on my LAN and WLAN connection

---

### Post by PaulFr on 2007-06-16
I had the same problems and did three things: first, disabled ipv6 as you did; then disabled ipv6 in Firefox (set **network.disable.ipv6** to true in **about:config**) and finally changed my DNS server to opendns (see **[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)**). Worked wonders for me.

On another note, you can see if it is DNS causing your problems by running **dig** to lookup using DNS the sites causing you trouble like support.dell.com. For example, try running **dig support.dell.com** which should return quickly based on your network speed.

Hope this helps.

---

### Post by sondo2121 on 2007-06-16
That didn't work for me.  I have my own DNS server, which I disabled to test OpenDNS, and I am still having the same issues.  


I used OpenDNS settings in all of these combinations:

* On my router (gave them out VIA DHCP)
* On my DNS server (used them as forwarders)
* On my Ubuntu machine (hard coded them as prepends in the dhcp file)

The weird thing is that when I go to work, I can get to any website I please.  I guess this means that Iowa State University's network (for DNS) is set up correctly and mine is not?  This maybe the issue, although I don't know where to start.

---

### Post by sondo2121 on 2007-06-16
It is fixed now, I have rebuilt my router's config file (from factory default).

If any of you users out there have issues with Linksys routers and Ubuntu, I suggest starting from a fresh factory setting, and most current firmware.  Then do the IPV6 trick in both FF and in the config files.

I am also using OpenDNS in addition to my 3 other DNS servers and everything resolves great.

---

