---
title: "Wireless security from a wired connection"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by mukeliller on 2007-08-25
Hello,

I am running Ubuntu 7.04 and have a wired ethernet connection through a WRT54G Linksys router; I use a wireless router for my girlfriend's iBook. What I would like to do is secure my wireless network. Is this possible using my Linux machine or would it better accomplished using the ibook. 

My friend, who converted me to Linux (1 month ago) has suggested a solution via MAC addresses, however I am unsure how to manage that and would like to start using the forums for solutions as opposed to phoning my friend. Thanks, and thanks.

---

### Post by jml on 2007-08-25
I have the very same router/access point and I will share what works for me.  Unless you have enabled remote administrative access for your router, you will have to make the necessary changes through your wired connection.  With your computer connected to your router by Ethernet cable, open your web browser and type in the following URL 

[http://192.168.1.1](http://192.168.1.1)

That should bring up the administrators log in screen.  Type in your user name and password and you should bring up the configuration screen.  From this screen, you can configure you router to your heart's content.  ;)

You have several ways to secure your router, the one I use is WPA encryption, most Linux distros including Ubuntu supports it and is much more secure than WEP.  You can also secure by using MAC address filtering from the configuration application, but I don't have any experience with that process.  Good luck.

Joe

---

### Post by mukeliller on 2007-08-25
I do not know the user name and password for authentication. Because it is a new router I expect there is a default?   ***got it (admin)*** thanks so much for the speedy and USEFUL help!!

---

### Post by jml on 2007-08-25
Glad to be of help.  If you have not already done so, be sure to change the administrator password on your router.  Most people interested in networking know the default administrator password on most brands of common routers and access points.  You may also want to change the ESSID that your router broadcasts.  No need to give people free information about your setup.

Joe

---

