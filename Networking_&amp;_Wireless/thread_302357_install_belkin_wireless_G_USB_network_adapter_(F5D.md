---
title: "install belkin wireless G USB network adapter (F5D7050)"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by tater_3001 on 2006-11-18
Ok, back when i was running windows i had a Belkin Wireless G usb network adapter. The cd only came with drivers for windows and when i switched i had to go back to ethernet.  I was wondering if anybody knew how to install the drivers on Ubuntu.  If you do could you please help me. Thanks, Turner

P.S. the product id is f5d7050.

---

### Post by FrodoB on 2006-11-19
Which version of Fd7050 are you using? 

Here are documents for the two that I am familiar with:

ver 3000: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show)

ver 4000:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Either of these versions works very well. If you have another version let the group know.

---

### Post by Kasper42 on 2006-11-20
Hi,

I found Ubuntu (Dapper and Edgy) works with my F5D7050 out of the box. I just went into System>Administration>Networking and configured it, couldn't be easier!:)

---

### Post by FrodoB on 2006-11-20
Then yours is likely pre version 3000. What is the usb id that you get from:

lsusb

---

### Post by Kasper42 on 2006-11-20
D'oh, sorry I forgot to add mine is pre-v3000 (v1000)

---

### Post by FrodoB on 2006-11-20
It is just good to let folks who read this thread know that it is version 1000 that works out of the box.  Thanks.

---

### Post by daveoily on 2006-11-23
ok, perhaps I'm asking a dumb question, but I need to ask, how do I know whether mine is a 1000, 3000 or 4000 (and presumably there's such a thing as a 2000!)? I've looked everywhere in my documentation and found nothing, my previous research suggests 3000, but I can't remember why...

anyway, thanks for the help, I just hope I can get to grips with these instructions :)

---

### Post by FrodoB on 2006-11-23
The easy way is to get the USB ID from the output of lsusb:

$ lsusb

Then find the Belkin ID and do a search on the web and you should find a lot of hits with Linux folks telling you what chipset it uses.

Another great site with information on device that have kernel drivers is:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

You can look in the Belkin section and often find what you are looking for:

[http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin)

It would be good to know the USB IDs for pre version 3000 devices as I see that USB IDs are not listed on those.

---

### Post by arvevans on 2008-01-30
Very Interesting:

[INDENT] Re: install belkin wireless G USB network adapter (F5D7050)
Which version of Fd7050 are you using?

Here are documents for the two that I am familiar with:

ver 3000: [https://help.ubuntu.com/community/Wi...29?action=show](https://help.ubuntu.com/community/Wi...29?action=show)

ver 4000:
[https://help.ubuntu.com/community/Wi...cs%2FDevice%29](https://help.ubuntu.com/community/Wi...cs%2FDevice%29)

Either of these versions works very well. If you have another version let the group know.[/INDENT]

Read over these methods and then try to imagine your grandmother, mother, or any mere mortal following through this procedure to get their wireless dongle working.  If this is the standard method for getting WiFi to work on a Linux PC, then the "other OS" wins every time.

When will we resolve the Linux WiFi problem?  If it works out-of-the-box, they you are one of the lucky ones.  If it doesn't, you have my sympathy.

The problem is not that the experts cannot get it to work.  The problem is that non-experts cannot get it to work.  We need those non-experts to be happy with their Linux WiFi access in order to make Linux a mainstream OS.  

Arv
_._

---

