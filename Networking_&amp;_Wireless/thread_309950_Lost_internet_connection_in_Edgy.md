---
title: "Lost internet connection in Edgy"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by oolunchbox on 2006-11-30
Started last night. Got home, tried to check my email, nothing. DSL modem looks good, router is fine, girlfriend's computer works fine (though shes running dapper).  I haven't knowingly changed anything (I am a *relative* n00b, I will admit) I performed an update yesterday, I believe, but I'm pretty sure it was only Wine and Automatix.  I can't get into my router from my computer, I can't ping anything, I show an IP address using DHCP and my router shows that I'm connected, I've tried switching cables, tried using another port (I've got Dual Gigabit Ethernet on my motherboard).  It's mysteriously just stopped working.

Help!
](*,)

Edit:
Ok now I'm even more confused.  I've run ```
ifdown -a
``` and ```
ifup -a
``` and I was able to get an IP from my router without a problem, in fact all three of my ethernet ports could get an IP without any issue.  I had Guarddog installed but never use dit, I uninstalled it in case my girlfriend had been using my computer and accidentally enabled it and managed to block all traffic (I know I'm going out on a limb here...). I've still got nothing, I even tried connecting my DSL modem directly to my computer and nothing, IP fine but zero internet connection.

[SIZE="2"]Anyone?[/SIZE]

---

### Post by oolunchbox on 2006-12-01
Anyone? I've narrowed it down to having to be a software problem as I've installed a new network adapter that I know works and still i get no connection. I can get an IP but no connection to the internet.  I just can't seem to figure out what's going on.

---

### Post by oolunchbox on 2006-12-02
Ok, I've tried everything under the sun I can think of. I've tried the live CDs (dapper & edgy) I tried resetting my CMOS. I've done it all. Nohting works. Like I stated- I can get an IP from my router but cannot ping anything (using an IP or URL) or connect in any way to the internet. Any ideas?

---

### Post by oolunchbox on 2006-12-04
when I try to ping [www.google.com](www.google.com) I get ```
ping: unknown host www.google.com
```
when i release and renew my IP address I get one just fine. whats the deal? still no connection. HELP please.

---

