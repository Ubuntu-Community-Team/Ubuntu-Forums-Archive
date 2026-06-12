---
title: "bcm 4318 &amp; Network Manager"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by JReagan1990 on 2007-04-22
hello, everyone.

I have installed fiesty on my laptop which has a bcm 4318 wireless card built-in.  As usual, I intalled the drivers via a well working script from one of the HOWTO's here in the forums.  For me, I've always had trouble with Network Manager.  It never recognizes my card.  AS with Linux Mint, I just deleted the network manager and configured my now working card through system > Admin > Network.  It still will not connect, even though it is now set as the default connection.  I tried my ethernet, and it didn't work either.  My wireless sees the network, however, it will not use it as a valid connection.  Do you guys have any suggestions?

Thanks in advance!

Jon

---

### Post by a6500r on 2007-04-26
hello,
got the same problem before,this may help?
on asus a6r/feisty-this is what i'd done-
removed network manager w/ "sudo apt-get remove network-manager"
installed wicd network manger w/c i downloaded from their site

downloaded files from(can't able to arrange my reply-SORRY) [http://ubuntuforums.org/attachment.p...8&d=1177147133](http://ubuntuforums.org/attachment.p...8&d=1177147133) (got this of course from searching this forum)

rebooted and twas okay after entering datas{essid,ip,etc.}cause i dont know how to autodetect network yet w/. wicd.  the speed varies from 30% to 50%.(dont know what does that mean but i get modest speed compared w/ using xp on same machine)

how can I post my own message?thanks

---

