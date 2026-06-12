---
title: "Difficulty figuring out how to configure my new router for wireless connection - help"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by gluonman on 2007-11-11
I bought a Netgear 108 Mbps Wireless Firewall Router WGT624 v3. I was sooo exited to be able to use my own private wireless connection that I almost ran home. However, that was two days ago and I have yet to successfully connect. I'm stuck.

Since I'm not using Wincrap, I can't just pop in the CD and go through the easy, user-friendly configuration process. The manual that the router came with tells me that I need to enter the IP address into the location bar of a javascript capable browser (I use firefox). When I do, a window pops up asking for username and password as expected. When I type in the router's default username and password (as given by the manual) it doesn't work. The window just refreshes and I don't get any authentication. I've come across other posts that mention having to configure my network settings to enable wireless roaming mode before I can do it, but then nothing works (I just get Page Cannot Be Loaded messages). Otherwise, NETGEAR does show up in my list of networks with a blasting 100% connectivity. I just need to know how to configure it so I can access the internet with it, and then figure out how to make it a high-security connection.

:confused: Might an Ubuntu veteran provide me with a noob-friendly how-to? It would be much appreciated.

---

### Post by kevdog on 2007-11-11
If your are typing the ip address of the router in firefox and receiving a popup box asking for your name and password to access the router, then there is nothing wrong with Ubuntu.  You need to confirm on the popup box that it states the essid of your router (not your neighbors) and that you are typing the correct  name and password. If all else fails, grab a paperclip and hold the reset button in on the router for 20 seconds (this is a hard reset) to reset all the routers settings back to the default.  Try again.  It would be best to do all these things with a wired connection rather than wireless, in fact Im not sure if wireless will even work since I thought you had to activate the wireless access point capabilities in the router after logging in.

---

### Post by gluonman on 2007-11-12
It did come with an ethernet cable, but I can't use it to plug the router into anything (other than my laptop).

---

### Post by SpiritIsReality on 2007-11-12
howdy
If you do not have the router plugged in to anything, how are you trying to reach the internet? Do you have an internet service provider?
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)
trails

---

### Post by SpiritIsReality on 2007-11-12
howdy
If you plug the router into your laptop, then I think you can type the ip address of the router (see router manual) into firefox and it should connect after using the default username and password from the router's manual.

[http://www.google.ca/search?as_q=WGT624+v3&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=WGT624+v3&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=router&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=router&titlesearch=Titles)
[https://help.ubuntu.com/community/Router?highlight=%28router%29](https://help.ubuntu.com/community/Router?highlight=%28router%29)
[http://www.google.ca/search?hl=en&q=WGT624+v3&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=WGT624+v3&btnG=Search&meta=)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)
links
[http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
[http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)

---

### Post by Peter09 on 2007-11-12
Might be worth resetting the router, so that you are sure that it has the default user id and password in it. (oops, see that this has already been suggested)

---

### Post by gluonman on 2007-11-12
I have just discovered the cause of my problems. I have talked to probably 24 people on this forum and on IRC #ubuntu, and amongst savvy friends and followed everyone's advice to no avail. So I've been VERY frustrated.
Anyway, I called Netgear's tech support and found out that the router requires a modem or ISP in order for a connection to be established. My wireless card and/or connection between my laptop and the router via ethernet cable will not suffice to configure it. So, I have to pay for an ISP and a modem to get the router working.
The thing that erks me, though, is that the salesman who sold me the router, nor the manual it came with, nor any of the 20 odd people I've sought help from ever once mentioned the need for an ISP or modem.

---

### Post by Peter09 on 2007-11-12
Are you sure you need the modem, I do not know the router but is the modem built in?

---

### Post by SpiritIsReality on 2007-11-12
howdy
here's a link that might help [https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)
I got there by going to
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)  and clicking on the Internet and Networking link, which took me to [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking) and then click on
InternetHowTo . Here's some links [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
trails

---

