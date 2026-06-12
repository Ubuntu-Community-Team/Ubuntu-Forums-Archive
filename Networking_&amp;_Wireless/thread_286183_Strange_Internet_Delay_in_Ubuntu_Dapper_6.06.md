---
title: "Strange Internet Delay in Ubuntu Dapper 6.06"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by R3V on 2006-10-27
Hi, I'm new here to the forums.  I've been using Ubuntu Dapper 6.06 for about a month or two now and have to say that I love it.  I used to be a dedicated RedHat/Fedora user, but after some problems I had with the newest version of FC, I decided to switch to Ubuntu.  Ubuntu has worked smoothly, except for one problem...

Ever since I first installed Ubuntu, I have had this strange delay whenever I attempt to access the internet.  Every website I would visit took at least 10 seconds to load.  I did some surfing on the net and discovered that it may have something to do with resolving dns names.  In an attempt to fix the problem, I disabled ipv6 and then followed instructions [here]("http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/") to configure DNSMasq to run a local DNS cache.  These two steps worked wonders and fixed my problem, except for a few websites here and there, such as dictionary.com, that would still load slowly.  I was willing to put up with that though, until recently...

No idea why, but I've started having the original problem all over again.  Nearly all websites load terribly slow, and it's making it an absolute pain to use the internet on Ubuntu.  No matter what, whenever I access the internet I experience a painful delay of 10 to 15 seconds.  I have absolutely no idea what is causing the problem.  I believe it may still have something to do with DNS resolving since a local DNS cache really helped, but I'm not entirely sure.  Maybe it has something to do with DHCP and my router.  It seems that if I restart Ubuntu a couple of times, it can somewhat lower the delay, but the delay is still there.  Strangely one website still manages to load fast, which is Google.  No idea why that is...

I don't experience this problem on Windows at all, so I know it's something directly in Ubuntu that is causing the problem.  I really hope someone can be of some help because this is making me want to pull my hair out.  The majority of my time spent on the computer is on the internet, so this delay is making my PC experience a nightmare.  Thanks so much for reading and hope someone can help soon!

---

### Post by mingoes on 2006-10-27
What browser do you use?
My problem was fixed after disabling ipv6 in Firefox.
(about:config -> set network.dns.DisableIPv6 = True)

---

### Post by R3V on 2006-10-27
I use both the Firefox that comes with Ubuntu and Galeon.  I experienced the same problem in both browsers.  It's not a browser-only problem but a problem with accessing the internet itself, regardless of what program I'm using.

I also disabled IPv6 by editing /etc/modprobe.d/bad_list and adding "alias net-pf-10 off".

---

### Post by R3V on 2006-10-27
I just seperately disabled IPV6 in FireFox and it did the trick!  All websites seem to load perfectly fine now.  The only problem is that it still does it in Galeon and other applications.  The step I took before was supposed to disable IPV6 throughout Ubuntu, but I guess for some reason it didn't...

Well, at least I know the problem was IPV6.  Anyone know if what I did to initially disable IPV6 was incorrect?  Or maybe Galeon just somehow overrides the badlist file I created.  Not sure...

Anyways, thanks for the tip.  It worked well.

---

### Post by stream303 on 2006-10-28
I would love to see your /etc/resolv.conf file.

Had this timeout problem in the past when the router's internal dns server would delay before you get to your isp's server if the router's address is the first one in the list.  If so there is a fix....

---

### Post by xargonax on 2006-10-30
I have exactly the same problem. I disabled the ipv6 module, set the firefox variable not to use ipv6 and also removed all the ipv6 host names and loopback. However the problem still appears, although less frequently. For me it mainly occurs when accessing an internet page through http. Pinging, intranet, ssh, etc all work perfectly well in both directions. ](*,)

---

