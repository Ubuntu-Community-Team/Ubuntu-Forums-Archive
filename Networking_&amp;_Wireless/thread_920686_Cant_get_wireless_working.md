---
title: "Cant get wireless working"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by scphoneguy on 2008-09-15
You'll have to excuse me...I'm not that smart. 

Anyway, I thought it would be intersting to try to learn something new...Obviously, I am a newbie to all of this. Have been working with Windows and this is a big change. 

I have an old IBM Thinkpad T21, with XP and Ubuntu 8.04 installed. I can get to the internet wired but wireless is not so easy. I've tried 'googling' all this but mostly just get confused. Working with 2 laptops to find answers. I've also tried reading all the Sticky's and other threads for answers and again..mostly confusing. Is there a simple step by step instructional out there that can walk me thru getting this figured out? Again, not that smart so be patient if you are willing to help me.

Thanks in advance!

---

### Post by Zorinea on 2008-09-15
By the sound of it. You are having the same problem as me. If when you go to networking, there is no option for wireless, then your wireless card is not compatible with Ubuntu. If you know it, post what your wireless card is and you will have to find a driver for your laptop for wireless to work.

Hope this helps

---

### Post by scphoneguy on 2008-09-15
No, I think the wireless card is compatible, it sees it. I just cant connect to a access point. Its a Linksys WPC54G v1.2. I think it might be a driver issue, I cant seem to get the driver installed.

---

### Post by scphoneguy on 2008-09-17
Now I have another problem. It doesnt see the wireless card at all in Network. If I go to Applications>System Tools>Device Manager, it see it there. But, under Network, all I have is 'Wired Connection' and 'Point to Point connection'. It had the wireless connection listed at first but I think I screwed it up somehow. Can anyone help me? Thank you.

---

### Post by i messed up on 2008-09-17
i am having similar problem hope it works out =P

---

### Post by scphoneguy on 2008-09-17
Figured it out. IF someone else is having this problem...I dont know if I can help..but, here is what I did to resolve the problem: Found the driver for Linksys WPC54G here:

[www.fjall.org/d505/wlan/bcmwl5.inf](www.fjall.org/d505/wlan/bcmwl5.inf)

However, when I attempted to download the file from laptop with Ubuntu, no go. So, I downloaded from my other laptop to thumb drive, then copied the file into folder and went to System>Administration>Windows Wireless Drivers. Choose Install new driver, browse to where the driver is located and done! After the correct driver was installed, it says Hardware Present: YES And now I can get to the internet wirelessly.

Good luck to everyone else!

---

