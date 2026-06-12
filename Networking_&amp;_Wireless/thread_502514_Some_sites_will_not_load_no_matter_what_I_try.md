---
title: "Some sites will not load no matter what I try"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by analogline on 2007-07-16
After reading many posts like this, some people are going to think I'm beating a dead horse.  However, I'm at my wit's end with Feisty Fawn on this score, and posting here is my last gasp for help before I try something else.

Downloaded the latest version, and I'm having the oft-reported issue of some websites working fine (like this one) and some hanging halfway through (like slashdot.org)

Any other means of connection works fine, just web browsing, and web browsing alone hangs, no matter what web browser I try on slashdot.

I can dig slashdot.org, and images.slashdot.org (which is the site that Firefox claims it is waiting for) with no problems, my DNS responds quite fast.  However, trying to browse there through ANY web browser will hang me up.  Even lynx, which sits at "HTTP/1.1 200 OK" forever.

I've tried all the IPv6 disabling tricks that I've been able to find on this place and none of it appears to have helped at all.  In Firefox, network.dns.disableIPv6 is set to true.  IPv6 does appear to be actually disabled.  I've rebuilt the router and DSL modem from factory default, I've rebooted the switch it's plugged into.

I really don't know what else I can try.:confused:

---

### Post by dreadlord_chris on 2007-07-16
> **analogline said:**
> After reading many posts like this, some people are going to think I'm beating a dead horse.  However, I'm at my wit's end with Feisty Fawn on this score, and posting here is my last gasp for help before I try something else.

Downloaded the latest version, and I'm having the oft-reported issue of some websites working fine (like this one) and some hanging halfway through (like slashdot.org)

Any other means of connection works fine, just web browsing, and web browsing alone hangs, no matter what web browser I try on slashdot.

I can dig slashdot.org, and images.slashdot.org (which is the site that Firefox claims it is waiting for) with no problems, my DNS responds quite fast.  However, trying to browse there through ANY web browser will hang me up.  Even lynx, which sits at "HTTP/1.1 200 OK" forever.

I've tried all the IPv6 disabling tricks that I've been able to find on this place and none of it appears to have helped at all.  In Firefox, network.dns.disableIPv6 is set to true.  IPv6 does appear to be actually disabled.  I've rebuilt the router and DSL modem from factory default, I've rebooted the switch it's plugged into.

I really don't know what else I can try.:confused:

That's pretty wierd....

I have absolutley no problems like this - slashdot opens in a snap for me in both Firefox & Opera
Are you sure this isn't an issue with a filter-proxy at your ISP?

---

### Post by analogline on 2007-07-16
Unless it's checking to see that I'm using a Linux machine to do it from.  The same machine works fine in Windows, no problems to slashdot or anywhere else.  A Mac plugged into the same switch works fine.  2 other Macs plugged into the same router work fine.

Slashdot isn't the only site I get it hanging mid-page on, but it's the easiest to test on.  (I generally use it to test network connectivity, since most of my clients just don't use it)

---

### Post by NilsE on 2007-07-16
Try opening up the images on the bottom of this web site and see if you are getting hung up on any particular images.  It's a long shot but a long time ago I was having a hard time opening some images.

[http://www.linspire.com/file_types/filetypes.php](http://www.linspire.com/file_types/filetypes.php)

I actually like this page for testing various functions when I do any kind of changes.

---

### Post by analogline on 2007-07-16
I don't have any problems loading anything on that page.  Not even the links to the few that I've tried.

---

### Post by analogline on 2007-07-16
As some additional info, I just checked that Firefox is downloading the full source of the slashdot webpage.  It is just hanging when trying to pull up the stuff at the images.slashdot.org site.

This is happening at other pages where I'm having problems.  It starts loading part of the page, then when it gets to something from another site it hangs everything.

---

### Post by Mr. C. on 2007-07-16
Two things to suggest:

1) check your /etc/resolv.conf file to see if your router is the first nameserver listed.  If so, use your ISPs nameservers.

2) See my first post here:

[http://ubuntuforums.org/showthread.php?t=477659&highlight=mrc+tcp&page=2](http://ubuntuforums.org/showthread.php?t=477659&highlight=mrc+tcp&page=2)

MrC

---

### Post by analogline on 2007-07-16
My router isn't in my resolv.conf at all.  I checked that, put in opendns servers in case my ISP's dns was screwed up, nothing.

Edit:  Tried the links in your second suggestion.  One of them hung on me.  Tried the TCP window scaling stuff, kept giving me Permission Denied until I enabled root.  Once I did that, it let me run what the first link called the "nice" way of doing it "echo 0 > /proc/sys/net/ipv4/tcp_window_scaling" and slashdot came directly up for me.

Thanks so very much!  

May want to add that root would need to be given a password for those commands to work, the next time some poor soul like me is about to throw his monitor out the window.  =/

---

### Post by Mr. C. on 2007-07-17
That's great news!

I'll update my post; thanks for the feedback.

MrC

---

### Post by analogline on 2007-07-17
OK, well, a bit of reading and some lockups later, that doesn't persist through reboot, and isn't the "nice" option, but the 10 ton hammer option.

The one that works through reboot is adding 

net.ipv4.tcp_rmem = 4096 65536 65536
net.ipv4.tcp_wmem = 4096 65536 65536

to the end of /etc/sysctl.conf

---

### Post by Mr. C. on 2007-07-17
Right.  The changes are for the current boot only.  The kernel settings need to be applied each boot.

MrC

---

### Post by Waqas M on 2007-10-16
I am having a similar problem, sites such as slashdot or adobe will not load, I have tried some of the solutions given like disabling ipv6 but without success. I can connect to these sites using windows on the same machine.
I am connected through my university network and do not have access to the router.

---

### Post by siknux on 2007-10-22
My english is awful and I have just registered to this forum to thank you. I was going mad. Same error. Same tries. No success... till now! Thank you!

---

### Post by siknux on 2007-10-22
> **Waqas M said:**
> I am having a similar problem, sites such as slashdot or adobe will not load, I have tried some of the solutions given like disabling ipv6 but without success. I can connect to these sites using windows on the same machine.
I am connected through my university network and do not have access to the router.

Waqas M, try this:

sudo -su (and hit enter)
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

(check any website that didn't work)

If it works add:

net.ipv4.tcp_rmem = 4096 65536 65536
net.ipv4.tcp_wmem = 4096 65536 65536

to the end of /etc/sysctl.conf.

If not, continue digging

---

