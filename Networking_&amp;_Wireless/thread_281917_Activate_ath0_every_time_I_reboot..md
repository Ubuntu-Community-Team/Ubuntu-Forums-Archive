---
title: "Activate ath0 every time I reboot."
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by synaptyx on 2006-10-21
Hi folks!
I'm brand spanking new to this, so go easy. ;)

I managed to install Ubuntu on my laptop and got the wireless card (Atheros) to connect by activating it in Administration>Networking, telling it the SSID and telling it to use DHCP. But, everytime I reboot I have to do the same thing again.

How can I make it permanent!?

Any help greatly appreciated.

---

### Post by handy on 2006-10-21
Hi & welcome :) 

Apparently the **Atheros** cards are troublesome?  Do a forum search on **Atheros** you will see a lot of posts, it shouldn't take too long to find the solution.

All the best. :)

---

### Post by synaptyx on 2006-10-21
Thank you Handy. I've seen how troublesome these cards are in the past. Usually I give up at the point they fail and go back to Windows. Not this time, however. I was reinstalling my wife's laptop with Ubuntu and had rebooted several times. I rebooted just now and the settings seem to have stuck! I had just done an Ubuntu update of 44 files. Not sure if that had anything to do with it, but it seems to have worked. 2:10 am here now - I deserve a rest. This was my first success with wireless on Linux! :D Now I need to get Kubuntu working on the machine upstairs, but that's another story... ;) Night, night!

---

### Post by handy on 2006-10-22
> **synaptyx said:**
> Thank you Handy. I've seen how troublesome these cards are in the past. Usually I give up at the point they fail and go back to Windows. Not this time, however. I was reinstalling my wife's laptop with Ubuntu and had rebooted several times. I rebooted just now and the settings seem to have stuck! I had just done an Ubuntu update of 44 files. Not sure if that had anything to do with it, but it seems to have worked. 2:10 am here now - I deserve a rest. This was my first success with wireless on Linux! :D Now I need to get Kubuntu working on the machine upstairs, but that's another story... ;) Night, night!

Great news, it sounds like windoze networking, i.e. you do all the right things but don't get the desired result, so you undo it & do it again, & so forth until all of a sudden it works, & keeps working!!! :KS

---

### Post by osinangi on 2006-10-22
A quicker way to do this is to open a terminal session an type

sudo iwconfig ath0 essid xxx.

I have the same problem. This is the fastest way I can get it going. This will force the card restart the access point association.

---

### Post by handy on 2006-10-22
> **osinangi said:**
> A quicker way to do this is to open a terminal session an type

sudo iwconfig ath0 essid xxx.

I have the same problem. This is the fastest way I can get it going. This will force the card restart the access point association.

Would this work if you had a script to run your command at bootup?

If so?

Here is a good link for securely getting around the **sudo** so that you don't have to put in your password. 

[**_See Post 3 here._**]("http://ubuntuforums.org/showthread.php?t=245618")

---

### Post by synaptyx on 2006-10-23
> **handy said:**
> Great news, it sounds like windoze networking, i.e. you do all the right things but don't get the desired result, so you undo it & do it again, & so forth until all of a sudden it works, & keeps working!!! :KSI now have Kubuntu on my own laptop, my desktop and my work PC. All their various networking bits (another Atheros card in the home desktop) all worked fine! For the first time in years I'm actually enjoying using and playing with an OS! :D I'm making a serious attempt to go with Linux. One thing. I NEED Photoshop, so you know what that means... :-?

Thanks for the terminal tip, Osinangi! I'm scared of commandlines, but I think I'd better get learning something about it. ;)

---

### Post by handy on 2006-10-23
It sounds positive over all! :) 

Search for Photoshop in the forums there are lots of threads.

Also, Gimp is very powerful, just different!

All the best! :KS

---

