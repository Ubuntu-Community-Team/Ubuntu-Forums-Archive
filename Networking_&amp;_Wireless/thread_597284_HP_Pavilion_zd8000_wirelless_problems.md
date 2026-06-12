---
title: "HP Pavilion zd8000 wirelless problems"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Dorotheos on 2007-10-30
I hate life! Anyone out there that can hack my computer and fix this for me can take anything else, ill even give you the password! Ok, i cant get the card to work! I have done all the config commands and found that it is called eth1 and it is off and disbabled... thats all i know and i want to get on the internet! Please help! I dont speak binary or code, so be very very simple.
Thanx](*,)

---

### Post by SunnyRabbiera on 2007-10-30
there might be a driver out there as HP is normally linux friendly...
but it depends on the card.

---

### Post by WhatTheCoitus on 2007-11-08
1. Add Broadcom Restricted Drivers
2. Download firmware from internet
3. Create a file in /etc/wpa_supplicant/wpa_supplicant
4. Add single line - "ENABLED=0"

---

### Post by hankjw on 2008-02-22
I have a somewhat solution.

Open a terminal window and enter the following command

sudo ifup --force ath1

And the wireless will work. I have a ZD8230us and I am using my wireless now.
You will also need to select the access point by clicking the network icon in the upper left of your screen. You may also need to enter your WEP/WAP key if you have encryption set up on the router.

Type the command exactly as shown; note the double dash prior to the force option.



Have fun

Hank:):)

---

