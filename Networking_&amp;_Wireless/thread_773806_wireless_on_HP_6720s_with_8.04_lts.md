---
title: "wireless on HP 6720s with 8.04 lts"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by k00ra on 2008-04-29
greets

I am using a HP 6720s, and I can't seem to get the wireless card working with ubuntu.

First I installed 7.10, the wireless card appeared but no wireless networks appeared. After applying the following [http://sudan.ubuntuforums.com/showthread.php?t=659027](http://sudan.ubuntuforums.com/showthread.php?t=659027) the ethernet card dissapeared from 'networks' and there were still no wireless networks appearing. (This was 10meters from the AP)

A few days ago I installed 8.0, the problems were the same (wireless card appears and no networks appear).
15h ago I got to a wired internet connection, used the automatic update option, and after it updated everything, the wireless card disappeared from 'networks'.

What can I do :confused: I am not really experienced with these sort of things... Thank you! :KS

---

### Post by matic13 on 2008-04-30
hi. first do that from sudan forums and then try typing that in console

```
sudo apt-get install b43-fwcutter
```


```
sudo wget http://download38.mediafire.com/2bdi9e0d0l7g/jyjze9dd7t9/network-manager_0.6.6-0ubuntu1_i386.deb
```

```
sudo dpkg -i network-manager_0.6.6-0ubuntu1_i386.deb
```

reboot 

and i think that will works :)

---

