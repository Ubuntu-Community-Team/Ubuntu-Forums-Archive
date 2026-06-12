---
title: "Wireless antenna"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by NetMonster on 2007-08-05
Hello everyone :) I'm relatively new to Linux and I'm trying to set up a wireless network with our second computer. I have an ASUS Wi-Fi-AP Solo wireless antenna. Where can I find the necessary software for Ubuntu to recognize it?

Thanks!

(*I posted the above in "absolute beginner talk" as I hadn't noticed this part of the forum. I got a reply by agurk--*

Your wireless chipset seems to be the Realtek 8187. As I understand it, by reading other posts on the subject, is that Ubuntu comes with a driver which only lets you connect to unencrypted networks. If you want to be able to use WEP or WPA, you'll need to use either ndiswrapper + Windows driver, or compile a Linux driver yourself. I'd try the latter first, there are some instructions over at [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

*and posted this followup--*

Sorry, I seem to need a little help here. The first two commands of the suggested script (ifconfig,rmmod) result in errors. It can't find the connection or the module.

BTW sorry if this is a dumb question but what is this "chipset" you mentioned? I've never heard of the term. I guessed it's part of the card, but I should have asked from the start.

*I guess here would be a more appropriate place to discuss my problem.*)

---

