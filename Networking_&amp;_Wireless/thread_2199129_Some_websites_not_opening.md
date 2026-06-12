---
title: "Some websites not opening"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by itsankur on 2014-01-12
Hi
Some websites are not opening in laptop (ubuntu 12.10, firefox).
I have seen similar threads, but unfortunately couldn't figure out the solution.

I have seen a similar thread by **liquidstone** where he found the solution, but could not
understand how. My problem matches with him.

Examples of sites that are not opening:

mail.yahoo.com
ausopen.com (showing ***waiting for cdn.adinfinity.com.au***)
bleacherreport.com (showing ***waiting for cdn.optimizely.com***)

---

### Post by itsankur on 2014-07-06
Hi
This thread was not replied by anybody for long time. But I guess this is a real problem faced by many users. Although I think it may not be a problem of ubuntu or any specific OS becoz I can not open the same websites in windows either! When I connect this ubuntu machine to my university network, everything works fine. I can access all the websites. I have tried

1. Deleting all cookies
2. Adding the line *net.ipv4.tcp_window_scaling = 0 *to the file [B]/etc/sysctl.conf
[/B]3. Adding the lines 
*                          net.ipv4.tcp_wmem = 4096 16384 131072*
                          *net.ipv4.tcp_rmem = 4096 87380 174760*
                                                                            to the file [B]/etc/sysctl.conf4
WITH NO EFFECTS. 

I can not even access to some the journal websites to see the abstracts of the papers.
I AM IN A SERIOUS PROBLEM. PLEASE HELP.
[/B]

---

### Post by jeremy31 on 2014-07-06
Have you added the google DNS to your connection

[h=3]Google Public DNS IP addresses[/h][FONT=Open Sans]The Google Public DNS IP addresses (IPv4) are as follows:[/FONT]

[LIST]
[*]8.8.8.8
[*]8.8.4.4
[/LIST]
[FONT=Open Sans]
[/FONT]

---

