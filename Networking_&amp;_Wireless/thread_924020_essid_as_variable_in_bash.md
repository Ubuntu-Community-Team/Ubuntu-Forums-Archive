---
title: "essid as variable in bash"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by gregology on 2008-09-19
Hello,
      I want to run essid specific mounts. So when I connect to essid "home" it will preform certain mounts and when I connect to essid "work" it will preform others. My plan is to put a bash script in /etc/network/if-up.d with an if statement but I don't know how to make the essid a variable for the if statement. Can anyone help?

Thanks.

---

### Post by gregology on 2008-09-19
wifi=$(/sbin/iwconfig wlan0 | grep ESSID | cut -d '"' -f 2)

figured it out :)

---

