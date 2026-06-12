---
title: "plugging in ethernet kills Wifi - Solved"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by markackerman8@gmail.com on 2016-02-15
Wierd, but as I said when I plug in the ethernet cable, my Wifi gets killed instantly,

and troubleshooting from this page solved it at this point
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source && sudo apt-get install b43-fwcutter firmware-b43-installer

Press Enter. When prompted, type your password. Your password will remain entirely invisible, not even dots will show, this is normal.
Press Enter again.

c. Remove the ethernet cable.
d. Reboot your computer.

Wow weird problem fixed ... I hope it helps others

---

### Post by dave157 on 2016-02-16
I was reading your post but as I am not good at this fixing this issue I did not reply. I figured that the installation installed the wrong driver for your card. 

I am guessing you know what you did but if you do not the command removed 

removed driver below

bcmwl-kernel-source broadcom-sta-common broadcom-sta-source 

and installed 

b43-fwcutter firmware-b43-installer 

I got lucky with my thinkpad t500 Kubuntu installed the driver with the live cd and than I installed. most card do not work that way.

If you want to use Linux in the future here is a link for laptops tested with Linux. Template mean not working or not tested. Not all info is up to date though.

---

