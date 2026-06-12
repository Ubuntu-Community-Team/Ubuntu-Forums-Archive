---
title: "Atheros AR242"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by racie on 2008-07-09
Upon Googling and searching everywhere in the forums, I came across a successful case of an Atheros AR242 card.  [http://ubuntuforums.org/showthread.php?t=756318](http://ubuntuforums.org/showthread.php?t=756318)  Can someone summarize this thread for me and explain in it simple terms because I'm not that great with computers and I'm new to Linux.  What is HAL?  And how can I make my Atheros AR242 (non supported) wireless card work?  I don't have the disk because the card was built-in when I got this computer.  This is different from my other question on WiFi because I had Xubuntu then, but it had a massive error so I installed Ubuntu.  lol  Please help!

---

### Post by racie on 2008-07-09
Update: I did all of the comands in this thread: [http://ubuntuforums.org/showthread.php?t=756318](http://ubuntuforums.org/showthread.php?t=756318), restarted a couple times, disabled Atheros, etc, but it still doesn't work.  Any suggestions?  I'm desperate.  =P

---

### Post by racie on 2008-07-09
Bump. :biggrin:

---

### Post by racie on 2008-07-09
omg, PLEASE help me.  i really need some help.

---

### Post by Mr_Mischif on 2008-07-23
OK, I'll take a shot.



I had the same problem getting my computer's wireless card up, but something you should know is that it's not the AR242, it's most likely the AR5007.



That being said, these two tutorials did it for me, although I waited until both items were installed before I did the final "sudo modprobe ath_pci"



[IMG]http://i10.photobucket.com/albums/a144/mrmschf/help1.png[/IMG]

[IMG]http://i10.photobucket.com/albums/a144/mrmschf/help2.png[/IMG]

---

### Post by chudux on 2008-07-24
Please post the direct links to the threads of those screen captures.

Thanks

---

### Post by harry666t on 2008-12-19
Seconded! I have a similar problem.

---

### Post by wwusnobrdr on 2008-12-19
The links are BOTH right there in those screenshots, but to help those lazy people who need links here you go :-)


[First Screenshot link=HOWTO: Atheros wireless, including AR5007EG]("http://ubuntuforums.org/showthread.php?t=743299")
As of Intrepid Ibex (Ubuntu 8.10), this HOWTO is considered obsolete. Please use [this wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") instead.


[Second screenshot link: Success making HP Pavilion DV6700 fully functional!!!]("http://ubuntuforums.org/showthread.php?t=792158")

Enjoy the link goodness.  I know how much of a pain wireless can be, I actually came to the forum because my ar5007 wifi broke after latest kernel update.  It looks like ath9k kernel drivers were installed looking at my /var/log/messages file, so I will do some more digging and update this when it is fixed.

---

