---
title: "DLink ADSL router configuration"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by HeroVina on 2007-02-22
I am a newbie of Ubuntu.

After install the Edgy version, my DNS Servers list contains only 192.168.1.1. This works when I bring my laptop to the office (ie, I can access to Internet with no more configuring). When I use at home with the DLink 504T, I cannot access to Internet

Switch to Windows OS, the networking works fine with the same router configuring

Back to Ubuntu (at home), I change DNS Servers list to

208.67.222.222
208.67.220.220

then I can access to Internet, but this modification is auto cleaned after about 15 minutes when the /etc/resolv.conf file is overwritten. At this time, my DNS Servers list is auto-reset to be 192.168.1.1 and I again cannot access to Internet 

My confusing are:
- Is the problem from Ubuntu installation ? If Yes, why I can connect from my office ?
- Is the problem from my home router configuration ? If Yes, why I can connect from Windows OS ?
- Is there any configuration wrong ? How to fix ?

Thank you very much.

---

### Post by ubunutgoz on 2007-02-22
Hi...

I am having the same trouble as you and it is driving me nuts.  I have done the DNS thing, and yes, it resets after 15 mins.  Thus that is not a solution, its a quick workaround.  

For simple internet access with firefox, have you disabled ipv6?  It'll get Firefox working, but won't get all the other stuff (security updates / application installation) going!

FYI, links to my other threads 

[http://ubuntuforums.org/showthread.php?t=367508&page=2](http://ubuntuforums.org/showthread.php?t=367508&page=2)
[http://www.ubuntuforums.org/showthread.php?p=2194648#post2194648](http://www.ubuntuforums.org/showthread.php?p=2194648#post2194648)


Please post any solutions you come across
Thanks
Alan

---

### Post by esacre on 2007-02-22
The fastest and easiest solution, I think

1.Firefox : disable ipv6 -> about:config in the adress bar, search for ipv6 and change the default setting

2.the rest of the box (update,....). Go to network config, disable dhcp for the ethernet card you use, set an fixed ip. Then go to dns server and there put first the 2 open dns address ([www.opendns.com](www.opendns.com)) and after the 2 dns from you isp.

It's done and everything is working fine.
Ok you loose dhcp but for a home networking with no more than 1 to 5 pc, it's not a problem.

Manu

---

### Post by Rui Pais on 2007-02-23
> **Ubunutzgoz said:**
> Hi...

I am having the same trouble as you and it is driving me nuts. I have done the DNS thing, and yes, it resets after 15 mins. Thus that is not a solution, its a quick workaround.

For simple internet access with firefox, have you disabled ipv6? It'll get Firefox working, but won't get all the other stuff (security updates / application installation) going!

FYI, links to my other threads

[http://ubuntuforums.org/showthread.php?t=367508&page=2](http://ubuntuforums.org/showthread.php?t=367508&page=2)
[http://www.ubuntuforums.org/showthre...48#post2194648](http://www.ubuntuforums.org/showthre...48#post2194648)


Please post any solutions you come across
Thanks
Alan

Ubunutzgoz, you should have replied on [your previous thread]("http://ubuntuforums.org/showthread.php?t=367508")... 

If your /etc/resolv.conf is overwritten you can [do this]("http://opendns.com/start/ubuntu.php") (from the link i posted before). 

hth

---

