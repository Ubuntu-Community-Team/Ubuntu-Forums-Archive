---
title: "my wifi card can be detected but not used, HELP!"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by henryjm206 on 2008-11-04
Hi,

i have a laptop that I'm trying to connect to my router with. 
In the GUI on the top panel there is no wireless option. So I ran this command:
```
ifconfig wlan0

```
and it gave me :
```
wlan0: error fetching interface information: Device not found

```

So i checked my wifi card with:
```
 lspci | grep Network
```
and i got:
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61
```
so i don't know what to do from here.
Please Help!

thanks,
henry

---

### Post by CassioBunana on 2008-11-05
Hi  henry, I'm experiencing the very same problem with a different Intel wireless card. I'm not a linux expertise but it seems to me a module problem, i.e. the right module hasn't been loaded...but I can't figure out now out to solve!

Andrea

---

### Post by henryjm206 on 2008-11-07
bump

---

