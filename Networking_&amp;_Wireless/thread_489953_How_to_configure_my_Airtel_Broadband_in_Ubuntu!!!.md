---
title: "How to configure my Airtel Broadband in Ubuntu!!!"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by Georgekutty007 on 2007-07-01
[FONT="Book Antiqua"][SIZE="4"][B]Hi All :KS, 

After installing Ubuntu 7.04 in my pc, i am having some issues configuring my Airtel broadband connection (220 BX ADSL2 + Modem). I found some articles on the net; but, still i am not able to configure it successfully....  

I updated the ip address, subnet mask, and Gateway in the network settings. But i dont know how to connect to internet!!! i tried the "sudo pppoeconf" command, but its giving an error...

I have attached a screen shot which contains the error.

Thank You,

Warm Regards,

Georgekutty :) [/B][/SIZE][/FONT]

---

### Post by Games Goblin on 2007-07-11
I'm sorry .. I'm not a Linux Expert... :( Just Started to use the system...

Did you say you have connected it via an ethernet card? It seems Ubuntu has detected it all right :) since there is network icon on the taskbar. I have connected through my USB port...

Can you access the modem in Ubuntu?? i.e. open up FireFox, in the address bar type 

[http://192.168.1.1/main.html](http://192.168.1.1/main.html)    

If asked for Username and Password:

Username :  admin
Password  :  password

________________________________________________________________________________________________

If you can't access the modem like this, your modem is not correctly detected..

Please report back after trying this :)

---

### Post by mytorciar on 2007-11-15
Hi,
This is not a solution but I am adding to the problem defined. I am also a newbie to Ubuntu and because of the safety of linux and such distros against viruses etc, thought to try Ubuntu specifically for internet. 

I have a dual boot with WINXP Pro. Connected thru ethernet, Airtel Beetel 220BNX ADSL2 Modem works beautifully in WINXP and WIN98 ( which I have removed). 

Ubuntu - I started with 6.06 and internet would not work. Tried whaever was written on the Net, but obviously was missing something or something was prohibited. ON WINXP the modem has an ip of 192.168.1.1. It is connected to ethernet and I use a RASPPPOE dialler to connect - therfore my connection is on only when i wnat to use it.

Since, no success, i removed 6.06 and downloaded the latest 7.10. Created the CD and used the live CD to test internet. Worked beautifully with pppoeconf command. I thought i would make the installation final and so installed 7.10 (not upgraded from the old). Now the connection refuses to work. Tried everything again as said on the Net. Just no success.

Now the main fear of going thru the [http://192.168.1.1./main.html](http://192.168.1.1./main.html) routine as has been suggested here and elsewher also. Assuming this works, will it effect the WINXP working as quite possibly some setting may be different for WINXP?   OR - do i go thru this routine in WINXP and note down everything and then try and replicate it on Ubuntu 7.10 ????

There are many many posts from people who have tried various things and succeeded and more than that from people that have failed and given up. Is there any fail proof way to do this or it is better to give up the idea and move to some other linux distro or give up linux altogether if a working and safe internet was the main question?

Would be greatful if anyone could provide a definitive solution.

Thank You
Mytor

---

### Post by dr_gauravsuneja on 2007-12-30
[http://www.honeytechblog.com/configuring-airtel-beetel-220bx-in-ubuntu/](http://www.honeytechblog.com/configuring-airtel-beetel-220bx-in-ubuntu/)

---

