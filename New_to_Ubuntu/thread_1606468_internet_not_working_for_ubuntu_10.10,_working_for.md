---
title: "internet not working for ubuntu 10.10, working for windows xp"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by rodrickhales on 2010-10-26
Hello.  I have recently installed Ubuntu 10.10 on the same machine with Windows XP (dual boot).  I really want to get to know and like Linux better.

Let me start by saying, I have looked in the forums, help.ubuntu.org, and the net for solutions.  I  still have no stable connectivity from ubuntu 10.10.  It seems I am having no problem with transmission but with reception as it is at 0%.  However when I start Firefox, I can go to Google and do searches and check gmail but anything outside of Google.com it just either waits or times out on the connection.

My plans were originally to have it wired to my Linksys router (model: WRT-110).  I have since bypassed it with a connection directly to the cable modem.  After several restarts, it still works with Windows XP and not in Ubuntu 10.10.  I am at a loss here and I have been at this for a couple of days now.  I just want it to use DHCP just like Windows. Any suggestions would be greatly appreciated.  Thanks.

---

### Post by d3v1150m471c on 2010-10-26
10.10 maverick meerkat is still in beta stage. if you're using ubuntu as a first experience use 9.10 ( my personal favorite) or 10.4

---

### Post by Verbeck on 2010-10-26
> **d3v1150m471c said:**
> **10.10 maverick meerkat is still in beta stage.**

WTF!!!!?????

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by d3v1150m471c on 2010-10-26
if it's not then i'm obviously out of the loop. last i checked it was still being tested. either way, try 10.4 and 9.10 and see how it works out. i strongly recommend playing around on the live cd before installing to check for hardware incompatibilites in the future.

---

### Post by d3v1150m471c on 2010-10-26
"The final stable version will be released on October 10, 2010." - lol close but no cigar.

---

### Post by Verbeck on 2010-10-26
isn't today supposed to be October **26**th? :confused:  lol
edit:nvm

---

### Post by Apot on 2010-10-26
As far as I know it is stable.
Not a major release but still a stable release

---

### Post by d3v1150m471c on 2010-10-26
no, i've decided it's october the 9th ;)

---

### Post by ajgreeny on 2010-10-26
Try all of them: 9.10, 10.04 and 10.10 if you get an opportunity and then install the one that works best with your hardware.

In my case 10.10 has solved several problems that I had with 9.10 and 10.04 display, both needing 16 bit colour until I had tweaked xorg and the kernel version in 10.04 and finally got it running properly.

For me, with an ATI 9200SE video card, a sempron 2400+ and 2GB ram, 10.10 is about as near perfect as I've seen for some time.

Give it a whirl and you may find the same.

---

### Post by rodrickhales on 2010-10-26
ok. i will try 10.04 since it is available for download.  i really want this to work so wish me luck:)

---

### Post by rado1 on 2010-10-27
on the menu bar right click on the connections -> edit connections, choose wired then edit and try enable ip6 with automatic DHCP, works for 10.04, 10.10

---

### Post by rodrickhales on 2010-10-27
> **rado1 said:**
> on the menu bar right click on the connections -> edit connections, choose wired then edit and try enable ip6 with automatic DHCP, works for 10.04, 10.10

Alright I will give that a shot since 10.04 failed to connect to the internet after installing.  You know a lot of people on here were talking about disable or ignoring ipv6.  Something is bound to give.  It works fine in Windowz.

---

### Post by primaxx on 2010-10-27
I used to have a similar problem on an older version of Ubuntu, but my problem was related to DNS.

Have you tried this solution?
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9979446&postcount=8]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9979446&postcount=8")

Good luck!

Rgrds, Primaxx

---

### Post by Perseverance on 2010-10-27
Common issue lately. Again the solution :
Change your dns to the first one stated here [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

In your firefox browser at the address bar write about:config and search for network.dns.disableIPv6 and set its value to True. There are some guides that show how to disable IPv6 system-wide but i do not consider it good idea.

> **primaxx said:**
> I used to have a similar problem on an older version of Ubuntu, but my problem was related to DNS.

Have you tried this solution?
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9979446&postcount=8](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9979446&postcount=8)

Good luck!

Rgrds, Primaxx

Google DNS are not running properly for some internet providers , so it could work and yet it could not work. The site will calculate the fastest dns for his provider and IP

---

### Post by primaxx on 2010-10-27
> **Perseverance said:**
> Common issue lately. Again the solution :
Change your dns to the first one stated here [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)
Fantastic tool, will be bookmarked! :-)

---

### Post by rodrickhales on 2010-12-28
> **Perseverance said:**
> Common issue lately. Again the solution :
Change your dns to the first one stated here [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

In your firefox browser at the address bar write about:config and search for network.dns.disableIPv6 and set its value to True. There are some guides that show how to disable IPv6 system-wide but i do not consider it good idea.



Google DNS are not running properly for some internet providers , so it could work and yet it could not work. The site will calculate the fastest dns for his provider and IP

OK.  So I changed the network.dns.disableIPv6 in Firefox.  Changing the DNS was kind of tricky though. Did I mention that google.com, youtube.com, w3schools.com resolve quickly.  Although I could not download adobe flash player. I guess what I am experiencing is selective resolving.  This is strange:|  Still no consistent resolutions.  All I am wanting is the internet to work and I think everything will be OK with Ubuntu.

note: i have tries both 10.4 and 10.10: same difference.

---

### Post by rodrickhales on 2011-01-04
SOLVED! Went to edit connections and renamed connection from 'auto eth0' to 'eth0'.  What a dirty trick to play on someone!  Thanks a lot everyone that responded.

---

### Post by rodrickhales on 2011-01-04
Was solved when I renamed 'Auto eth0' to 'eth0' ... spoke to soon.  I  rebooted and back to square one. Partially loading pages (if any  loading).  Open to more suggestions.  Thanks.

---

