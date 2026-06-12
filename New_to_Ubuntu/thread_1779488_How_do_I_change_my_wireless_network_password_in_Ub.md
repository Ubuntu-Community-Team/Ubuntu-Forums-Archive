---
title: "How do I change my wireless network password in Ubuntu ?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by haggardtechno on 2011-06-10
Hey guys, I was wondering if anyone could tell me how i can go about changing my router password. I switched ISP's today, and the default password the technician set is like 25 characters long :???:, i wanted to change it to a more simple password. Thanks.

---

### Post by papibe on 2011-06-10
That has to be done on the router itself. Google your router brand and model, to see how to access it. Usually it is done by connecting the browser to a LAN IP. Typical address are:
```
http://192.168.1.1
or
http://192.168.1.254
```
Hope it helps.

---

### Post by wep940 on 2011-06-10
Do you mean the password for maintenance and configuration tasks on the router, or do you mean the key that was assigned for encryption, which you would use when trying to connect to the net via wireless?

If it's the router configuration password, do as [papibe]("http://ubuntuforums.org/member.php?u=774785") suggested.

If it's the password/key you need to use to connect your PC wirelessly, you may not want to change it.  A longer key is supposedly harder to crack.  Also be sure you match the encryption type - WEP/WPA/WPA2.  If it is only set to WEP, I would strongly suggest changing it via the router configuration to WPA or WPA2.  WEP is very weak and can be cracked easily.  Also, you normally only have to enter this key once for ubuntu or windows, so it's not like you need to memorize it or anything like that.

---

### Post by papibe on 2011-06-10
Both, actually.

You'll need the admin password first to make changes (they are very standard and you can google the defaults). Then once you have access to the router, you can change the wireless key.

I recommend using WPA or WPA2, because WEP it is very easy to break. Also use a key made of numbers and letters, at least 12 characters long. Finally change the user/password for administer the router for even more security.

Hope it helps.

---

### Post by haggardtechno on 2011-06-10
yepyep, all done. Thanks so much for the help guys. Peace. :p

---

