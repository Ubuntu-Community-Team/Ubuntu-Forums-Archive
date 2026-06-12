---
title: "Boosting wireless g signal strength of atheros card?"
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by wbeck85 on 2005-05-19
My problem is: I have a laptop with an atheros based card. Ubuntu detected it no problem. Using network-admin, I have configured my wireless card to use a static IP for my home network. In my home, I have 4 other computers all running Windows (1 XP Pro and 3 Win2KPro) They share a dialup connection to the internet (Curse you rural town! (i don't even have cable run up my road). One of the win2k machines is in a closet, dailing up to the internet at the request of the other 3, and sharing the connection via Windows Internet Connection Share over a linksys wireless-g network. It all works peachy(except for being so doggone slow). Sharing files between computers, I typically get transfer speeds of 1 - 5 megabytes per second. However, today, I just tried to transfer a Fedora Core 3 iso from one of the computers to my laptop. The estimated time of completion was an hour and a half! I thought that was rediculous and figured it might have had something to do with samba. So I set up a local ftp server on the computer with the file and tried to get it that way. firefox gave the same estimated time of completed and my download speed never went above 100 kb/s and averaged around 50 kb/s. I thought that was rather weird. I right clicked on the networking applet in the gnome panel and selected properties. Under the general tab, while the iso was downloading to this computer, there is a little indicator that tells the status of the connection. It was switching between "Idle" and "Sending/Recieving". About 60 or 70 percent of the time was spent on "Idle". My signal strength was staying between 60 and 70 percent as well. I though this was plenty strong enough for a 1mb/s transfer speed atleast. but i guess not. I am in the room right next to the one containing the router, I would say I am literally within 10 feet of it.

Out of curiosity, I just set my laptop right next to the router while downloading the iso from the computer next to me. I immediately saw the transfer rate in the Firefox downloads window climb up to 450kb/s and the signal strength of my connection rise to 93%  This is what should be happening from 10 feet away, I think. I have now brought my laptop back to my original workspace and my xfer speed has fallen by 150 kb/s to 300 and my signal strengh is back to 70%. This irks me.
How can I boost my signal from the laptop?

---

### Post by jasmuz on 2005-05-19
[QUOTE=wbeck85]My problem is: I have a laptop with an atheros based card. Ubuntu detected it no problem. Using network-admin, I have configured my wireless card to use a static IP for my home network. In my home, I have 4 other computers all running Windows (1 XP Pro and 3 Win2KPro) They share a dialup connection to the internet (Curse you rural town! (i don't even have cable run up my road). One of the win2k machines is in a closet, dailing up to the internet at the request of the other 3, and sharing the connection via Windows Internet Connection Share over a linksys wireless-g network. It all works peachy(except for being so doggone slow). Sharing files between computers, I typically get transfer speeds of 1 - 5 megabytes per second. However, today, I just tried to transfer a Fedora Core 3 iso from one of the computers to my laptop. The estimated time of completion was an hour and a half! I thought that was rediculous and figured it might have had something to do with samba. So I set up a local ftp server on the computer with the file and tried to get it that way. firefox gave the same estimated time of completed and my download speed never went above 100 kb/s and averaged around 50 kb/s. I thought that was rather weird. I right clicked on the networking applet in the gnome panel and selected properties. Under the general tab, while the iso was downloading to this computer, there is a little indicator that tells the status of the connection. It was switching between "Idle" and "Sending/Recieving". About 60 or 70 percent of the time was spent on "Idle". My signal strength was staying between 60 and 70 percent as well. I though this was plenty strong enough for a 1mb/s transfer speed atleast. but i guess not. I am in the room right next to the one containing the router, I would say I am literally within 10 feet of it.

Out of curiosity, I just set my laptop right next to the router while downloading the iso from the computer next to me. I immediately saw the transfer rate in the Firefox downloads window climb up to 450kb/s and the signal strength of my connection rise to 93%  This is what should be happening from 10 feet away, I think. I have now brought my laptop back to my original workspace and my xfer speed has fallen by 150 kb/s to 300 and my signal strengh is back to 70%. This irks me.
How can I boost my signal from the laptop?[/QUOTE]
 I would recommend you maximize the capability and range of your network (done easily by adding an antenna to the transmitter, or making a home-based one antenna).

Why do your transfer and signal rate go down?--> If you have your server in the CLOSET, it means the signal cant spread evenly, and/or the signal is being absorbed by the nearby walls (pretty common).

Let me know if you make any modification, and how it turns out.

These are some ideas you might want to check out:
[http://www.freeantennas.com/projects/template/](http://www.freeantennas.com/projects/template/)
[http://www.wwc.edu/~frohro/Airport/Primestar/Primestar.html](http://www.wwc.edu/~frohro/Airport/Primestar/Primestar.html)

---

