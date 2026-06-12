---
title: "Cannot open some sites on Firefox whereas I can open them in Chrome"
date: 2017-07-29
forum: Networking &amp; Wireless
---

### Post by yashar2 on 2017-07-29
Hi
I've installed fresh 17.04 with gnome desktop.
After that, I can't open some sites on any browser on my Linux machine except Chrome.
Some of the sites are duckduckgo.com, twitter.com, and sometimes tumblr.com
Browsers I've tried which none of them could open that sites: Firefox, Midori, Opera and Chromium.
I can open them on the same browser and machine and network on windows.
I've tried removing Firefox and all its configuration and then install it again but that didn't work.
I didn't have this problem on 16.04.
Any help?
Thanks

---

### Post by wildmanne39 on 2017-07-29
This does not sound like an internet issue, what happens when you try? any messages? make sure to allow the sites if using noscript, adblocker or ghostery they can prevent sites from loading.

---

### Post by yashar2 on 2017-07-29
I get connection time out error and I'm using fresh installed Firefox with no add-on installed

---

### Post by wildmanne39 on 2017-07-29
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here, if you are using a wifi connection.

---

### Post by yashar2 on 2017-07-29
here it is: [http://paste.ubuntu.com/25198139/](http://paste.ubuntu.com/25198139/)

---

### Post by praseodym on 2017-07-29
```
##### resolv.conf #######################

search test.com
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.0.53
```
Using these DNS on purpose? Lets try

```
sudo mv /etc/resolv.conf /etc/resolv.bak
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by yashar2 on 2017-07-29
No
Actually, as I remember I didn't change the DNS.
I did what you said but that didn't fix the problem, by the way, contents of /var/run/resolvconf/resolv.conf is the same as /etc/resolv.conf so it didn't change anything

---

