---
title: "Realtek RTL 8187 Problems"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Piro24 on 2008-05-26
Hello, I'm having a bit of trouble with my wireless card.

When Ubuntu boots up, it automatically tries to connect to the wireless network, sometimes this succeeds, and sometimes not, fairly at random. When it does succeed, it seems to be fine, but several minutes later, it simply stops working. The network interface icon gets stuck, and will usually say something like "90%" but no internet connection, or any network activity is going on.

Reconnecting also does not work, the only way to get it back is to turn off networking, then enable it, and hope that Ubuntu connects. There supposedly is a Rtl8187 driver installed when I click on 'about" button. I'm not sure what to do now.

When I installed Ubuntu, it worked great at first, and the internet had no problems, but then I saw the update manager, and there were some 102 updates, so I downloaded and installed them all. Since then, I have been having this problem. 

Help would be highly appreciated.

Edit:

Hmm, after a bit more searching, I found this

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)

It seems my card fits the 8187B description, and my laptop is indeed a Gateway (though I am not sure if it is the same model, it is a safe bet) by looking there, it seems that the only way to get it too work is Ndiswrapper, is this true? Has anybody had sucess with this, any further information would be appreciated. I've had plenty of trouble with Ndiswrapper in Puppy Linux before, so if there is any other way to get it to work, I would do that.

---

### Post by mapes12 on 2008-05-26
There's a section in this HOWTO that deals with rtl8187 driver issues:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Piro24 on 2008-05-26
> **mapes12 said:**
> There's a section in this HOWTO that deals with rtl8187 driver issues:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I tried just about every way that I could think of using this guide, and every time, it doesn't work. 

However, ```
sudo modprobe r818x 
sudo modprobe r8187
```
 just gives me a "Fatal" Module not installed error. Like I said before, I'm using Ubuntu 8.04. I'll look for those modules one last time and try again before I try Ndiswrapper as a last resort.

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

---

### Post by Piro24 on 2008-05-27
I have a card like that, it uses the RT2500 chipset, and it does work fairly well, but it would still be nice to get the internal one working. 

And, that is why I wanted to try everything else before having to use ndiswrapper, I too have had problems with it, and it seems to be avoided like the plauge.

---

### Post by Psyphre on 2008-06-05
ur alternative is to use gutsy not hardy. Mine works perfect and im sticking with gutsy until a proper solution is found in hardy.

---

### Post by scholzilla on 2008-06-12
Are you sure you have the 8187b and not 8187l chipset? I had this problem forever with my gateway laptop and had assumed I was using 8187b since everyone else was, gateway customer 'service' couldn't tell me and realtek customer service does not exist in any useful way. Here's the only way I think you can check: get a screwdriver and unscrew the panel where your wireless card sits. It will say b or l on the card itself. If you have L, download the driver for L from the realtek download site. It will only work on 32-bit systems, which means if you're running 64-bit, you'll need to reinstall 32-bit. It works well for me now. The How-To won't help you if you have the 8187L chipset.

---

### Post by Turkey Pwner on 2008-06-12
Try installing ndisgtk whenever your Internet comes back up. :)

---

### Post by zurichsl on 2011-08-17
> **Piro24 said:**
> I tried just about every way that I could think of using this guide, and every time, it doesn't work. 

However, ```
sudo modprobe r818x 
sudo modprobe r8187
``` just gives me a "Fatal" Module not installed error. Like I said before, I'm using Ubuntu 8.04. I'll look for those modules one last time and try again before I try Ndiswrapper as a last resort.

I`m getting an error message said`s module not found . 
I have downloaded the tar.gz file but i really have no clue how to install the driver by using that type of file format.
I have seen the . deb somewhere and of course accidentally i have navigated from the page so now i can`t find it. 

So now i am so much pissed off ...

---

### Post by scholzilla on 2011-08-18
you might try upgrading to 10.04. Years of struggle with my rtl 8187 problems ended once I did this.

---

