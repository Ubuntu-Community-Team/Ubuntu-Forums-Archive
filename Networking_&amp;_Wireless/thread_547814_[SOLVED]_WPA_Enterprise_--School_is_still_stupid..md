---
title: "[SOLVED] WPA Enterprise --School is still stupid."
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Garrulousbrevity on 2007-09-10
Hi, So, last week I got to my college, and I'm trying, trying, to get by everything without needing to reinstall OSX or XP on my computers.  

Unfortunately the IT department at my school is primarily made up of bitter, close minded Dell Help Desk workers, who haven't been all that helpful with any of my issues.  If it's at all avoidable I would like to not go to them. 

When on my laptop I have issues connecting to the school's wi-fi network.  

I suspect that this is Ubuntu related, because the only other people who are having trouble connecting to the wi-fi networks are those who still have their laptops on backorder. 

There are two networks.  One is a normal, non-secure connection, where they make me log in once I'm connected.  I get one green dot if I'm near by (however, not up in my dorm where I'm wired and writing this), but I never finish connecting.

The school also has a network that uses WPA Enterprise, and I'm told that the password and user name are the same password and user name I have to use for everything else school related.  For this connection I don't even get the one green dot.  Nothing happens. 

As for other settings, judging by the guides for [XP]("http://techhelp.mcla.edu/index.php/Windows_XP_Instructions_-_Connecting_to_the_MCLANET_wireless_network"), [Vista]("http://techhelp.mcla.edu/index.php/Windows_Vista_Instructions_-_Connecting_to_the_MCLANET_wireless_network"), and [OSX]("http://techhelp.mcla.edu/index.php/Mac_OS_X_Instructions_-_Connecting_to_the_MCLANET_wireless_network"), they want me to use WPA Enterprise.  They want my data encryption method to be TKIP and to use PEAP.  They have a blurb on editing your PEAP settings, which I have no idea on how to do, but they seem to want a certain authentication method.  I don't know what Ubuntu tries to use. 

I've put all that information into the password entry thing when I try to connect to the network, but alas, nothing.  

If it helps, I'm running on a Macbook.  I have the madwifi drivers and this is the first time I'm really having a problem with it.  

Any advice? 

Thank you.

---

### Post by lsmobrian on 2007-09-10
My school has pretty much the same setup (lol, sounds like we goto the same school by your description)


click the network manager
choose connect to other wireless network
enter the network name(ssid)
choose the security option, WPA enterprise
fill in your identiy and password

that should be it unless they have other steps to follow, look on your schools IT or information services, or help desk website and see if they have specific instrucitions or downloads needed

---

### Post by Garrulousbrevity on 2007-09-17
Hey,  

I was having plethora of small issues with Ubuntu, and being unable to sleep last night, I decided that reinstalling Ubuntu and starting fresh would help. 

It did.  At least with this problem.

---

