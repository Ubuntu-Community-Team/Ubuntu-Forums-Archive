---
title: "PPP vs Konqueror/Kmail - can not connect"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by nxt on 2007-12-05
I have small internet connection problem.

When I connect using LAN or WIFI everything works nice and smooth. But when I use **PPP connection to connect with GPRS and now CDMA**, I get connected, Firefox, Skype, Kopete work perfectly, but **Konqueror and Kmail cannot connect** anywhere... :(

:confused: Please help!

---

### Post by nxt on 2007-12-05
*I switched off cache in Konqueror* - and YAY! Konqueror is on the net. But I still got** no luck with Kmail** :confused:

---

### Post by nxt on 2007-12-12
OK...so I got KMail working as well with PPP.

The trick is in the restarting of the network daemon.

KControl > KDE Components > Service Manager

in Startup services just find: Network Status Daemon, select it and click on STOP and START buttons respectively.


....I still don't know how to restart the network daemon automatically on PPP connect....but hey....I am getting there ;-)

---

### Post by gatman3 on 2007-12-12
Just wanted to say thanks - coincidentally, I have encountered the same problem this week.  I am using dial-up-networking with my Nokia cellphone to get a ppp connection, and Firefox and vpnc work great... but kmail doesn't seem to want to even try to download mail.  Oddly, I can send mail using kmail, just not receive it.

I will try your solution.  Thanks a bunch for posting it.

Does it seem like a bug should be opened for this problem?

---

### Post by gatman3 on 2007-12-14
Yep, worked great.  I started and stopped the network status daemon and magically kmail saw the new ppp connection.  Thanks again, nxt!

---

