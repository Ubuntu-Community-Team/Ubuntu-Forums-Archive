---
title: "Need help with F5D7000 Wireless Card"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by ShrewHead on 2006-08-05
Hiya there. I'm a little new to linux; I only installed it because I screwed up my hard drive without a Windows XP boot disk... Yeah

Anyways, I'm on a different computer right now and I need to set up the Belkin F5D7000 card. I've read every tutorial on the internet about ndiswrapper and I've followed them up to the point where I've got the driver, ndiswrapper-ed it and then did something with modprobe. However, when I go to the Networking section of the admin tool, I only see eth0, eth1 and ppp3 and no mention of wlan0 which every tutorial seems to assume will always be there. Once that appears I'll be home and dry but any help as to how to get that to appear?

Please? :(

---

### Post by spd106 on 2006-08-05
At the terminal try ```
iwconfig
```This will tell you which interface is the wireless one.

---

### Post by ShrewHead on 2006-08-06
Cheers for that advice. I've typed that and wlan0 doesn't even turn up, but there's loads of statistics underneath eth1, so I thought: "Ah, that must be the one!" However, when I type in the network information into the window that pops up, I click "Ok" then "Activate" it takes ages then says it is active. I then click "Ok" on the networking window. It takes ages to shut down, nothing works and when I check the eth1 connection has disactivate itself again.

In addition to this, I only just noticed that ther eisn't a lght on on the back of my card... Most tutorials mention this being on, and there certainly is a light that could light up, it just doesn't. Does this have any significance?

Cheers for all the help!!

---

### Post by spd106 on 2006-08-06
Sometimes there is an issue where you have to edit a file. Change the radiostate from a 1 to a 0. I can't remember exactly where but I think it was in the ndiswrapper directory.

Here's the thread where they discuss it [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by weekend warrior on 2006-08-06
Is this the Belkin F5D7000 v3 ? If it is you shouldn't even need to use ndiswrapper or any windows drivers. It's built on the Ralink RT2500 chipset as you can see on this [list from the FSF]("https://www.fsf.org/resources/hw/net/wireless/cards.html") and should be fully supported in Ubuntu. 

I have the Belkin F5D7010 which is the laptop card version of the one you've got and it works out of the box, no configuration needed. Did you try just seeing if it was detected and working first before going through the ndiswrapper setup?

---

### Post by ShrewHead on 2006-08-06
> **weekend warrior said:**
> Is this the Belkin F5D7000 v3 ? If it is you shouldn't even need to use ndiswrapper or any windows drivers. It's built on the Ralink RT2500 chipset as you can see on this [list from the FSF]("https://www.fsf.org/resources/hw/net/wireless/cards.html") and should be fully supported in Ubuntu. 

I have the Belkin F5D7010 which is the laptop card version of the one you've got and it works out of the box, no configuration needed. Did you try just seeing if it was detected and working first before going through the ndiswrapper setup?

Tried that and had exactly the same problem as above.

> **spd106 said:**
> Sometimes there is an issue where you have to edit a file. Change the radiostate from a 1 to a 0. I can't remember exactly where but I think it was in the ndiswrapper directory.

Here's the thread where they discuss it [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

I tried that just now, and it loads of things came up saying "[file]: Permission denied", I retried going through the Network manager and no success.

A puzzlement, eh? :-k

---

### Post by weekend warrior on 2006-08-06
That's a shame you've apparently got a version without the Ralink chip. :(   

Is a bit odd wlan0 isn't there. That said, mine actually comes up on ra0. But there should be *something* there for wireless connection *if* you've done the previous steps correctly.  

Did you disable eth0? Have you rebooted since setting all this up?

No lights on the card isn't *necessarily* a bad sign.The LEDS on my card only come on when a connection is made. But if the tutorials say it *should* be on... then yeah... probably a bad sign.

What tutorial were you using?


EDIT: There was [someone who posted a week ago]("http://www.ubuntuforums.org/showthread.php?t=225896") who said he had his on eth1 too, but it wasn't working for him either.

2ND EDIT: Though apparently it **is** supposed to come up on eth instead of wlan0 as stated [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
> 1.2.3. Setting up the Wireless Card
The device gets loaded as either eth1/eth2 (some weird kernel bug, i am guessing). Find out which one it is by doing a 
iwconfig

---

### Post by oxalá on 2006-09-02
here's a question out of the blue:
how do you tell which driver the card is currently using?

---

