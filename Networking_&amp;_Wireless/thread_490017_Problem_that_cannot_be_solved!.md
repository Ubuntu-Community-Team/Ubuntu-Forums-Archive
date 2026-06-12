---
title: "Problem that cannot be solved!"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by dingorunner on 2007-07-02
I added this thread some days ago:

Hello, I've been using Ubuntu Feisty for a couple of months and everything was going great until eventually Gaim stopped being able to connect to MSN and I realised that I have the same issue with Firefox and [http://www.hotmail.com](http://www.hotmail.com). At the beginning I was able to login to MSN and check my hotmail from Firefox but now I can't. but I'm able to login to MSN from Meebo.
I have XP in this computer (because I haven't being able to configure any VOIP program to support my local VOIP provider), well the funny thing is that I can access Hotmail using Firefox in XP and Windows Live Messenger works just fine.
I hope you guys could help me fixing this issue.

An then added this info:

hello, I have new data for regarding this issue;
Another unaccessible web; [http://www.dattebayo.com](http://www.dattebayo.com). I'm in ubuntu using LiveCD; guess what,. same exact problems; No MSN, no Hotmail. and no other webs I've already
mentioned.
When I try to visit one of those websites firefox 'tries' opening it but eventually it goes;

The connection has timed out

The server at [www.hotmail.com](www.hotmail.com) is taking too long to respond.

* The site could be temporarily unavailable or too busy. Try again in a few
moments. (It's been 3 days)

* If you are unable to load any pages, check your computer's network
connection. (I can load a lot of other pages)

* If your computer or network is protected by a firewall or proxy, make sure
that Firefox is permitted to access the Web. (I don't use proxy and I already tried 'sudo firestarter -p' and besides, this issue started before I even installed firestarter)


I hope that info was helpful.


Now I'm kinda hopeless since it's been like three days and nobody has replied since someone told me to change the MTU settings.

So far this is a problem without solution and this is everything I tried:

- MTU settings > 1400
- Tried using OpenDNS > change the prepend line in on dhcp.client with the OpenDNS addresses. 
- Disabling ipv6 on firefox
- aMSN (doesn't connect either)
- Flushing iptables
- Installed firestarter and created a 'rule' that allowed traffic at port 1836. (didn't work)

I'm really sorry to re-post this but I'm sure I'll get some replies faster since people forgot about the old thread.

---

### Post by Old *ix Geek on 2007-07-02
I'm sorry you're having problems and--believe me!--I know how frustrating it is to ask for help and not get any (my posts almost NEVER get any replies at all).  Anyway...I can't really help you with your problem, but wanted to let you know that I tried the links you're having trouble accessing and they all worked for me--in SeaMonkey (my normal browser), Opera, Firefox, and Konqueror.  Have you tried other browsers?  If not, why not give that a whirl so at least you'll know if the problem is specific to Firefox [on your computer] or if it's across the board.

---

### Post by Ayuthia on 2007-07-02
Have you tried clearing your cache or cookies in firefox?

**Oops!  I missed the gaim not working part.  My comment would most likely not work.**

---

### Post by avik on 2007-07-02
Can you ping or traceroute to those sites?

---

### Post by inuyokai on 2007-07-02
This will sound stupid but I'm a newbie and I like trying to help; but, have you tried removing Gaim, aMSN, FireFox and reinstalling them?

Did you do anything else with your network settings prior to this problem occurring? Are you having any issues with your router or modem?

Try investigating those things first before changing a bunch of other settings; I find that sometimes its the stupid things that cause problems in (K)ubuntu and are easy to fix but not obvious.

---

### Post by sebas.rhcp on 2007-07-02
try connecting on a web based messenger I tried meebo and it works, but connecting with kopete it doesn't, maybe there are routing problems on the net

---

### Post by dingorunner on 2007-07-02
I think It has to be more with the ubuntu settings since everything works fine in XP. Yeah I actually was using GAIM and when I had this situation I installed Pidgin but It didn't solve anything. (Pidgin can connect to Google Talk, Yahoo...).  What does it tell you the fact that I have the same issues when I run ubuntu from the LiveCD ?

---

### Post by inuyokai on 2007-07-03
Tells me that ubuntu doesn't want you to chat with people....

Just joking. 

It's got to be something with the way your network settings are configured when (K)ubuntu loads. Have you checked all of the connection settings?

---

### Post by dingorunner on 2007-07-03
What kind of settings? I checked my Network DNS's address and compared then to the one's in XP and they are correct. I also got several IP address such as Subnet Mask, Gateway and DHCP server; but I'm not sure if I can change those when I'm using Ubuntu.

---

### Post by Chappy7777 on 2007-07-03
I don't see what you are using to connect to the net with. Modem? Cable? Wireless?

The fact that things work well in XP and not in Ubuntu sounds like modem problems. 

Can you give us some more info re: you setup. Do you have XP and Ubuntu on the same HD?

Which distro of Ubuntu are you using?

Things like this may tell the geeks in here who are linuxyears ahead of me stuff that may be of help.

(Also, this should bump you again).

---

### Post by bobkat60 on 2007-07-03
Another Nooby here. the advice I got was 'don't muck about with iptables ' it's running on installation of ubuntu. 
so I uninstalled firestarter .. went to [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)  and used the tests on there to check my vunerability online, and results came out sound, all I can suggest is go back to basics ...also try the help on the start pagesof firefox - welcome to ubuntu    . good luck.
 Bob

---

### Post by dingorunner on 2007-07-03
I'm use cable modem, I only have one hard drive and 4 partitions:
NTFS > Data
NTFS > Window$
EXT2 > Linux 
Swap.

I use Ubuntu Feisty Fawn

---

