---
title: "Wireless Network Help!"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by misanthropica on 2010-02-04
My friend gave me an old Presario 2100 laptop with Ubuntu 9.10 already loaded. My wife was using the computer to search the internet and she let the battery completely die. When I plugged it in and tried to start it back up, it kept freezing up, so I re-installed Ubuntu and now it's working again; however, now I can't connect to my wireless network. I'm completely new to Ubuntu, and my router is obviously working because I'm typing this on my other laptop. The help page isn't much help, either. What do I do?

---

### Post by brawd on 2010-02-04
Start by clicking on the network applet at the top right of the screen. A left click will show if you have detected your wireless network.
If it has then click on it to enable it. Then (I think) right click on the applet to put in your WEP number.

That's the simple stuff. See how you go.

regards,

brawd

---

### Post by switch10 on 2010-02-04
plug the laptop into your router via an Ethernet cable.  go to system>administration>hardware drivers in Ubuntu.  See if that finds your wireless drivers.  

Did the laptop have Ubuntu previously installed on it?

---

### Post by misanthropica on 2010-02-04
Thanks for responding. "No proprietary drivers in use on this system," was the message I received when I checked for drivers, so I'm assuming my friend loaded one before...? Where would I find a the driver I need and how do I check the card type?

Stumped,

Newbie

---

### Post by bkratz on 2010-02-04
> **misanthropica said:**
> Thanks for responding. "No proprietary drivers in use on this system," was the message I received when I checked for drivers, so I'm assuming my friend loaded one before...? Where would I find a the driver I need and how do I check the card type?

Stumped,

Newbie

go to the terminal (Applications>>Accessories>>Terminal) and type in 
lspci  (that is LSPCI in lowercase). Copy/Paste the output back here for decoding or look at it yourself.  this will tell what the wireless card is.

---

### Post by warfacegod on 2010-02-04
Wouldn't enabling Restricted Extras, in Software Sources, be required here?

---

### Post by misanthropica on 2010-02-04
> **bkratz said:**
> go to the terminal (Applications>>Accessories>>Terminal) and type in 
lspci  (that is LSPCI in lowercase). Copy/Paste the output back here for decoding or look at it yourself.  this will tell what the wireless card is.


Cool: Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Now I just need to go to the driver store, right? :)

---

### Post by bkratz on 2010-02-05
> **misanthropica said:**
> Cool: Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Now I just need to go to the driver store, right? :)




See the second half of this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
Yours is specifically mentioned as b43-legacy

---

### Post by misanthropica on 2010-02-05
I'm typing this thank you message on my laptop and sending it over my wireless network. Thanks for all your help.

Sincerely,

Newbie

---

### Post by bkratz on 2010-02-05
> **misanthropica said:**
> I'm typing this thank you message on my laptop and sending it over my wireless network. Thanks for all your help.

Sincerely,

Newbie

Congratulations!  Now all that is left is to go to the thread tools and mark the thread [solved] and enjoy your wireless!

---

