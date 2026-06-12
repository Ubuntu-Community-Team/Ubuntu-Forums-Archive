---
title: "DDNS DuckDNS For Static IP Address"
date: 2023-09-20
forum: Networking &amp; Wireless
---

### Post by aaroncatolico1 on 2023-09-20
[SIZE=3]I've built a web server with my pi using the LEMP stack server (Nginx as my main web server), and I already have my own domain at Godaddy. I'm just wondering if I need to add any additional DNS records at GoDaddy to point to the assigned domain provided by DuckDNS after following these simple installation steps:[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3][_**[https://www.duckdns.org/install.jsp](https://www.duckdns.org/install.jsp)**_]("https://www.duckdns.org/install.jsp")[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]If I need to add any DNS records at GoDaddy, what records do I need to add? :?: :idea:[/SIZE]

---

### Post by TheFu on 2023-09-22
The Registrar needs to be told a primary and backup "official" DNS to use for the domain.  Without those public DNS records, nobody will find it.  If you only plan to use the pi internally, then you wasted money with GoDaddy.  

BTW, when your registration ends, you'll learn why people dislike GoDaddy.  Do youself a favor and set a reminder to transfer your domain 6 months before the end date.  I was with GoDaddy on a domain for 20 yrs (10 yr registrations at a time).  They used to be price competitive and for 10 minutes, every 10 yrs, they'd nag me for upsells I didn't need/want.  Last time, their prices were 200% higher than reasonable, so I transferred in a hurry ... for 1 yr.  Then I began looking for the best deal and privacy available.  Some domain registrars charge only what ICANN charges. You can't do any better than that.  After all, the registration record is just an LDAP DB with about 10 fields. How much should running that infrastructure really cost?  IMHO, anything more than $0.50/yr is too much.

As for what any specific registrar needs or doesn't need, that depends on your skills.  In general, it is a bad idea to have registration and dns and hosting at the same places. All three of those need to be at 3 different places to provide network and business redundancy.  If you don't really understand the subtle security of DNS, please don't host it on the internet. You will get cracked.

---

