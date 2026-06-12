---
title: "Realtek RTL8187 Wireless 802.11g 54Mbps USB 2.0 Network Adapter #2 Problems"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by darkhacker902 on 2007-07-17
Ok,  So I bought this Gateway laptop, MT6452 and IT came with the internal Realtek RTL8187 Wireless 802.11g 54Mbps USB 2.0 Network Adapter #2 Wireless adapter. Its great, 1gb of ram, 160 GB hdd all that jazz, and here i am in vista, wishing for my ubuntu release that i had customized. So i get on here, Partition my drives and all, am a happy man, until i want to connect to the internet through my wireless. I open up the network console under system>admin>netwok. and it shows 2 wireless adapters, and they both are set to roaming mode. So up on my bar, I can see the network icon, and when i click it, it gives me the option of connecting to the network, so i do, and its all good, but it wont go anywhere. No pages load, at the most, one will, but i open up the network info on it, it shows it sending then switches to receiving real fast, then just goes to idle. all in like 2 seconds, and stays on idle. So i cant browse pages :(.

That is my main issue.

My second issue, is Beryl.


When i go to open it, all i get is this white page. Either that, or everything is extremely choppy :(.

Using an ATI radeon xpress 1150M 128 MB Grphx card.

---

### Post by Jexel on 2007-07-19
Did you install beryl properly?
Here's a guide to installing berly with ati.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

Also in terms of your wireless, rtl8187 drivers are rather dodgy in feisty (i assume you're using feisty?) You probably want to use ndiswrapper to get it fully working. I also have a rtl8187 adapter and after using ndiswrapper it works perfectly.

Here's a howto to getting ndiswrapper working with rtl8187:
[http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

---

### Post by telder63 on 2007-07-24
I have a new Gateway with the realtek too. I have had had nothing but problems with the wi-fi. I took it back to BestBuy. At first the problem was intermitent and I could not get it to error out very much at the store. The geeksquad gave me the normal procedural fix it type stuff. Today, I went back in and the store manager has the same computer with the same error. We are going to work with Gateway and get it fixed now. I think Realtek and vista may not play well together.

---

### Post by darkhacker902 on 2007-07-30
Yup I installed Beryl Correctly. It does the same thing with Feisty's default Graphical dealy, that is supposed to be similar to beryl does the same thing :(


And ill try that Installer for the realtek. thanx.

---

