---
title: "New to Ububtu... Help:P"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by j_penac13 on 2009-02-19
Hey guys! I just installed Ubuntu after seeing a friend use it.
I installed it in a new partition of HD, same HD that has Vista installed.

SO, Im a COMPLETE noob when it comes to this. This is my first time using Linux. And, ofc, I have A LOT of questions....

1. Where is the command line here? Ive read some threads about programs and most of them say, "write this command in order to install the program". Ive tried googling for it... no luck (maybe cuz i dunno the name) 

2. Do Windows games play nice here? I downloaded WIne in order to install .exe files. I installed this game I play (Crowns of Power) and it goes to launcher just fine, but when  you click on play (which would lead you to the login window) it just closes and do nothing.

3. Whats this "Cannot read UDF Volume" thing? I tried inserting a Data DVD, but it wont read it. I burned it from my Vista account in order to free space and then pass it here in Ubuntu, but it wont open the DVD.

4. How do I set up the wired network to STAY? I mean, when I log in, the wired network is ALWAYS changed to default settings. I tried searching how to change the default settings, but I cant find it -.- So everytime I log in, I have to manually set the network up :(

I guess those are the main questions I got right now. Hope I get some answers soon :)

---

### Post by swoody on 2009-02-19
Hi, and Welcome to the Forums):P For the easier answers:

1) In the top, lefthand side click on 'Applications' then 'Accessories' then 'Terminal'. That is your command line.

2)Many Windows games do run really well here. You may want to check out the Gaming and Leisure section of the forums here:
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)
As for what Wine will play, you can check out these links for a HUGE list of what Wine can play:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://www.wine-reviews.net/](http://www.wine-reviews.net/)

I'll have to look a little bit more into the last two, or else someone else might be able to chime in here. Again, welcome to the forums! :D

---

### Post by khelben1979 on 2009-02-19
1. ctrl + alt + f1 will get you to a text console. You have all the text consoles on f1 to f6.

2. I don't know what's wrong over there. But [have a look at this Ubuntu page]("http://www.winehq.org/download/deb") which describes how you should do it.

Okay, so now you have 2 questions left but I'll haveto leave them for someone else.

Hopes it can help somewhat.

---

### Post by superprash2003 on 2009-02-19
3) you could edit your /etc/network/interfaces file and setup static ip there..

---

### Post by Therion on 2009-02-19
> **j_penac13 said:**
> 
3. Whats this "Cannot read UDF Volume" thing? I tried inserting a Data DVD, but it wont read it. I burned it from my Vista account in order to free space and then pass it here in Ubuntu, but it wont open the DVD.
You can thank Vista for that.  MS introduced new "features" with UDF support in Visa that make it incompatible. Think MS Office and *.docx and such.  

Yea!  :)

---

### Post by rgb96 on 2009-02-19
4. Are you trying to give yourself a static IP? If so you are probably going to want to turn network manager off and do it manually by editing the file /etc/network/interfaces.

---

### Post by j_penac13 on 2009-02-19
> **rgb96 said:**
> 4. Are you trying to give yourself a static IP? If so you are probably going to want to turn network manager off and do it manually by editing the file /etc/network/interfaces.

No no, not static IP, just the default DNS. I want it to be 4.2.2.1 and 4.2.2.2 instead of 10.0.0.1 that ALWAYS pops up when I log in.

TY guys for welcome :)
I found the command line too, ty for that!

Still dunno whats wrong with the game... Its not in the list ow WIne games, its a new game that came out like 2-3 months ago...

---

### Post by Kareeser on 2009-02-19
The newer a game, the less likely it'll work on any form of Linux on WINE, unfortunately.

Over time, however, WINE will improve, and you'll be able to play the games you so desire :)

For example, check out Call of Duty 2! Released in 2005, it plays perfectly!

In the meantime, if you'd like to help out the community, consider submitted a test report on the appdb. It'll help others diagnose bugs in the game.

---

### Post by rgb96 on 2009-02-19
Oh. To modify your DNS you are going to want to edit:

```
sudo gedit /etc/resolv.conf
```

If there is anything in there comment it out by putting a '#' at the front of each line, and then type this at the top:

```
nameserver 4.2.2.1
nameserver 4.2.2.2
```

putting whichever one you want it to try to use first at the beginning of the file.

---

