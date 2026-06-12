---
title: "Belkin high-speed mode wireless G desktop network card"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by Ers on 2006-12-14
Anyone who knows how to get this card working?

---

### Post by michaelc.nash on 2006-12-16
I can't help you there, but I'm staring the same problem in the face.

---

### Post by Ers on 2006-12-17
You have the same card as me and can´t install it? This is incredible! I have to wireless cards that ubuntu won´t detect directly. Well well... I´m getting good help on the other card :D I´ll post here if I find a solution to the belkin problem.

---

### Post by compwiz18 on 2006-12-19
Run **lspci**.  I just finished helping someone else with a Belkin high speed card, so if you have the same card, I'll see what we can do for you.

---

### Post by jondecker76 on 2006-12-19
I have the same problem - its a belkin wireless G PCI card. The card is detected by network settings and has my wireless network's SSID configured properly etc.. Running LSPCI returns the following for the belkin card:
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

I am new to Ubuntu so I am stuck for now..  All i know is that the correct setting are entered but I casn't access Internet or see other workgroups or computers on the network.

Does Ubuntu have any kind of wireless signal meter?

Thanks - i'm glad I'm not the only one struggling with this card - can anyone please help us?

thanks,
Jon

---

### Post by compwiz18 on 2006-12-19
Do you have the CD that came with the card?

---

### Post by jondecker76 on 2006-12-20
Yes, i have the CD that came with the card

---

### Post by compwiz18 on 2006-12-20
Put the CD in the drive, and run **ls -R /media/cdrom >> ~/Desktop/log-of-cd.txt** . This will make a file on your Desktop which can be uploaded here, and then we all can figure out which parts of the CD you need to use (I'd just tell you what to look for, but I'm not too sure myself)

---

### Post by jondecker76 on 2006-12-20
Thanks for your help so far. I will do that when I get off of work tonight and post my results.

Also, I visited the MadWiFi website, and both my card and the specific chipset are listed as supported under the recent release that went out this month.
Is it possible that the version of MadWiFi in my Ubuntu installation needs brought up to date? How would I do that if that is the case?

thanks
jon

---

### Post by jondecker76 on 2006-12-21
Ok, I have it figured out.. The solution was right there all along and I feel stupid for not seeing it.

All I had to do was connect to the internet using a wired connection, download and install the Ubuntu updates (i loved how automated this was!)..

After updating the system all I had to do is plug the card in and it worked without a hitch!

If anyone else is having similar problems, the first step is to make sure your system is up to date!  

thanks again,

Jon

---

### Post by benfreed on 2006-12-30
hello! i'm a brand spankin new user and am having the same problems with my belkin atheros card. here's the deal. my card is recognizes and does work but in networking tools/devices there are two 'unknown interfaces' listed. one is (wifi0) and the other is (atho0). I can't get and security to work and the third party wifi utils don't seem to work either. i have everything updated through a hard connection. any ideas????? thanks

---

### Post by jpyanowski on 2006-12-31
Benfreed,

I also have a Belkin G card. The unknown interfaces on my laptop are also wifi0 and ath0. The ath0 is the card. If you select it you should see your Protocol, IP address, and Broadcast info. Hope this helps.

---

### Post by benfreed on 2006-12-31
do you know how i can get encryption working? it works with no encryption.

ben

---

