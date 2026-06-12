---
title: "ndiswrapper website problems"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by gisler_csn on 2008-11-30
hi,

i have just installead and started using linux for the first time. 

i now am trying to set up my wireless. i have managed to install ndiswrapper just fine. the only problem is when i go to ndiswrapper's website it just gives me errors. if i understand everything correctly i need to get drivers from them for my wireless card? if there is another website or i am missing something please try to explain. 

also i have a broadcom wireless card, this is built into my laptop.

many thanks

gisler_csn

---

### Post by Ayuthia on 2008-11-30
If you have a working internet connection and using 8.10, you can activate your Broadcom card through System->Administration->Hardware Drivers and select the Broadcom Driver.  If you have the Broadcom STA option (instead of the Broadcom b43 option), you don't need to have an internet connection to make it work.

However, if you want to use NDISwrapper, you will need to have the Windows (XP or older) version of the wireless driver.  It will be labeled as bcmwl5.inf and you will also need the bcmwl5.sys or bcmwl564.sys file.

Hope that helps.

---

