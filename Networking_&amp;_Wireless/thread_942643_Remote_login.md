---
title: "Remote login"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by santhoshsd on 2008-10-09
I have disabled internet access to a particular user by using te command 
sudo iptables -A OUTPUT -p tcp -m owner --uid-owner santhosh -j DROP

I followed the steps in this link
[http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html](http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html)

but now I am not able to do a remote login to that system as user santhosh, I was able to do a remote a login before doing this ?? 
Any suggestions where in I can disable the internet to the user,
but he should still be able to do a remote login ?

Thank you in advance

---

### Post by superprash2003 on 2008-10-09
is this a remote login to a pc on the internet?

---

### Post by santhoshsd on 2008-10-09
yes, 
I am a system admin.
The user was able to do a remote logon to the system before I disabled internet for him. Now he is not able to do a remote login.

How do I ensure the user will be a able to do a remote login to the system and he shouldn't be able to use internet in that machine.

---

