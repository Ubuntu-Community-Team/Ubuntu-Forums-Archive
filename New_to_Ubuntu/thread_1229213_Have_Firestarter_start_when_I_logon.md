---
title: "Have Firestarter start when I logon"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by zer010 on 2009-08-01
How do I have Firestarter start whenever Ubuntu is logged into, no matter what user logs in?  If there's a better firewall, let me know about that too. Thanks!

---

### Post by wojox on 2009-08-01
ufw - Uncomplicated Firewall is installed by default but not enabled. It's a better firewall. Here's a link to give you some more info and it automatically loads. Firestarter is the gui for ip tables

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by HiImTye on 2009-08-01
firestarter *is loaded* as firestarter is just the easy user interface to iptables. the only reason you would need firestarter open at all times is to view the logs within firestarter. keeping firestarter open at all times, however, can be quite laggy.

ufw is a good solution. just 'sudo ufw enable' and it will be on. you can customize it very easily, for instance, to enable windows-networking. there is also something called 'gufw'.

---

### Post by ad_267 on 2009-08-01
Firestarter doesn't have to be running for you to be protected, iptables is always running and Firestarter just configure iptables. That's my understanding anyways, I haven't used Firestarter.

---

### Post by HiImTye on 2009-08-01
> **ad_267 said:**
> Firestarter doesn't have to be running for you to be protected, iptables is always running and Firestarter just configure iptables. That's my understanding anyways, I haven't used Firestarter.
you are correct

---

### Post by ayenack on 2009-08-01
Firestarter is running at boot if you installed it from the repo's. The only part that is not running is the GUI. It's better to just start the GUI manually and then enter your password.

Decided to delete the howto on how to start the GUI at login it's not secure.

If you want to see the firestarter status type this in terminal

**sudo /etc/init.d/firestarter status**

---

### Post by zer010 on 2009-08-03
Very insightful. Thanks so much for the great feedback!  I, so do love this community!  I've been running Ubuntu exclusivly for a couple months, and I've never looked back, and NEVER will!!!  Thank you everyone!!!

---

