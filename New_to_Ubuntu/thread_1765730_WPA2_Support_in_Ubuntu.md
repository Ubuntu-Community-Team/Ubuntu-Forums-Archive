---
title: "WPA2 Support in Ubuntu"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by kalimojo on 2011-05-23
does ubuntu support wpa2 ?

---

### Post by compmodder26 on 2011-05-23
Depends on the wifi card and if proper drivers are available for it.  Assuming proper drivers, yes, Ubuntu has no issues.

---

### Post by beew on 2011-05-23
> **compmodder26 said:**
> Depends on the wifi card and if proper drivers are available for it.  Assuming proper drivers, yes, Ubuntu has no issues.

I am connecting through WPA2 when I am typing this and I am on Ubntu. :)

---

### Post by josephmills on 2011-05-23
hi there if you open yout terminal (ctrl+alt+t )  then enter in ```
nm-tool | grep WPA 
``` you should see something like this 
```
-PC:~$ nm-tool | grep WPA
    WPA Encryption:  yes
    WPA2 Encryption: yes

```     and it should show you the other networks that are using wpa and wpa2 you can also do a ```
iwlist auth 
``` hope that this helps 
Joseph

---

### Post by grahammechanical on 2011-05-23
Ubuntu's Network Manager allows me to set my wireless encryption method to:

WEP 40/128-bit key (Hex or ASCII)
WEP 128-bit Passphrase
LEAP
Dymanic WEP (802.1x)
WPA & WPA2 Personal
WPR & WPA2 Enterprise

Is it missing any encryption methods?

Regards.

---

