---
title: "Need help with a Belkin Wireless G Card (F5D7000)"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by ts51 on 2006-08-02
About a month ago I installed Ubuntu on a Windows Me P4 Machine. It had no internet so I bought a Belkin Wireless G Card (F5D7000) to use with my D-Link Wireless G Router. I have read many tutorials but, of the ones I've read, they havn't been much of a help. I am new to linux, so if someone could help me install the card and get internet running that would be great.

-ts51

By the way: I am running Ubuntu 6.06 and I'm pretty sure the card says its version 2000.

---

### Post by Fass on 2006-08-02
If my googling is correct, that card is a Broadcom 4306.

[This thread should be of service to you](http://www.ubuntuforums.org/showthread.php?t=201902), as it basically outlines a procedure similar to the one I used to get a Broadcom 4306 card working.

Now, the supplied Belkin bcmwl5 drivers are shit. So, [try using these ones from linksys instead.](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1123637884333&pagename=Linksys%2FCommon%2FVisitorWrapper) I've had good results with them.

---

### Post by ts51 on 2006-08-02
Thanks for replying so fast =D> . I tried to use that method. It seemed to work but towards the end I ran into some errors. Then when I went into networking under system it didn't show my wireless card at all! Please help!! Did I do something wrong on my part?

Sorry for being such a pain,
ts51

---

### Post by Fass on 2006-08-03
You have to tell us what went wrong if you want us to help you. That something "went wrong" is obvious, otherwise you wouldn't be posting here, but you have to tell us what.

These "errors," for instance, what were they? When in the process did they occur? What did you do to try to resolve them? And so on...

---

### Post by ts51 on 2006-08-03
Well, on my Linux system I am doing a fresh install of Ubuntu 6.06. That way it will erase all the stuff I did trying to configure the card. Ubuntu fully recognized the card before I followed that How-To. So, do I need to install a driver, or did I just have the wrong internet settings??

-ts51

BTW: I had taken a screenshot of the terminal and was going to post it up here to show all the errors but forgot to. It is erased know because (as I said) I am doing a fresh install. ](*,)

---

### Post by ts51 on 2006-08-03
Ok- Here's the deal:

1)My fresh install of Ubuntu detects the card and shows it under networking.

2)I enter in my WEP, the SSID, and I tell it the Key Type is Hexadecimal, and for configuration I select DHCP

3)I hit OK and then activate it. I try to access the internet through Firefox and it says "Server Not Found"

I try to do the same thing but instead of selecting DHCP I click Static IP address and enter in the IP addres, Subnet Mask, and Gateway Address. I hit OK and when I try to activate it I get this message:

"Could Not enable the interface eth1 check that the settings are correct for this network and that the computer is correctly connected to it"

I should not be getting that error. I am 99% sure the settings are correct and that the computer is correctly connected to it.
:-k 

-ts51

---

### Post by Fass on 2006-08-03
If you want to follow that guide, you need to rmmod and blacklist the "bcm43xx" module and then run the ndiswrapper steps.

If you want to use the "bcm43xx" module, you need to use bcm43xx-fwcutter to get the Broadcom firmware in place, as the module doesn't just work on its own. [This is a guide on how to do that.](http://www.ubuntuforums.org/showthread.php?t=185174)

You have to decide whether you want to use the ndiswrapper method or the bcm43xx-fwcutter one. The latter might be easier for you.

---

### Post by ts51 on 2006-08-03
I wan't to use the bcm43xx-fwcutter one but I don't have an internet connection on Ubuntu so this isn't possible (or is it?)
 
If I use the other guide will it do the same thing it did to me last time and not show my card under networking at all?

---

### Post by ts51 on 2006-08-03
Hey I found this page online:
 
[http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working](http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working)
 
It seems like it will work without and internet connection. Can someone please verify this?

---

### Post by itendsnow on 2006-08-03
-Removed Sorry.

---

