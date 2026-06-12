---
title: "Network connection no longer works"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by to25 on 2010-11-29
I know this topic has been posted many times but my issue varies.

Initially my wireless connection was working fine. However, last week it just stopped connecting out of know where. Other Laptops using Win7 have had no issue what so ever. The laptop is dual-booted with WinXP and it was affected as well. On the XP I had to go back to a restore point for the wireless network to work. I also reinstalled Jaunty but to no avail. I have checked the router's page and it detects my laptop with no restrictions. I am noticing that every time I enter my key, I would check on it again ad would change to this long sequence of numbers which are the same each time. I am at my wit's end and hopefully someone can help. I am at the point where I am just going to format everything and start from scratch. 

I am using a 7405GX Gateway Laptop
With Broadcom chip running on B43-fwcutter


Let me know what info you guys need. 

Thanks.

---

### Post by psycho5 on 2010-11-30
> **to25 said:**
> I know this topic has been posted many times but my issue varies.

Initially my wireless connection was working fine. However, last week it just stopped connecting out of know where. Other Laptops using Win7 have had no issue what so ever. The laptop is dual-booted with WinXP and it was affected as well. On the XP I had to go back to a restore point for the wireless network to work. I also reinstalled Jaunty but to no avail. I have checked the router's page and it detects my laptop with no restrictions. I am noticing that every time I enter my key, I would check on it again ad would change to this long sequence of numbers which are the same each time. I am at my wit's end and hopefully someone can help. I am at the point where I am just going to format everything and start from scratch. 

I am using a 7405GX Gateway Laptop
With Broadcom chip running on B43-fwcutter


Let me know what info you guys need. 

Thanks.

Your key is changed to a series of numbers because of security. So you don't have to worry about that. Try plugging in your laptop with an ethernet cable, then run Ubuntu updates, after updates, then enable  your restricted driver for your wifi. See if it works. Make sure your internet settings are DHCP or static. If they are static you need to enter your Ip address, gateway, and subnet mask, along with primary and secondary DNS.

If your network card is also not working on XP, then it could be a hardware problem and nothing to do with the OS.

---

