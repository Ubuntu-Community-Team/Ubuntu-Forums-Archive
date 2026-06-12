---
title: "Dell 1525 Wireless does not appear with lspci"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Allen25 on 2008-06-03
Hi,

I recently got a Dell Inspiron 1525 with a "Dell Wireless 1395 WLAN Mini-Card - BCM4315". I am unable to get Ubuntu Hardy 8.04 to see it at all (nothing appears for it with lspci - though my wired connection does appear and work).

I verified that the wireless card works properly by getting it to work in Vista (this is a dual booted machine where Vista was installed first and I have installed Ubuntu after it).

Is this some type of crazy hardware issue or can someone tell me what I have to do to get the wireless card to even appear with lspci?

Thanks!
Allen

---

### Post by Allen25 on 2008-06-03
Soooo, the first thing I learned was NOT to post a question on a public forum when it is 2:30am and you are not thinking straight. 

To keep anyone from making my mistake, here is how you correct the "problem" I posted:

sudo apt-get remove b43-fwcutter
sudo apt-get install b43-fwcutter
reboot

Get Windows XP drivers - here is what I got: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=RU&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=RU&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819)

Extract the files with unzip (even though it is an exe, it is just a self extracting zip file).

System -> Administration -> Windows Wireless Drivers
Install Driver - I selected bcmwl5.inf in the DRIVER_US folder
 
Then just configure your wireless connection with whatever encryption key you need.

Hope that helps,
Allen

---

