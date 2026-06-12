---
title: "No Wireless?"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by wsetchell on 2008-05-22
So tonight I just switched my laptop from vista to Ubuntu.  The wireless was working fine previously.  Now with Ubuntu no wireless connections are found.  Normally I can access my own network and see several of my neighbor's networks also.  

Ideas for fixing this?

Muchas Gracias

---

### Post by Enthralled on 2008-05-23
Does Ubuntu detect your WiFi card at all? Which card do you have? Did you install the card's drivers (if needed)?

Tip: You have to give us some more info before posting a thread.

---

### Post by mapes12 on 2008-05-23
Please could you post the output to these please. Please use the quote tool (4th button in from the right in the message toolbar) to help folk with bad eyesight like me:

```
sudo lshw -C network

ifconfig

iwconfig

cat /etc/resolv.conf
```

---

### Post by iopo on 2008-05-23
Did it work using the live-cd? Did you use the normal cd or the alternate cd to install Ubuntu?

---

