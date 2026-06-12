---
title: "no http traffic from server"
date: 2018-03-01
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-03-01
I am trying to do a wget/update on my server, and it fails, timing out.  Doing a dig returns the ip fine of a hostname.  The clients can browse websites.  
Here are my rules I have in place:
```
-A INPUT -i lo -j ACCEPT-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.0.0/24 -i eth0 -o eth1 -m conntrack --ctstate NEW -j ACCEPT
-A OUTPUT -m conntrack --ctstate ESTABLISHED -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -o eth1 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
-A OUTPUT -o eth1 -p tcp -m tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT

```
Doing a wget:
```
wget dell.com--2018-03-01 09:48:59--  http://dell.com/
Resolving dell.com (dell.com)... 143.166.147.101, 143.166.135.105
Connecting to dell.com (dell.com)|143.166.147.101|:80...
```
And it just stays there for a long time, then fails out.
eth0 = lan interface

---

### Post by Doug S on 2018-03-02
Your similar question [here]("https://ubuntuforums.org/showthread.php?t=2385783&p=13743334#post13743334"), suggests that your chain policies are DROP rather than the default ACCEPT. Is that the case for this question? If yes, then that is incredibly important information. If no, then I don't know what is wrong.

If your OUTPUT chain policy is DROP, then you are not allowing your server to initiate a TCP session. You need to allow a state of NEW to get out. However, you also don't allow any reply to get back in either.

---

