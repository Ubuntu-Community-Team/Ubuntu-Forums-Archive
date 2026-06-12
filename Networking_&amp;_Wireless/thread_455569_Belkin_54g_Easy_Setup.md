---
title: "Belkin 54g Easy Setup"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by theironchef on 2007-05-26
Alright I am a complete n00b and have installed Ubuntu a million times. It was such a pain to go through the tuts on installing the Bellkin 54g Wireless card( F5D7011 ). So recently I just made those tuts into a shell script and put the files on my personal site. All you need to do is plug into ethernet port and run the script. Then your wireless card will be ready.

This ONLY works for the Belkin Wireless 54g. Note this is for completey new people to Ubuntu and are frustrated because they can't go wireless!

DIrections:

first...
```
wget http://shadyserver.com/linux/bcmwl5/BelkinDriver.tar.gz
```

second...
```
tar zxvf BelkinDriver.tar.gz
```

lastly...
```
./BelkinDriver
```


And that should be it. If anyone else has done this I'm sorry. This was more of a learning experience for myself anyway.:)

---

### Post by Orgelkraft on 2007-05-28
Which chipset is this for??? Belkin made three versions of their wireless 54g pcmcia card. I have version 3000 (3) with the RaLink RT2500 Chipset. I thought I would try to sort this out again before I buy a new card to replace it tuesday.  I have been trying to get it working for a month and a half, fooled with NDISWRAPPER and even tried to make the drivers on the RaLink site work. I know I will never own another peice of gear with a RaLink chip in it!!!! RaLink sure isn't going to make any money by not releasing the driver information.....they will never make any more money from me or our business if I can help it. Please excuse a month and a half's worth of ranting, I'M ALMOST LOOKING FORWARD TO USING IT FOR SKEET PRACTICE EVEN IF I GET IT WORKING!!!!!!! I can buy a card that Linux will see for $30 and unload this turkey on ebay for $5 if I don't shoot it first!!!!!! PULL!!!

Mark

---

