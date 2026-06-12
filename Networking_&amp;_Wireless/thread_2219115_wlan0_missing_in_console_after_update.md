---
title: "wlan0 missing in console after update"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by chimanrao on 2014-04-23
hi
I updated from 12.10 to 13.04.
Something went wrong in the process and I need to run sudo apt-get install from console.
The problem is that the console is not listing the wlan0 interface.
when I run ifconfig, i see eth0 and lo.

how can I fix this?

---

### Post by varunendra on 2014-04-23
What are the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
uname -mr
```
??

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by lz1dsb on 2014-04-23
Amazing... sorry to interrupt, but I just wanted to point out the elegance of [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net 
Thank you Varun, It's always good to learn something neat :)

To me, if wlan0 is no visible in the output, it's very likely you're lacking the appropriate driver for it.[/FONT][/COLOR]

---

### Post by varunendra on 2014-04-24
> **lz1dsb said:**
> Amazing... sorry to interrupt, but I just wanted to point out the elegance of [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net[/FONT][/COLOR] 
Thank you Varun, It's always good to learn something neat :)
Actually, I stole it from Wild Man :p

---

### Post by chimanrao on 2014-04-24
Thanks for your replies. I fixed my upgrades by using a live cd and using chroot to get the upgrade happening correctly.
Hugely disappointed by 13.10, some basic stuff like network manager is not showing up by default, makes it difficult to convince non-techies to use this OS, they expect consistent behaviors after upgrades.

---

