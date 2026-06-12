---
title: "Picking up wireless network and connecting, but no internet"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by leingod86 on 2008-01-15
My wireless card is picking up my router and connecting to it, however I have no internet and am not being assigned an IP Address. This card has had issues with Windows on boot-up, as I usually have to repair the connection 2-3 times before it finally works. It's a linksys wireless card, but I'm at work at the moment so the model number isn't immediately available.

Does anyone have any idea what could be going on and/or how to fix it?

Thank you

P.S. Another point I neglected, the network manager spams me to reenter my WPA key every minute or so, despite entering the correct key. (I have double checked using Windows that it is the correct key)

---

### Post by doc_holiday on 2008-01-15
I have exactly the same problem.

---

### Post by Hightide on 2008-01-15
> **leingod86 said:**
> My wireless card is picking up my router and connecting to it, however I have no internet and am not being assigned an IP Address. )

Make sure you have the correct driver for your wireless card installed. 

I would also suggest that you use you ethernet wired connection (if you have one) to check your router configuration details.

:)

---

### Post by doc_holiday on 2008-01-15
I have nothing of security configured on the router to be sure it is not the router.

---

### Post by Hightide on 2008-01-15
HI Guys

I would checkout this tutorial first

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
:)

---

### Post by aflog on 2008-01-15
I too have the same problem... It connects with wicd at **0%**... hows that supposed to work? Other times it freezes on obtaining IP address... ill attach a pic to show u's... (Please note my desktop is Xubuntu 7.10)

Jden

---

### Post by doc_holiday on 2008-01-15
> **Hightide said:**
> HI Guys

I would checkout this tutorial first

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
:)

I did this, the problem stays the same. He just tries to connect to the wireless but has time out and does not get an IP.

---

### Post by aflog on 2008-01-15
Ditto

---

### Post by kevdog on 2008-01-15
Check out my tutorial about connecting from the command line in my signature!

---

### Post by doc_holiday on 2008-01-16
> **kevdog said:**
> Check out my tutorial about connecting from the command line in my signature!

This solved my problem, thank you very much!!!

---

### Post by aflog on 2008-01-16
Solved mine too thanks!

---

### Post by whitewizardcoder on 2008-01-16
/leingod86:  It might be possible that your router is not giving your card an ip address.  This has happened to me a few times.  Try resetting your router, or if that doesn't work, try assigning a static ip to your card.

---

### Post by leingod86 on 2008-01-16
I attempted to use the Ralink driver HOWTO. Unfortunately, after doing as it said, network manager is no longer recognizing that I have a wireless card. I am receiving the correct output from ndiswrapper -l and I have tried both variations of the interfaces editting (with and without using the wlan0 lines). However, no matter what I do, I cannot get it to recognize wlan0 as a valid interface. In fact, my only available interface is eth0 now, making it impossible to connect using the terminal. Can someone please help me out?

Edit: To clarify, Ubuntu is acting as if my card no longer exists at all. However, when I used ndiswrapper -l it seems to see it (assuming DEVID 13B1:000D is my wireless card). Network Manager is acting as if I only have a landline connection available now (it wasn't prior to the ralink HOWTO changes) and only has Ethernet (eth0) in my list of available interfaces. Also, the card has/still does work on my Windows XP partition.

---

