---
title: "WPC54G v3"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by thedragonmaster on 2007-05-17
[B][FONT="Arial"][SIZE="4"]greetings. i am requesting assistance in getting a linksys wpc54g v3 wireless pcmcia card to work in ubuntu. i am a complete newb to linux, infact this is my first install system stats


ibm thinkpad t23
384MB's of ram installd
ubuntu 7.04 installd as a dualboot

linksys pcmcia wpc54g
router uses 802.11b wireless (will upgrade this some day)

ive read some things on how to get this card to work. but i couldnt make heads or tails of it. so please be gentle :) any help is greatly apreciated.

edit: i wanted to mention that i am legally blind and color blind so slightly larger print than normal or atlest bolding would be greatly apreciated :)
[/SIZE][/FONT][/B]

---

### Post by thedragonmaster on 2007-05-19
**[SIZE="4"]well i figured out how to use ndiswrapper. when i go to configure the network it see's the ssid with 76% out beside it. i enter my key and set it for ssh. it cant connect. and the link light on the card never lights up. ideas please?[/SIZE]**

---

### Post by High Roller on 2007-05-19
> **thedragonmaster said:**
> **[SIZE="4"]well i figured out how to use ndiswrapper. when i go to configure the network it see's the ssid with 76% out beside it. i enter my key and set it for ssh. it cant connect. and the link light on the card never lights up. ideas please?[/SIZE]**

[SIZE="4"][B]I had this same problem.  Apparently the best method to solve this problem is to download and compile ndiswrapper.  If you're at a complete loss I would suggest this (but it should be noted that there's a performance hit if you choose this method):

install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot
enjoy wireless.

I really wish these cards would work "out-of-the-box" :)[/B][/SIZE]

---

### Post by thedragonmaster on 2007-05-20
[SIZE="3"][B]i have no clue how to compile an app. so i installd the deb package you provided and id like to say THANK YOU THANK YOU THANK YOU! it workd!, now if i could figure out why my audio quit working shortly after installing ndiswrapper id be one happy camper.

again thank you! :)[/B][/SIZE]

---

