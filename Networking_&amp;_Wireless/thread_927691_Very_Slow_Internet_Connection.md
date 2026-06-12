---
title: "Very Slow Internet Connection"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by dotarts on 2008-09-23
Hello!

I have recently installed ubuntu 8.04.1 distro to my AMD64 and noticed exactly the same problem as before: very slow internet connection. I have installed 3 OS on the same PC: XP / Vista and ubuntu. in Windows there's no problem at all, but in exactly the same environment (HW, Wired connection, ADSL modem, etc. )

What is the root cause of the problem and how to fix it ? 

Thanks, 
Alex

---

### Post by vip3r87 on 2008-09-23
same issue here, windows on my IBM TP A30, firefox was quick as hell...went to Ubuntu, and its slow...I have tried so many tweaks but nothing seems to work! Grrr

---

### Post by superprash2003 on 2008-09-23
is it slow browsing speed or slow downloading speed?

---

### Post by vip3r87 on 2008-09-23
slow browsing for me


EDIT* Definately browsing speed, im on my college network, and on my windows desktop its insanely fast, just did a speedtest.net test on my laptop(running ubuntu), and got:
10543 kb/s download
16949 kb/s upload

whats up? Also, on the speedtest.net website it was very slow loading/glitchy...video driver problem?
[[IMG]http://www.speedtest.net/result/327986246.png[/IMG]](http://www.speedtest.net)

---

### Post by deffy-swe on 2008-09-23
I read somewhere in this forum that turning off ipv6 (unless you're using it) in both mozilla-firefox and in Ubuntu could speed-up your web-browsing.

Just do a search for it and you will find it.
Check that out, might be worth a shot

---

### Post by vip3r87 on 2008-09-23
turned it off in ubuntu, going to try it in firefox now

---

### Post by vip3r87 on 2008-09-23
FIXED** :)

Downloaded and installed dnsmasq, then opened System->Administration->Networks. Went to the DNS tab, added the IP 127.0.0.1 to the top of the list, and bang! just like that it works!

Idea came from:
[http://http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/]("http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/")

Followed the post #1 from Limulus:
> ...- Install dnsmasq with Synaptic
- go System -> Administration -> Networking
- click the DNS tab
- press the Add button and type 127.0.0.1 and press enter
- click on a different entry so that 127.0.0.1 isn&#8217;t highlighted and then click and drag 127.0.0.1 to the top of the list
- press OK and you&#8217;re done! :-)

---

### Post by dotarts on 2008-09-24
Thanks! 
I'll try it today and let you know if this trick helps for me. 

Regards, 
A.

---

### Post by vip3r87 on 2008-09-24
if possible do what was said by the original poster...if not everytime you reboot you will have to add 127.0.0.1 to the DNS settings. Hope it works for yah!

---

### Post by dotarts on 2008-09-26
Hey, 

I have tried this hack, but it seems this is not the solution for the problem and just workaround of it, which does not really help.

Do you know what is the root cause of this issue in Ubuntu ? If you know that, then it might be possible to fix, unless you have to buy a support from "Professional support services from Canonical Ltd"  to get rid of that :-)

:confused:

Regards, 
Alex

---

### Post by dotarts on 2008-09-26
Prepare popcorn & Cola to view this movie: 

[http://video.google.com/videosearch?q=ubuntu+slow+internet+connection&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&sa=X&oi=video_result_group&resnum=4&ct=title#](http://video.google.com/videosearch?q=ubuntu+slow+internet+connection&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&sa=X&oi=video_result_group&resnum=4&ct=title#)

have a fun!

---

### Post by dotarts on 2008-10-01
Hi All, 

ipv6 is off now, cache is on, but still browsing is not that fast as in vista :(

Any other proposals ? Or it is Ubuntu feature ? 

Unfortunately Back to Vista.. 

Regards, 
A.

---

