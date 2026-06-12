---
title: "wireless connection not working"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Tench on 2009-12-13
hi I'm new to Ubuntu 9.10, I need some advice on why my wireless internet connection keeps asking for my password, I type in the correct password but it just keeps asking for my password, what am I doing wrong? any help would be appreciated.

---

### Post by NCLI on 2009-12-13
Does it connect after you've entered your password?

If not, are you absolutely certain you've entered the correct password? Try writing it in OpenOffice or Gedit first to make absolutely sure it's correct, then copy-paste it into the password field.

You should also try re-entering the password on your already connected PCs to make sure you remember the password correctly.

---

### Post by leprkhn on 2009-12-13
Recheck the password, making sure it's correct.
If that still doesn't work try turning off your wireless security on your router and attempt to connect.
If that works, try re-enabling the router's security, but at a reduced level (eg WEP instead of WPA or WPA2).

---

### Post by NCLI on 2009-12-13
> **leprkhn said:**
> Recheck the password, making sure it's correct.
If that still doesn't work try turning off your wireless security on your router and attempt to connect.
If that works, try re-enabling the router's security, but at a reduced level (eg WEP instead of WPA or WPA2).

You should only reduce your wireless security to WEP if you live in a thinly-populated area, or are comfortable with letting other people access your network. If not, I'd recommend not using Ubuntu on that computer for now, if it should come down to that choice.

WEP is so easy to get through, you might as well have no security at all.

---

### Post by leprkhn on 2009-12-13
> **NCLI said:**
> You should only reduce your wireless security to WEP if you live in a thinly-populated area, or are comfortable with letting other people access your network. If not, I'd recommend not using Ubuntu on that computer for now, if it should come down to that choice.

WEP is so easy to get through, you might as well have no security at all.

I agree completely. Changing the security settings in this case are just for the purpose of diagnostics. If you can connect with  the degraded security, the we know what the problem is. ;-)
By no means, as NCLI has said, should you LEAVE your wireless security degraded or off (unless your closest neighbor is 200+ meters away).

---

### Post by Scunnered on 2009-12-13
One thing that I found when having similar problem to you was that provided I was not using restart then the wireless would connect after I shut down the system.  Having shut down and then re-booted everything worked OK.

Hope this assist

---

