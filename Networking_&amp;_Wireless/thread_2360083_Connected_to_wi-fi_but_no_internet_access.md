---
title: "Connected to wi-fi but no internet access"
date: 2017-05-01
forum: Networking &amp; Wireless
---

### Post by aalegria2 on 2017-05-01
Hi:

I decided to play around with Linux in an old Asus Netbook. I am a newbie to Linux but wanted to use this netbook to learn.
I downloaded the latest version of lubuntu and burned the image on a DVD.

I ran lubuntu first off the DVD to check that lubuntu ran OK on the netbook and it looked like it did. It found my home wi-fi and connected to the internet without a problem after entering password, meaning Firefox ran OK and I was able to surf the net.

so I felt bold and I decided to install in hardrive and nuked Windows 10. It is an old netbook, so I would not feel bad if later on I messed too bad. I would just re-install lubuntu and try again.

After installation, It connected again to my home wi-fi after after I entered the network password and it shows that is connected. But when I launch Firefox,  Firefox cant connect to the internet.The software installer too cannot connect to the internet. 

I tried using ethernet cable to the router. Again the icon at the corner shows that it is connected to LAN. But firefox or anything else  does not find internet connection.

So I got a challenge right out of the box.

I went to the command line and did a ping of 8.8.8.8 and it pinged OK surprisingly. 

I stopped there as now I do not know what else to do. Anybody has any ideas.

regards.

---

### Post by Autodave on 2017-05-01
When you are wired and click on the connection icon, does your router show in the drop down menu? Is it chosen?

Same for wireless.

---

### Post by wildmanne39 on 2017-05-01
Post 9 at the following link may fix your issue.
[https://ubuntuforums.org/showthread.php?t=2358610](https://ubuntuforums.org/showthread.php?t=2358610)

---

### Post by aalegria2 on 2017-05-01
I did the settings per thumbnail, and then typed the command to restart network manager. I got message that it failed to restart.

"Failed to restart .service.service: Unit .service.service not found."

---

### Post by aalegria2 on 2017-05-01
when connected to ethernet cable the network icon is not x'ed. It says  it is connected to "Wired Connection 1".

---

### Post by wildmanne39 on 2017-05-02
Reboot the computer then and the changes will take effect.
Thanks

---

### Post by aalegria2 on 2017-05-02
> **wildmanne39 said:**
> Reboot the computer then and the changes will take effect.
Thanks

I did a reboot at home, but same deal.

**New info**. I brought the laptop to work where there is a guest LAN and wifi. I tried both and the laptop connected fine to the internet. So I am thinking it has something to do with my router blocking internet access to this laptop rather than a hardware issue.

Networking is a black art that I am not very good at. Any ideas on why I cant connect to the internet at home?

---

### Post by wildmanne39 on 2017-05-02
Please run the wireless script in my signature from the network you can not connect too.
Thanks

---

### Post by aalegria2 on 2017-05-02
Problem solved:

I used the work network to update lubuntu and drivers. one of the drivers was a proprietary driver for the wifi adapter.
When I got home, the laptop connected to my home network without problem.

Thanks for your tips.

---

