---
title: "Wired Connection Connected But Not Working"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by chazdg24 on 2014-03-11
I had a strange situation yesterday.  Ubuntu 12.04.4 was connected to the internet but was not working.  I logged into Windows 7 and my internet worked fine.  I found a boat load of information for such an event on Google.  Unfortunately nothing worked.  Today Ubuntu works fine.  

Any ideas what could have happened?  I would need to log in to Windows to give specific websites I visited and trouble shooting I did.  Thanks to everyone.

---

### Post by chazdg24 on 2014-03-11
Bump, any ideas?

---

### Post by varunendra on 2014-03-11
When (and IF) it happens again, post back the outputs of -
```
sudo lshw -numeric -C network -sanitize
ifconfig -a
route -n
nm-tool
ping -c4 *<your gateway or router's IP>*
```

It is hard to make a guess, but it could be a DNS or routing issue, or maybe just a DHCP or even physical connection issue. You rebooted, and whatever was stuck got reset - just a guess.

---

### Post by chazdg24 on 2014-03-12
> **varunendra said:**
> When (and IF) it happens again, post back the outputs of -
```
sudo lshw -numeric -C network -sanitize
ifconfig -a
route -n
nm-tool
ping -c4 *<your gateway or router's IP>*
```

It is hard to make a guess, but it could be a DNS or routing issue, or maybe just a DHCP or even physical connection issue. You rebooted, and whatever was stuck got reset - just a guess.
I will do that, thanks!  Still working today.  I never had an issue with any Linux installation like that.

I did have a similar issue with Win 7 and had to reset the TCP stack.

---

