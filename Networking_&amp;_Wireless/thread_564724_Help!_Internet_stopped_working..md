---
title: "Help! Internet stopped working."
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by alex-desktop79 on 2007-10-01
I have been running Gusty for a couple days now, everything working fine. I left the computer on last night and when I came back to it this morning, internet was no longer working!

Here's what I know:
-It works fine on my XP partition (that's how I'm posting this)
-I tried unplugging and replugging everything.
-I tried "sudo dhclient eth0" wich gave me no errors, looked fine (I dont really know what it does)
-Ubuntu tells me I have X packages available to update, and I was able to do "sudo apt-get install lynx", yet when I try to access a web page with firefox or lynx, it simply hangs and loads nothing. Same thing for pidgin.

Please help me, I would greatly appreciate not having to reinstall Ubuntu.

---

### Post by alex-desktop79 on 2007-10-01
bump, if you don't know how to solve the problem, please just give me your two cents, that way i wont feel *completely* ignored

---

### Post by noob12 on 2007-10-01
Here are some suggestions.  Please post the output of these commands for more diagnosis:
```

ifconfig -a

route -n

cat /etc/resolv.conf

# Can you ping an external host?  like one of google's ips.
ping 216.239.59.103

# Can you resolve hostnames?
host www.google.com

# Can you get web pages using wget?
wget www.google.com

# Are you running an (iptables-based) firewall
sudo iptables -nL

```

---

