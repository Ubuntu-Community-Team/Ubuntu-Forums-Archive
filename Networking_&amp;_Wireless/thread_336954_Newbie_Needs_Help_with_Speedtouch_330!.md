---
title: "Newbie Needs Help with Speedtouch 330!"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by willbur on 2007-01-12
Hi all

I'm new to Linux and Ubuntu (installed Edgy 2 days ago!) and am having real problems getting my crappy Speedtouch 330 modem to work. There are lots of threads in this forum relating to this problem, including the official Ubuntu help pages referring to a Dapper install, which may (or may not) work with edgy (different kernels?). I've seen lots of subtly different scripts and tried them all between reinstalls of the OS, but no joy. Could anyone please help me with this, as I've been trying for 2 days solid and am running out of ideas?

My hardware:
IBM T40 laptop, with nothing on the HDD except for a fresh Edgy installation
Thomson Speedtouch 330 modem, revision 4 (black)
My ISP - Tiscali

I have the firmware ZZZL_3.012, have the splitter program which works fine for me, get no error messages when going through any of the instructions posted on the forum, reboot and - nothing ](*,)  Help!

as an aside, is there a difference between the symbols ' and " when used in the secrets file? What about ( and [ for the bootscript? Many thanks....

---

### Post by Richard Kut on 2007-01-12
Hi Willbur, and welcome. You don't mention if you are using a router between your laptop and the modem, so I will assume that you are not using a router. 

So, at the risk of asking the obvious, have you tried running the pppoeconf command? If not, then give that a try, and then please update this post with what happened. Good luck!

---

### Post by willbur on 2007-01-12
Hi Richard

Thanks for the reply, and for the welcome. No, no router, I just plug the modem into the phone socket on the wall and plug the other end into a USB port. Pppoeconf? What's that? If you assume I'm a complete novice (2 whole days experience!) you won't go far wrong ;) 

Regards

Willbur

---

### Post by amar on 2007-01-12
I remember having similar headaches with this modem as a newbie (actually i still am a newbie just not as much a newbie)

I followed the instructions on this web page, 
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

VPI/VCI numbers for your country/ISP. -  0 / 38
and follow the instructions for PPP Over ATM

It was a pain the first time, second time was essayer (i had to completely reinstall at one stage) then when installing on my laptop I wondered what I was fussing about before. Just stick at it

good luck

---

### Post by willbur on 2007-01-12
Thanks, Amar.

Can you confirm that these instructions will work with edgy? I've read elsewhere that edgy's kernel is different to previous versions and that warty or dapper info won't work?

Regards...

---

### Post by amar on 2007-01-12
The first time I did it with dapper, second and third times with edgy, I can't remember there being any differences.

---

### Post by willbur on 2007-01-13
Thanks again, amar - I'll try it again and let you know how i got on ;)

---

### Post by willbur on 2007-01-13
Bizarre. After following all the instructions to the letter and rebooting, I get a ppp0 option in the connection properties dialog, but no connection. After another reboot - I'm in! :D  Many thanks amar - I owe you one!

willbur

---

