---
title: "Question about USB wireless"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by ahaslam on 2006-12-10
My dad has been having numerous problems with windows recently & is going to have to reinstall shortly. I've told him a bit about Linux, but he won't be convinced unless he can easily get it working.

I suggested that he try a live cd, firstly to see if his hardware is compatible and secondly to see if he felt comfortable with it. He tried out the mini edition of Sayabon Linux which booted without error & gave hardware acceleration for his ATi graphics. 

The only thing that didn't work was his internet connection. He has an OvisLink EVO-WR54ADSL wireless router with a USB receiver. I have no knowledge of such things as I plug straight into my router. 

My questions are:

1. Are there any live distro's that would have this running out the box (or easily set up)?

2. If he were to be convinced by a live cd, how would I get this to work under Ubuntu Dapper?

Any advice will be appreciated ;)

Tony.

---

### Post by FrodoB on 2006-12-10
Provide the exact manufacturer, model, and version of the USB wireless device.

Boot the computer using a live CD without the device installed.

After logging in insert the device and then open a terminal and run demsg. The last part of the output should show data about the device if it was recognized. Provide the section that shows the device if any.

In the same terminal run lsusb:

lsusb

and publish it back to this forum. That will tell us something about the device.

---

### Post by ahaslam on 2006-12-10
Thanks for your reply. The manufacturer & model is in my first post. I'm about 50 miles away from him so I can't trouble shoot atm. I've seen the Ubuntu Wiki and feel confident that if it is compatable, we'll get it sorted.

**Please ignore my second question, I really just want ot know if there's a live cd that will work for him?**

Tony.

---

### Post by FrodoB on 2006-12-10
We do not need to know what kind of wireless router he has, we need to know the answers about the USB device to answer the question. 

Otherwise, you are depending upon some to have purchased the exact model of router that you describe with the exact model of USB wireless device that you did not describe. 

I could only find three references to that router you describe on Google.

Unless you are saying that he is connecting directly through USB to a router that connects to the modem and wireless is not at all involved.

---

### Post by ahaslam on 2006-12-10
Sorry for the lack of info, it's all I was given. I know nothing about wireless devices and as you've seen google isn't that helpful on this one.

Anyway, he has just rang & is insistent in reinstalling XP. To be honest, he'll probably be better off there. :-# 

Thanks anyway,

Tony.

---

### Post by FrodoB on 2006-12-10
Yes, if he is 50 miles away, it would probably be tough on you.  Without getting the USB ID for a device it is really not possible to say if it can be made to work or not.  Probably so, but it can be a lot of work.

---

