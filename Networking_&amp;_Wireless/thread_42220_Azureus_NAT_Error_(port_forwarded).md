---
title: "Azureus NAT Error (port forwarded)"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by ephman on 2005-06-16
hi,

i've setup azureus to listen on port 50060, and i've forwarded the port in my router.  in winxp everythings seems to be fine, but when i try in ubuntu i get an error?  any idea on how i can fix this?  i'm not running any firewalls on the machine, and it should be fine, but it's not.  any help would be appreciated.

thanks,
ephman

---

### Post by Arthemys on 2005-06-16
Does your router support UPnP? If it does, I'd suggest turning it on if it isn't and enabling UPnP usage in Azureus. Makes life easier for me atleast.

---

### Post by ephman on 2005-06-16
thank you for the advice.  yes UPNP is enabled in both the router and in azurues.  

ciao!
ephman

---

### Post by Arthemys on 2005-06-16
The only port issue I've experienced with Azureus is when you close the program and the router still retains the automatic port routing information. Then you try and start it elsewhere on your network, only to get an error from Azureus saying that the port is currently occupied by another computer.

Uhm, try turning UPnP off then on in the router and removing the port routes you've created for Azureus manually, and probably resetting the settings in the program to defaults. Those have worked for me.

---

### Post by ephman on 2005-06-16
thanks again.  however to no avail.  is there something in the iptables i should configure?  i'm not sure how to play around with it, or even if i have to.

thanks
ephman

---

### Post by Arthemys on 2005-06-16
You shouldn't need to play with iptables unless you've previously configured them. If you didn't set up the computer to act as a router, then it shouldn't be configured.

---

### Post by ephman on 2005-06-17
i totally gave up trying to figure this out.  so i reset my dlink 614+ router to factory defaults, and re-opened the ports i needed, and kabang it worked.  there was no difference in the settings.  so i have no real solution or reason why i was having this problem but for the past little bit i've had no issues.  go figure.

thanks,
ephman

---

### Post by rathel on 2005-07-13
I think it might be the router, cuz I have that same router, and I'm getting same problem. I'll try what you did tomorrow.

---

