---
title: "Weird network hardware compatibility issues"
date: 2015-06-01
forum: Networking &amp; Wireless
---

### Post by e_james on 2015-06-01
This is not exclusively a linux / ubuntu question. I have PCs in my network running Lubuntu and Linux Mint and I also have Android smartphones and tablets and PCs running Windows XP or Windows 7. If there is a more appropriate forum, please advise.

Basically my network looks like this

All wired devices  ----------ZyXEL-----------TP-LINK------------Dynamode--------- all wireless devices

ZyXEL is a 16 port gigabit switch model GS1100-16   
TP-LINK is a TD-W8960N 300M Wireless N ADSL2+ Modem Router
Dynamode is a R-ADSL411N 802.11n 300Mbps Wireless Router with ADSL2+ Modem

The Dynamode router is the current connection to the internet. The TP-LINK router is simply acting as a switch - wifi is off, DHCP is off and internet is unplugged.

The weird part is that, at this time, all wired devices have internet access and all wireless devices have local network access but no internet access, at least as far as I have tested. Additionally, if I remove the TP-LINK and attempt to connect directly from ZyXEL to Dynamode, the connection fails. It looks like the handshake tries and fails. I did try more than one port. Possible crossover issues?

Up to about 36 hours ago I was using the TP-LINK for internet access with no apparent problems until I had a chat with my ISP (talktalk). The consequence of that chat was that they reset my login and now it seems that only the Dynamode can login. I may have misunderstood some of the settings.

More clues. 
For many months I have been unable to login to my bank from my own network although I could do it from other networks including the mobile phone network. I can now login from my network using my Windows XP laptop on ethernet. 
One of the first things I did after successfully connecting to the internet from the Dynamode was to try Netflix on my smart TV. It worked for about 2 minutes and then the TV reported that there was no network connection. The "smart" TV refuses to believe that a network connection is possible if it can't see the internet.
Currently I have no landline telephone service (2 lines, one cable) which is why I was chatting with talktalk. The broadband does appear to be working.

I am wondering if IPv6 has any relevance in this matter. I had a vaguely similar experience with ubuntu 6.10 and IPv6 was a factor. I had to specifically disable IPv6 in order to get Firefox and Thunderbird to work properly.

Any comments?

---

### Post by gordintoronto on 2015-06-01
Your networking questions are beyond my pay grade, but they sound like DHCP issues.

Dump XP! It's not secure! If the users need Windows, install Windows 8.1. I have users running it on some pretty grotty old hardware, with no complaints. The only issue might be memory.

---

### Post by e_james on 2015-06-01
> Dump XP

I suspected someone would make such a comment. I refer you to these links
 
[http://www.linuxquestions.org/questions/linux-software-2/why-i-can%27t-leave-windows-xp-for-linux-gui-file-search-required-4175507143/](http://www.linuxquestions.org/questions/linux-software-2/why-i-can%27t-leave-windows-xp-for-linux-gui-file-search-required-4175507143/)
[http://forums.linuxvoice.com/viewtopic.php?f=3&t=196](http://forums.linuxvoice.com/viewtopic.php?f=3&t=196)
[http://www.python-forum.org/viewtopic.php?f=12&t=15800&p=30348#p30348](http://www.python-forum.org/viewtopic.php?f=12&t=15800&p=30348#p30348)

I still use XP for some jobs because it is the best OS I know for those jobs. If you have a better solution, I would like to hear about it.

---

