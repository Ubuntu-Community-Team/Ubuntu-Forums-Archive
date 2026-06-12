---
title: "WLAN problem on LapTop"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Rim3nX on 2008-05-26
I have a laptop with WLAN card that works fine with XP, but I dont know how to set WLAN as primary connection in Ubuntu that is instalated on the same Laptop via Wubi... help me please... I know that ubuntu is being uploaded only from network, Im new in linux, Im planing to get over Windows and go only with linux... but I cant, since I dont know how to do meny things with any linux:confused:...

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

---

### Post by newbreed on 2008-05-26
post output from terminal:-

```
lspci
```

---

