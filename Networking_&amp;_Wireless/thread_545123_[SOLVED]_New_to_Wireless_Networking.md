---
title: "[SOLVED] New to Wireless Networking"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by victor9098 on 2007-09-07
Hello All,

Hope this has not been covered too many times but I just can not find the info!!!

I DO NOT have a home WiFi network. I only plan to use the WiFi when I am In University. Presuming I figure out any connection issues (LapLan2.0 is the Uni network), how do I approach security?

I believe the first thing I should do is create a "new user" with limited permissions and log on as "new user" when I can. But what about encryption? Can other people view or access the infomation I am sending?

You might have guessed I have only come from another OS recently! Any advice would be very welcome.

---

### Post by rivalarrival on 2007-09-07
Security is always a risk/benefit issue. You probably don't hire armed guards every time you make a withdrawal at an ATM, and if you did, people would probably call you paranoid. I'm not saying "Don't worry about it" I'm just saying "Don't worry too much".

LapLan2.0 seems to be what Dublin City University calls their generic, 802.11b Wifi network. The connection itself is unencrypted. 
[http://www.dcu.ie/csd/laplan/](http://www.dcu.ie/csd/laplan/)
From that page: [I]"A word of caution - Data being transmitted on wireless networks may be viewed by third parties. Therefore it is important to use software which encrypts sensitive data. This is particularly important for usernames and passwords. CSD would advise users to make use of secure applications when available eg using the SSH putty program instead of normal telnet and using the SSL option on Outlook and Netscape mail clients." 
[/I]

Most important traffic is encrypted anyway. When you try to login to online banking, the address starts with "https" instead of "http" - the "s" means it is using an encrypted (or secure) protocol to transfer the information to the address in the title bar. 

Your e-mail is normally sent in the open. To enable SSL, you'll have to get the information from your email provider. Most offer it, most also require it.

I'd focus on installing and configuring a firewall. I use Firestarter on my own computer and Shorewall on my office network - both work well, and there is a ton of information out there on getting them configured.

Basically, though, I wouldn't access my bank account or any other sensitive site over an open wireless network like this one. Other people can potentially see your network traffic, so if you avoid anything they might find interesting, you should be fine.

---

### Post by victor9098 on 2007-09-07
This Forum continues to amaze me!

Thank you for such a well researched reply! Your right, maybe being slightly paranoid and like most security issues with Ubuntu you really have to open the door for them to get in.

Yes, I have Firestarter installed in it's default mode. So like you said, while on the wireless I will presume someone could be watching, especially since the network is not encrypted. I really should start spending time looking at my 'log files'!? Just to see what they look like at home...or is that the paranoia again? 

Thanks again!

---

