---
title: "D-Link DWL-G650M not working"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by keron on 2005-07-07
I have bad experiances with d-link in the past, but this time this wasn't my choice :) Well, I have here a non-functioning  DWL-G650M - and i think that M is part of the problem. I haven't found anybody else posting about this exact card, and I have tried to adopt some  ideas on this forum and the wiki. But no result, which may be because I know just enough about linux to follow clearly written instructions... 

Well, anyway. lspci gives me the following line:
0000:06:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0020 (rev 01)

lspci -n gives this line:
0000:06:00.0 0200: 168c:0020 (rev 01)

can't find anything relevant i dmesg


I've been installing madwifi and ndiswrapper but none of them seemed to do the trick. But i've might have missed something... Any ideas?

---

### Post by lolow on 2005-07-08
I have the same card and I have only succeeded with a wireless network when removing the WEP key. 

Unhappily I want this key...

---

### Post by keron on 2005-07-10
I would be very happy if I got that far :)

how did you do it?

---- Edit -----

Made it work! Have not tried the WEP key since I have no use for it... 

Using ndiswrapper, followed the usefull guides all over the place  :smile: 

The problem was that i used drivers from the install-cd for the card. Somehow I thought they would include correct drivers, but no. 

I found a usefull driver [here](http://support.dlink.com/products/view.asp?productid=DWL%2DG650M)

---

### Post by RLR on 2006-10-17
Hello. I successfully installed this card via ndiswrapper.
I tried the driver on the CD but it did not work.
I downloaded the Win 2000 driver from D-Link website and installed it via ndis-gtk and immediately the card was detected
and all lights on card were green. I waited a couple of minutes and it detected an open wireless network and I was able to connect and surf. I also have signal strength bar in tray.
It works great so far. I will update the steps to istall ndis-gtk
and ndiswrapper for other noobs like myself.
I hope this is helpful.

---

