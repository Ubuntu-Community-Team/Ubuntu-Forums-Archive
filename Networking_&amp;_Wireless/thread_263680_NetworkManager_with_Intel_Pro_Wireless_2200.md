---
title: "NetworkManager with Intel Pro Wireless 2200"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by volkan on 2006-09-23
[FONT="Georgia"][SIZE="3"]Gentlemen,

I am using Toshiba notebook with Intel Pro Wireless 2200 (IPW200 onwards) card installed running on Ubuntu Dapper Drake. 

I haven't been satisfied with the wireless performance, hence I started looking some other wireless client until having come up with NetworkManager tool which seemed to meet my requirements. 

However, it says, "No Network devices have been found" while I am online via wireless connection. I was wondering how you would guide me to drive it?

Live long and prosper,
Volkan 

[/SIZE][/FONT]

---

### Post by happy-and-lost on 2006-09-23
It is actually working, right?

For Wireless, I highly recommend:
```
sudo apt-get install wifi-radar
```

---

### Post by volkan on 2006-09-23
Thank you very much for your interest, happy-and-lost. I tried wifi-radar after your suggestion. It looks cute, but what I had looked was something lives in system-tray. And, yes wireless is working but I don't feel I've full control of it. Actually I would be more than happy if I could just manage to run this NetworkMAnager thing.. But it instists not to recognize my wifi card. shh..

---

### Post by happy-and-lost on 2006-09-23
I'm afraid no-one's programmed the software you desire yet. Only 6 months ago Linux wifi was almost impossible.

Care to contribute? :)

---

### Post by volkan on 2006-09-23
Woow.. I never think that would be so hard to find. But I thought I found Network Manager, buddy. Anyway, thank you again, hope I would mature enough soon to contribute this wonderful community.

---

### Post by plexi50 on 2006-09-23
In order for network manager to work, you need to de-configure your network connection in network settings, i.e. take out your sys id and password so it does not connect on boot or on its own. Then, nm-applet will allow you to setup a connection thru the icon. Also, be sure that under System/sessions/startup programs you have nm-applet --sm-disable. 
I have found wifi radar to be more stable and hold on to connections better than networkmanager, especially after the latest kernel update. I have no idea why. I use ipw2200 in my Dell M140. 
Just my two  cents.....

---

