---
title: "Live CD install issue 11.04 Natty"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by todrab on 2011-05-14
I am trying to test and install Natty 11.04 from the live CD I downloaded today.  The set up is an HP DV6000 with a 16:9.  The iso is fine, I installed Natty on an ancient dell without any issues.  On the HP, the live cd only loads really low resolution for the 16:9 screen, which means I cannot see the load menu.  Is there someway to adjust this?

Thanks in advance for any help.

---

### Post by JRV on 2011-05-14
I would try to install with the alternate CD.

---

### Post by garvinrick4 on 2011-05-14
> I installed Natty on an ancient dell without any issues.  On the HP, the  live cd only loads really low resolution for the 16:9 screen, which  means I cannot see the load menu.  Is there someway to adjust this?
Hello, In the Live Cd run this and post: Will give you all the cards and drivers so users can
spot what you should do.  Most likely a setting you can change at boot. 
```
lspci -k
```

---

### Post by garvinrick4 on 2011-05-14
> **todrab said:**
> I am trying to test and install Natty 11.04 from the live CD I downloaded today.  The set up is an HP DV6000 with a 16:9.  The iso is fine, I installed Natty on an ancient dell without any issues.  On the HP, the live cd only loads really low resolution for the 16:9 screen, which means I cannot see the load menu.  Is there someway to adjust this?

Thanks in advance for any help. If you cannot see anything to boot the live Cd
hit any key when ubuntu cd starts then hit F6 and see if you can boot with nomodeset
option.

---

