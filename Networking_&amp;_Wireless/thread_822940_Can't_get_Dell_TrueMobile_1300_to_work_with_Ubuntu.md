---
title: "Can't get Dell TrueMobile 1300 to work with Ubuntu!"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by AlexLinuxUser101 on 2008-06-08
So I downloaded ndisgtk and tried every driver that is supposed to be associated with the TrueMobile 1300 (I tried many) but it still doesn't work!  Is it the fault of ndisgtk or something else?  Help please.  Thanks a lot.

~ Alex

---

### Post by Ayuthia on 2008-06-08
> **AlexLinuxUser101 said:**
> So I downloaded ndisgtk and tried every driver that is supposed to be associated with the TrueMobile 1300 (I tried many) but it still doesn't work!  Is it the fault of ndisgtk or something else?  Help please.  Thanks a lot.

~ Alex
Does ndisgtk show that the hardware is present?  If it doesn't, then it does not like the driver.  I am not familiar with the program because I generally use the Terminal to configure NDISwrapper.  You could go into the Terminal and type:
```
ndiswrapper -l
```If it shows that the hardware is present, then the driver is ok.  

If you want, you can post the results of the following:
```
lspci -nn
ndiswrapper -l
```
This will help us see what wireless card you have and see if you have the right driver.

---

