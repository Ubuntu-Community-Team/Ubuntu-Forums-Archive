---
title: "Windows and Ubuntu on the same Router"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by teddybairs on 2007-01-06
We happen to have problems with our router at home. We have a total of five computers which are supposed to be able to connect. Three of which are dell (one of which dells I have loaded Kubuntu on). The wireless connections on the windows systems (XP Home Edition) are giving errors having something to do with the ip address. The Ubuntu systems are working on the ethernet cables, but are not able to connect wirelessly for the same reason (I just got the wireless card working two days ago on my dell laptop with ndiswrapper, and I can connect to other wireless networks without issue).

My sister attempted to get help from Dell support after the Time Warner guy didn't help at all, and after walking her through a bunch of stuff on the Dell laptop concluded that it was because the other two systems were running linux. I would understand if this was the case if one of the two linux systems were set up as a server, but they're not. They're both clients connected to the same router as the other Windows systems. Apparently the Dell support person said that it was because you couldn't have two different OSes connected to the same router. I have never heard of this before, and I've worked in numbers of server rooms and computer labs where I've seen a motley number of oses all crammed into the same routers (NT, XP, 2003, Solaris, Linux, and others I couldn't identify).

Could someone help me? At least tell me that the Dell person was clueless so I know I'm not.

(Also, I appreciate a good Windows joke as much as the next person, and yes Windows is a joke all by itself, but I really need a good answer so please reply seriously.)

---

### Post by _simon_ on 2007-01-06
I can't help with your problem but this...

> 
the Dell support person said that it was because you couldn't have two different OSes connected to the same router.


... is total crap!

That's the problem with some tech support people, if they don't know then they make stuff up! I know as I used to do tech support and heard it going on.

---

### Post by hatstand on 2007-01-06
I have a router leading to 2 windows boxes, an Xubuntu box (laptop) and my Ubuntu desktop. No problem.

Your problem has nothing to do with OSs. It is a familiar problem on these boards of wifi support for ubuntu. I suggest you look up the threads and in the "How To" section to see how you can connect Ubuntu to a wifi network. I am using cables, so can't help you.

Good luck.

---

### Post by tturrisi on 2007-01-06
You can run different op systems in separate comps all on the same lan via the same router.  It sounds like you just may have conflicting addresses on the lan.  

Best to set all wired computers using static ip addresses, that eliminates potential conflicts in addressing.  Since most wifi comps are laptops, it's best to use dynamic addresses for them.  Access the router control panel & delete all of the dhcp clients in the list, power down the router, power down the comps, power up the router then boot each comp one at a time.

---

### Post by teddybairs on 2007-01-06
thanks for the reaffirmation that I do have some inkling, however minute, of what I am talking about. The Dell support guy had my sister so convinced that she and my mother were trying to convince me to wipe the Ubuntu and put XP back onto it (just for the record, I refused).

tturisi, how exactly do I set static and dynamic ip addresses. I may not be a full newbie, but I know networking is my weak point.

That actually does explain a lot with the ip addresses, like why we're able to have only two computers online at the same time (even when one is windows and the other is edubuntu), but the others can't be.

---

### Post by chili555 on 2007-01-06
First of all, I would check the Administration or Setup page of the router to see if it is set to only hand out two addresses dynamically, also known as DHCP.

Open up a terminal and type sudo route -n. The gateway, the router's IP address, will be shown, for example, 192.168.1.1.

Open up a browser and go to [http://192.168.whatever.wherever](http://192.168.whatever.wherever). A password will be requested. Look at the documentation for your router and enter the password, if you have not changed it. It is often admin.

In the case of my router, the DHCP server is enabled and is set to give out up to 50 addresses starting with 192.168.1.100. Is yours set too low?

To set your computers to static addresses involves IP configuration in XP. I can't help you, because I haven't touched a Windows computer in years. In Ubuntu, drop down System -> Administration -> Networking and highlight the method you are using to connect, ethernet or wireless, and click Properties. Change to Static IP and put in the address you want. Using my setup above, you might pick 192.68.1.110. The subnet mask can be determined from a working connection with sudo ifconfig -a. In my case Mask:255.255.255.0 is shown, so use that, and Gateway is the IP of the router, in my case 192.168.1.1.

Good luck, have fun and let us know if you need help.

---

### Post by tturrisi on 2007-01-06
Follow the instructions from chili555, but first verify that your router can use static ip addresses above 192.168.1.100+.  Most routers have a setting that for example delegates static ips in a certain range: 192.168.2-50 and dynamic ips beginning with 192.168.1.100 & upward.  My Linksys 8 port router uses static addresses between 192.168.1.2-99 and dynamic 192.168.1.100-253.

To set a static ip in  windows xp:
1. rt click My Network Places
2. click Properties
3. rt click Local Area Connection
4. click Properties
5. highlight Internet Protocol (TCP/IP) &
6. click Properties button
7. check the radio button Use the following IP address &
8. enter local ip address 192.168.x.x
9. check the radio button Use the following DNS server &
10 enter local ip address of the router 192.168.x.x (let the router handle DNS, it maintains a table of your isp DNS servers)
11. reboot OR use command prompt and enter:
ipconfig /release
ipconfig /renew
& if no joy then reboot.

---

### Post by teddybairs on 2007-01-06
you guys are lifesavers. Thanks. The router was set up by Time Warner Cable so I don't have the password to get into it's page, although I've seen them get into it. I'll play around with it some more and gather more data. So far I've checked the ip addresses on four systems in the house, two windows, and two ubuntu. Two desktops and two laptops. It seems to be able to assign above 192.168.0.1 without too much of a problem. 

Well, it's all a learning experience. A frustrating one, but still a learning experience.

---

### Post by tturrisi on 2007-01-07
What model router from TW?

---

### Post by teddybairs on 2007-01-07
Netgear cg814wg wireless cable modem gateway

---

### Post by tturrisi on 2007-01-07
> **teddybairs said:**
> Netgear cg814wg wireless cable modem gateway
Netgear default username & bpassword is:
username: admin
password: password or 1234
The firmware for that model is provided by the isp, thus the defaults may be different.  You need to contact your isp to get login info.  A shot worth trying is to use admin as the username and the password of your main account w/ the isp, which is usually the same as your main email account password.  Also, check the TW site support docs of the isp.

---

### Post by tturrisi on 2007-01-07
> **teddybairs said:**
> Netgear cg814wg wireless cable modem gateway
Netgear default username & bpassword is:
username: admin
password: password or 1234
ip: 192.168.0.1
The firmware for that model is provided by the isp, thus the defaults may be different.  You need to contact your isp to get login info.  A shot worth trying is to use admin as the username and the password of your main account w/ the isp, which is usually the same as your main email account password.  Also, check the TW site support docs of the isp.
TW:
[http://www.timewarnercable.com/CustomerService/FAQ/TWCFAQCategories.ashx?CatID=15&MarketID=0&Page=1](http://www.timewarnercable.com/CustomerService/FAQ/TWCFAQCategories.ashx?CatID=15&MarketID=0&Page=1)
Netgear router:
[http://kbserver.netgear.com/products/cg814wg.asp](http://kbserver.netgear.com/products/cg814wg.asp)

---

### Post by teddybairs on 2007-01-07
Ok, I got into the administration page of the router, but I'm not seeing anything which would indicate a limit on the number of dynamic ip addresses it can handle. It looks like it's set up so that all of it's configuration information is coming from the isp.

Wait, I found it. The beginning ip is set to .10 and the end is set to .13; if I change the end ip address to, let's say, .19; will that fix the problem?

---

### Post by Skidpad on 2007-01-07
It sounds like it. Most routers are by default configured to give out more than 3 IP addresses,perhaps yours was limited during initial setup?  (My D-Link defaults to 99).

Change the IP range to a number at least equal to the number of computers you are trying to connect with, and then see if each will connect.

---

### Post by tturrisi on 2007-01-07
You can set the "end" ip to a number that = 50 more than the beginning.  That's how most Linksys routers are pre configured.  Chances are that your isp set the initial number to a low one so if users run into this situation they call the isp who then sells the cust additional ip addresses for 6 bucks each/mo and then charges the cust to come & config tne router.  Some isps allow home networking w/ routers so as to share the net connection (using a single isp provided ip address) and their promo says something like "up to 3 comps can share the connection blah blah blah".  The truth is that up to 253 comps can share the connection on one router!  And other routers can be added to increase that number almost infinately using different subnets.

---

### Post by Skidpad on 2007-01-07
^^^ Agreed!

---

### Post by teddybairs on 2007-01-07
Thanks guys, I really appreciate it. I'm going to finish my battle plan and put it into effect over the next couple of days when certain people aren't in the house to complain. I'll let you know the results.

---

### Post by handy on 2007-01-08
You should be able to flash the firmware of your router with an update or at least the original unaltered firmware, available from the netgear site, bringing it back to standard.

---

### Post by chili555 on 2007-01-08
Are you leasing this router from the ISP? Usually, it is cost-effective and permissable to buy one instead. You can then set your own user name and password. 

Let's see...leased for $4.95 a month times infinity months versus purchased from Newegg for $60 once...hmmm.

---

### Post by GolfGeek on 2007-01-08
With my netgear router, it was set up as ADMIN as the user and password as the password.  oth the routers leave the passowrd blank. Hope it helps

---

### Post by tturrisi on 2007-01-08
> **handy said:**
> You should be able to flash the firmware of your router with an update or at least the original unaltered firmware, available from the netgear site, bringing it back to standard.
That particular device is a combo cable modem-router and cannot be flashed using Netgear firmware else the internet will break.  The firmware for that particular device is provided by the isp.  [http://kbserver.netgear.com/products/cg814wg.asp](http://kbserver.netgear.com/products/cg814wg.asp)

---

### Post by teddybairs on 2007-01-09
You guys are my new heroes! I decided to stay with Dynamic Addresses, but otherwise changed the settings from four ip addresses to twenty, and then powered down all the systems in the house as well as the router. I then powered up the router and one of the computers at a time being careful to access the setup page on each system and record the ip address. They're all online right now with no conflicts and different ip addresses. the router seemed to reassign mostly the same ip addresses to the same mac addresses where it could and then reassigned them where it couldn't. But it all works.

I really appreciate all your support and help. You guys told me more about it and actually knew what the problem was as opposed to the commercial "support" peope. Thank you.

---

### Post by chili555 on 2007-01-09
Glad it's working!

Some of us know this stuff because we made the same durn mistakes ourselves a few years ago. Then we read some of these posts and mutter to ourselves, "Oh baby! Not that old trick again!" And then we answer the post.

As your skill grows, don't forget to help someone else sometime. That's how this community works so well.

---

### Post by teddybairs on 2007-01-09
Well, I'm glad you still answer the same posts... over...and over... and over... and over again. Thanks, I'll keep my eye out to be a part of the help instead of just the seeker for help.

---

### Post by handy on 2007-01-15
The wonderful thing about this forum is that you can give a very limited answer as far as one viewer is concerned, that exceeds the requirements of the *initial* poster. :KS

---

