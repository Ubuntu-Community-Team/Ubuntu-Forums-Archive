---
title: "Linksys WPC54G ver.2"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by Mirky on 2006-11-18
I just installed Xubuntu Edgy Elf.
I have to say it was very COOL :D 
It was a little odd (for an old time Linux guy, RH 4.2) to have X windows running while it installed. Very slick I almost didn't know it had not installed :-k 

It's the first Linux distribution that has found my WPC54G ver.2 card.
The power light is on and the link light will blink. This tells me the card
is at least trying to talk to the AP.

I can't connect to the AP is the only problem. I configured the connection in "Network Settings" with the name of the AP and password.
I tried to connect as DHCP but get an IPV6 address, can't use it.
I put in the static IP, Subnet Mask, and Default Gateway, still not working

I have tried $ifdown eth0 but still don't get a wireless connection.

Is there a software I need to install to get to the AP?

---

### Post by Mirky on 2006-11-18
Thanks Frodo the information in the other Thread was perfect.
Hex and a Key fixed the issue.
I now will not go back to Windoze on my laptop, well I have to pull some data from the drive but that will be through USB ;)

---

### Post by dmizer on 2006-11-18
i've read [reports]("http://www.ubuntuforums.org/showthread.php?p=1641339#post1641339") that this card works out of the box in edgy, but that may have changed.  i was using this method: [http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g+the+trick](http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g+the+trick) to get my card to work in dapper, but it's since stopped working.

you may have to rely on ndiswrapper.  i wrote a howto for breezy a long time ago that broke, but i recently applied the same technique to make my card work in dapper.  use it as a guide for using ndiswrapper with this card rather than a howto. [http://www.ubuntuforums.org/showthread.php?t=201633&highlight=wpc54g+the+trick](http://www.ubuntuforums.org/showthread.php?t=201633&highlight=wpc54g+the+trick)

in addition to what's there, you'll also need to blacklist the acx module.

---

