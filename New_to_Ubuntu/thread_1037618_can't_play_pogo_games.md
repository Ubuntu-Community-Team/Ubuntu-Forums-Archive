---
title: "can't play pogo games"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by hiffenscgaupher on 2009-01-11
I need some help on being able to play pogo games. I have the flash player, enabled the java, and I am still getting applet table death when I try to enter a playing room. If someone could please help.I have version 8.04 LTS. I tried a restart, and tried to get to the game, and the same message was received.
I uninstalled and reinstalled the java program required to pogo games, I am still getting the message applet table death.

---

### Post by stoogiebuncho on 2009-01-15
Which java packages do you have installed?  You might try the Sun Java packages if that's not what you're already using.

---

### Post by mihajovics on 2009-03-04
Hi!

I have a similar problem. Java in general works, but I can't play pogo chess.
I'm using firefox and sun java6. And tried sun java5 and iced tea also, installing them with the package manager and setting them from the terminal with

sudo update-alternatives --config java

and tried each one, but with the same results.
Then I tried with another browser, Epiphany, and it worked for like 2 days, but now has the same problem and quits the game randomly. Or opens up the playing rooms, but you can't sit down at a table to actually play.
Wierd.
Any ideas?
Thnx

---

### Post by Lithical on 2009-03-04
My grandmother had this problem a few days ago after a system restore.  She could play some Pogo games, but not her favorite one.  My solution was to get version 6, update 11.  Just try to keep downgrading till you find one that works would be my first solution.

[http://java.sun.com/products/archive/]("http://java.sun.com/products/archive/")

---

### Post by hobo on 2009-03-13
I too have had problems running POGO games in 8.04 after upgrading from 6.06. What I found was TWO JAVA plugins resident in a Firefox subdirectory. Anyways, what I did was remove all JAVA from the system and downloaded the newest JAVA from SUN and installed. Then I deleted the OLD plugin and now POGO works just fine in 8.04 for me.

---

### Post by Alex82 on 2009-03-13
Hello I had loads of problems with this but if you read through this thread....

[http://ubuntuforums.org/showthread.php?t=1085319](http://ubuntuforums.org/showthread.php?t=1085319)

and follow either zika or presence1960 directions you should be onto a winner... just make sure you dont freak out and try to install too many versions or you will have to do what i did and start deleting things

---

