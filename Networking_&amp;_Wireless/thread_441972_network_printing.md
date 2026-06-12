---
title: "network printing"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by night116 on 2007-05-13
I have just upgraded to 7.04 and now my network printing and network have disappeared and do not work.
I have a brother hl-1230 connected to my windows machine running xp and for the love or money linux will not see my printer or whats on my windows networks. Can anyone please help me of how to setup or point me in the right direction.

---

### Post by tagra123 on 2007-05-13
If you can get the printer to print on the computer its connected you can share it another way. Not pretty but this works until cups gets fixed or someone can actually come up with an answer to the cups problem.

[http://ubuntuforums.org/showpost.php?p=2591426&postcount=8](http://ubuntuforums.org/showpost.php?p=2591426&postcount=8)

---

### Post by king_arthur on 2007-05-13
> **night116 said:**
> I have just upgraded to 7.04 and now my network printing and network have disappeared and do not work.
I have a brother hl-1230 connected to my windows machine running xp and for the love or money linux will not see my printer or whats on my windows networks. Can anyone please help me of how to setup or point me in the right direction.

Not sure if I understand correctly but if the network is gone, it's hard to imagine a network printer to work. :)

Please try shed some light here.

Network printing better than ever on my Feisty install with CUPS.
No need for any useless hacking.

I just went to my Admin preferences, asked to detect networked printers and voilà, I could select my old Epson unusable with WinXP. Done.
Works like a charm.

Suggest you fix your networking first.

/P

---

### Post by tagra123 on 2007-05-13
I think the problem is mainly with previously supported HP printers. Most of the post with problems seem to be HP.   The printer I'm using worked great in breezy cups or samba. Could only share via samba in dapper  -- and nothing on edgy or fiesty. 

All other networking work perfectly -- low latency on both samba and nfs. ALL the machines can communicate.  I'd be glad to post my hosts, exports, cups and other files if you think you can debug the problem. Iv'e wasted enough time. I can't print = I cant get paid.

I'm glad yours worked  king_arthur. Hard to believe it's a  network problem or dapper to dapper and windows to dapper wouldnt work either

---

### Post by king_arthur on 2007-05-13
Hum, 

perhaps my setup needs some further explanation: there is one Apple Mac running Tiger OSX with a Epson Stylus scan attached and shared and several PC's.

Printing from Feisty to that printer is nothing more than trivial.
You just select it and use it, a 2 minutes set-up.

This wasn't working with the same h/w and XP SP2 as Win was asking for drivers that weren't available for networking on XP only win 98, hence no printing. 
So much for Windows backwards compatibility. Thank you Bill.

BTW, I can reverse the process attaching the printer to the Linux box and print any document from the Mac. No problem at all.

/P

---

