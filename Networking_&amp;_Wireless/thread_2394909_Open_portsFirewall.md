---
title: "Open ports/Firewall"
date: 2018-06-23
forum: Networking &amp; Wireless
---

### Post by linux-user-0987 on 2018-06-23
I am trying to test the security of my Operating system and to check for open ports I have used several websites and nmap. For all the websites I am getting the same result: port 22 and port 443 are open. From nmap I am getting port 443 and 80 as open,(others being blocked because of firewall) and if I block 80 it does not show up.
I am using a public wifi and I needed to access the website from the providers log in page. 

Settings:
Deny incoming,outgoing. routed disabled.
allow out 25,53,80,110,443/tcp , 53,67,68/udp, 51413, 6969/tcp 

1)I want to know why port 22 shows up as open on the online port checking websites. Even with the settings set to deny outgoing and deny in port 22 it tells me that it is open. Is it because port 22(SSH) has some connection with another open port or does it have something to do with the public wifi I am using?

I used the online port checker and nmap before using another public wifi which did not require me to visit a log in page and for the online test the result was Timed out/stealth.

2) If an ISP, (provider of public wifi) decides to hack into a users system, does he have any advantage over someone who knows the just the ip address?

3) Can a system with no open ports or unresponsive ports be hacked?

4) If a hacker knows the ip address and finds open ports, how does he attempt to hack a system? If he is on the same network does it become easier for him hack?

5) Is there a difference between ports? Do hackers prefer some open ports more than others? What about tcp/udp? 

6) Is it possible to get a live notification from ubuntu about a hacking attempt? What about the logs?

7) What does routed mean is ufw status?

---

