---
title: "UFW not working as a Kill Switch"
date: 2017-08-02
forum: Networking &amp; Wireless
---

### Post by linux-lion2 on 2017-08-02
I have DD-WRT on my router with my OpenVPN  and a working kill  switch. While rebooting my router I notice it leaked my real ip once.  Never saw it leak again afterwards. Therefore, I want to create a backup  kill switch with UFW in my Ubuntu desktop. I am connected via Ethernet.

The problem that I am having is that I am on a Ethernet connection so  there is no tun0. The commands that I find on the Internet is for tun0  only or local ip starting with 192.168. 

I tried so many commands to get this to work and had no luck. 

Nothing from [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)  works for my needs since my VPN ip address is coming from my router's  OpenVPN config and I am connected via Ethernet my preferred connection.

Allow by Specific IP does work, by port either (1194).

Please Help!

---

### Post by ajgreeny on 2017-08-02
Duplicate of [https://ubuntuforums.org/showthread.php?t=2367517&p=13671421#post13671421](https://ubuntuforums.org/showthread.php?t=2367517&p=13671421#post13671421)
**Please do not create duplicate posts or threads;** it is confusing for all including you and dilutes the forum's ability to help you. 

Closed

---

