---
title: "Can't print to USR5461 / HL5140 printer from Edgy"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by Billquinn1 on 2007-01-10
I purchased a US robotics USR5461 router w/ print server. It said I would have to upgrade the firmware to print from linux. I did that but still can't print. It just puts some unknown file in the queue that I have to reset the router to delete. The printer is a Brother HL-5140 that prints fine when connected to the computer. All the windows boxes in the house print fine to it. If anyone has any thoughts about this I would appreciate any thing.


Thanks
Bill

---

### Post by kenns on 2007-01-28
Same problem here.
I have an HP Deskjet710C.

In Ubuntu 5.10 it worked.

---

### Post by rcarpint on 2008-06-28
Good news: USRobotics released a beta firmware to fix this issue.

From the product's support page:
[http://www.usr.com/support/product-template.asp?prod=5461](http://www.usr.com/support/product-template.asp?prod=5461)
download the BETA Firmware Version 3.93.35.0.9

or directly at
[http://www.usr.com/support/5461a/5461a-files/USR5461a-v4.3.93.35.09.usr](http://www.usr.com/support/5461a/5461a-files/USR5461a-v4.3.93.35.09.usr)

Then, upgrade your router firmware with the file you downloaded.
(at [http://192.168.2.1/device.asp](http://192.168.2.1/device.asp) )

It just worked for me in Ubuntu 8.04, no compilation or any additional package needed. :-)

---

### Post by Billquinn1 on 2008-06-30
This is great news. I have just updated my router and will work on the printer drivers later. If this works I will take back all the horrible things I've said about USR in the last year.
I'll report back if this works.

WOOOOOOHOOOOOO! Works like a champ.
Working for 8.04 and Fedora 9.

---

