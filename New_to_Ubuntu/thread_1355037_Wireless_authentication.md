---
title: "Wireless authentication"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by petermadd on 2009-12-14
Hi, I am running ubutu 8.04 on my Toshiba NB100, security type WPA-PSK. All has gone well for 6 months until the last couple of days. When attemting to connect wirelessly to the internet I get "Authentication required by wireless network". When I click on view password there is a very long string of numbers. I tried deleting these and entering my network passord but after a few moments I got the same message. Can anyone help please. Thanks, Pete
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8498454")

---

### Post by fatality_uk on 2009-12-14
Some good tips here!

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

---

### Post by petermadd on 2009-12-14
Hi Thanks for your reply. All solved. Turned out to be a problem with my router. Cheers, Pete

---

### Post by frenchn00b on 2009-12-14
> **petermadd said:**
> Hi, I am running ubutu 8.04 on my Toshiba NB100, security type WPA-PSK. All has gone well for 6 months until the last couple of days. When attemting to connect wirelessly to the internet I get "Authentication required by wireless network". When I click on view password there is a very long string of numbers. I tried deleting these and entering my network passord but after a few moments I got the same message. Can anyone help please. Thanks, Pete
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8498454")

give a try : 

WICD  
```
apt-get install wicd
```
then 
```
wicd-curses
```

---

