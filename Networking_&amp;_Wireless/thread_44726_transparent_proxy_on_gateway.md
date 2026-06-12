---
title: "transparent proxy on gateway"
date: 2005-06-27
forum: Networking &amp; Wireless
---

### Post by garbledwords on 2005-06-27
Hi,

I am having a slight bit of trouble of getting a transparent proxy set up to work right for my internet gateway box.  

My network is two PCs behind the internet gateway box.  One is on interface wlan0 and the other is on eth0.  Both of these are bridged on to interface bridge.  I have a dial-up internet connection which is ppp0.  I am trying to get transparent proxy working for the internet gateway box.  I am running Ubuntu 5.04, with Squid 2.5-STABLE8.  I set up iptables using Firestarter.  It all works fine in non-transparent mode.  

I included the following statement is squid.conf:
	httpd_accel_port 80
	httpd_accel_host virtual
	httpd_accel_with_proxy on
	httpd_accel_uses_host_header on

and the following in iptables:
	iptables -t nat -A PREROUTING -i bridge -p tcp --dport 80 -j REDIRECT --to port 3128

This now works as a transparent proxy for other computers in my network.  

But I can not figure out how to get it to be a transparent proxy for the squid box.  Could someone provide me with the exact iptables statement to do this?

Thanks in advanced.

Roy

---

### Post by Ryan FB on 2005-06-28
I ran into this problem today as well, and I found the solution in [this article](http://software.newsforge.com/article.pl?sid=04/06/23/1521209). Specifically, on my Ubuntu machine I used the rules:
```
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner proxy -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner proxy -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 3128
```
And outgoing requests are now filtered through squid.

---

### Post by garbledwords on 2005-06-29
Thanks, that is just what I needed.  Haven't quite figured out why it works though.

---

### Post by hippyjim on 2005-07-26
[QUOTE=Ryan FB]I ran into this problem today as well, and I found the solution in [this article](http://software.newsforge.com/article.pl?sid=04/06/23/1521209). Specifically, on my Ubuntu machine I used the rules:
```
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner proxy -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner proxy -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 3128
```
And outgoing requests are now filtered through squid.[/QUOTE]

I looked at the article, and got loads of errors whenever I tried any of the iptable commands.

I tried the commands above, and still no joy. It's like I've not done anything

I know dansguardian works because I can change my proxy settings in firefox to 8080 and it filters ok. I need help with this. The problem is I've tried so many different rules and configurations that I've probably dropped stuff in that contradicts itself. How do I wipe it all and start again, and how do I sort this out to "just work"?

I have to get this filtering working, or I'll need to go back to Windoze XP  ](*,)

---

### Post by gruepig on 2005-07-26
To flush iptables rules, use the -F option.  Try 'iptables -t nat -F' to flush the nat table.

Then try your PREROUTING rule again.  Then the same rule only replace 'PREROUTING' with 'OUTPUT' (just guessing with this part).  

Basically, you need two different rules because the first rule is being applying to traffic which is being forwarded through box which is running squid and the second rule gets applied to traffic which is originating from the squid box.

---

### Post by hippyjim on 2005-07-26
Superb! Thanks for the help there, I finally got this working. I just needed to flush the tables first. After I did that, it all worked perfectly. \\:D/

---

