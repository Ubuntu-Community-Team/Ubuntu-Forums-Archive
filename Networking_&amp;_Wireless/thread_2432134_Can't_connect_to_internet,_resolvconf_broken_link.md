---
title: "Can't connect to internet, resolvconf broken link"
date: 2019-11-27
forum: Networking &amp; Wireless
---

### Post by ceryyxx on 2019-11-27
Hello there, I'm really new to Ubuntu (a week or so) so I'm sorry if I don't understand everything. So I was testing my connection's security with reaver-1.4 and it told me some services could cause problem (including networkmanager) so I check-killed the services and obviously, without network manager, I won't be able to go on the internet. So when I was done, I re-enabled the network-manager service and I could connect to my wireless network, however I couldn't access the internet and I couldn't ping google.com I proceeded to check online if anybody else was having this issue. Turns out I'm not alone. I quickly understood that there was a problem with resolvconf. When I go to /etc/resolv.conf. It shows that resolvconf is a broken link. Anybody got an idea how I can fix this ? Also, I speak french, so maybe I did a couple of errors, sorry about that.

---

### Post by howefield on 2019-11-27
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by Skaperen on 2019-11-27
when i made my [COLOR=#006400][FONT=courier new]**/etc/resolv.conf**[/FONT][/COLOR] be a symlink, many things did not work.  when i made it be a regular file, something replaced my file.  that replacement was not what i wanted but maybe it will work for you.  so what i suggest is to rename that symlink (to save it, just in case you need to restore it) then reboot, and see if it puts a good file there.

for me, i wanted to use different servers.  so i put a file there and did [COLOR=#0000cd][FONT=courier new]**sudo chattr**[/FONT][/COLOR] on it to give it the immutable attribute.  so far that works for me.

---

### Post by chili555 on 2019-11-27
> **ceryyxx said:**
> Hello there, I'm really new to Ubuntu (a week or so) so I'm sorry if I don't understand everything. So I was testing my connection's security with reaver-1.4 and it told me some services could cause problem (including networkmanager) so I check-killed the services and obviously, without network manager, I won't be able to go on the internet. So when I was done, I re-enabled the network-manager service and I could connect to my wireless network, however I couldn't access the internet and I couldn't ping google.com I proceeded to check online if anybody else was having this issue. Turns out I'm not alone. I quickly understood that there was a problem with resolvconf. When I go to /etc/resolv.conf. It shows that resolvconf is a broken link. Anybody got an idea how I can fix this ? Also, I speak french, so maybe I did a couple of errors, sorry about that.May we see:

```
lsb_release -d
ls -al /etc/resolv.conf

```

---

