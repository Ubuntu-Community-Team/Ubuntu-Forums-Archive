---
title: "[SOLVED] Can't ... Reach ... Digg.com"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by garfonzo on 2008-04-29
Totally confused. I can only reach some websites. For instance, I haven't been able to reach this forum (until, surprisingly, today). One website I really can't get to is [www.digg.com](www.digg.com). Anyone have any idea why I'm only getting selective website access?


Thanks

---

### Post by chewearn on 2008-04-29
Can you ping those websites?

Check your DNS setting.

---

### Post by superprash2003 on 2008-04-29
you might want to try changing your DNS servers to opendns..read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by garfonzo on 2008-04-29
> **superprash2003 said:**
> you might want to try changing your DNS servers to opendns..read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

I have. I have been using DNS for a few days now and it doesn't seem to make a difference. I can't ping any website, even from my Vista machine which can reach all the websites my Ubuntu box can't. I've got my home router set to use openDNS so every computer benefits from it. 

When, in Ubuntu, I try to go to Digg, I get as far as the title of the Firefox window changing to "Digg/All News, Video, &Images" and the background colour changes to Digg's settings. But that is all. It is then always in a state of "Transferring".

So lame.

---

### Post by chewearn on 2008-04-29
Are you using wired or wireless?  What is your router model?

Try changing from dhcp to static ip.

---

### Post by garfonzo on 2008-04-29
> **AstalaVista said:**
> Are you using wired or wireless?  What is your router model?

Try changing from dhcp to static ip.

Wired, and Static

I had the same thoughts last night. I (think) I disabled wireless and made the IP static. However, no change at all.

arg!

---

### Post by chewearn on 2008-04-30
Ok, another thing to try is reducing the MTU for your network interface:
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122)

I have a similar problem in one of my set-up, where ubuntuforums.org (ironically) took very long time to load.  I figure it has to do with the old Cisco router I'm using.  Reducing the MTU from 1500 to 1498 solved the problem.

---

### Post by garfonzo on 2008-05-04
> **AstalaVista said:**
> Ok, another thing to try is reducing the MTU for your network interface:
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122)

I have a similar problem in one of my set-up, where ubuntuforums.org (ironically) took very long time to load.  I figure it has to do with the old Cisco router I'm using.  Reducing the MTU from 1500 to 1498 solved the problem.

Thanks for the tip. However, that hasn't changed anything. I must say it is really annoying (and vexing) that some websites work, and others do not. Are there any other tricks I might try to get my wired connection working properly?

Thanks so far!

---

### Post by chewearn on 2008-05-04
Have you tried lowering the MTU further?  The value I used ( 1498 ) just happen to be fine for my set-up, but yours might require more.

I recalled during the Windows days, there was a way to use DOS "ping" command to discover the optimal MTU value.  I will dig around on how to use the Linux "ping" for the same.

---

### Post by chewearn on 2008-05-04
Here is a helpful link:
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/411069.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/411069.html)

An explanation:
I'm currently on a Linksys router, which connects to my ISP.  I know that from the router to the ISP, the MTU is 1492.  Subtract that by 28 (ICMP and IP header), we get 1464.  Therefore, ping with packetsize of 1464 will be successful, while ping with packetsize of 1466 will fail.

E.g. ping with 1464, 0% loss:
```
$ ping -c 2 -s 1464 www.google.com
PING www.google.com (64.233.189.104) 1464(1492) bytes of data.
64 bytes from www.l.google.com (64.233.189.104): icmp_seq=1 ttl=243 (truncated)
64 bytes from www.l.google.com (64.233.189.104): icmp_seq=2 ttl=243 (truncated)

--- www.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 58.239/58.443/58.648/0.316 ms

```

E.g. ping with 1466, 100% loss:
```
$ ping -c 2 -s 1466 www.google.com
PING www.google.com (64.233.189.104) 1466(1494) bytes of data.

--- www.google.com ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1009ms

```

Therefore, the optimal MTU is 1492.

.

---

### Post by garfonzo on 2008-05-04
> **AstalaVista said:**
> Have you tried lowering the MTU further?  The value I used ( 1498 ) just happen to be fine for my set-up, but yours might require more.

Interesting. To be honest, I was picking values off the top of my head. I had no idea what MTU was so, perhaps I should be a bit more methodical with this. 

However, the biggest problem I have is that I can't ping the outside world from any computer in my place. I think I'm behind some kind of corporate wall (apt. complex with one massive internet connection that everyone shares). So I think I'm at a loss as to how to figure out my optimal MTU settings. 

When I ping [www.google.com](www.google.com) (from Vista), I get a "request timed out" and nothing happens. I can ping the comps on my home LAN, but not the outside world. Is there a way to bypass whatever it is that is blocking my pings?

---

### Post by chewearn on 2008-05-04
I'm not sure how to proceed.  You might need to check with the IT person at your site.

Alternatively, you could play "guess the number" game. :lol:

To find out if MTU will indeed fix the problem, try adjusting MTU lower by 100 each time:

E.g. if your MTU is now 1500, change it to 1400.
```
sudo ifconfig eth0 mtu 1000
```

As soon as you change, try surf to the site (digg.com); if it's still slow, or can't reach, reduce MTU by another 100.

---

### Post by garfonzo on 2008-05-10
I FIXED IT

Oh man, it's good to have this solved. From what I've gathered, there is a slight glitch in the kernel from version 2.6.20 and on (for some distros?) where users can't access certain websites because of a window scaling issue. Now, I have absolutely no idea what this is talking about, but I discovered this through [this thread]("http://www.mydatabasesupport.com/forums/unix-os-discussions/156427-re-only-some-websites-will-open-ubuntu.html") and subsequently found a bug report with the [resulinting fix]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331") included. 

If you are having the troubles I've been having and the previous methods mentioned in this thread haven't worked, this is what I did following the advice from the above bug report:

(don't forget to make a copy of the original file first!)

```

cd /etc
sudo cp sysctl.conf sysctl.conf.ORG
sudo vi sysctl.conf
--> ADD THIS LINE:
net.ipv4.tcp_window_scaling = 0

```
save the file and reboot. Hopefully, this will have solved your problem!

Thanks so much for all of your help and suggestions! This is what makes Ubuntu a great distro.

Cheers
:)

---

