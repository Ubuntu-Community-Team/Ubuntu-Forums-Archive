---
title: "games on POGO &amp; IM's on dating site"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by shorepenny on 2009-05-16
I cannot play games on pogo.com - keeps saying I need to install Java, but I think Java is already installed.  Also, I cannot open or send an IM on jdate - a dating site.  Just will not connect.  Any advice?  I'm very very new to ubuntu.

---

### Post by taurus on 2009-05-16
Did you install (Sun version) java yourself because it is not installed as a default.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-jave6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.  Then YES on the next question.

Now, you need to restart firefox.

---

### Post by SunnyRabbiera on 2009-05-16
Well I am unsure of jdate but I know for a fact Pogo is not very good with linux.
Some games work, some games dont as pogo mainly suits windows users.
A good woerk around is to install WINE and install firefox for windows in it.
Then install all the plugins for windows that way.
There is not much to get around it I am afraid, its the downside of living in a windows oriented world.

---

### Post by Miljet on 2009-05-16
I could never get Pogo games to run when using Ubuntu 8.04, no matter what I tried. But ever since installing 8.10, every game works. Almost every time I start a game, it will bring Firefox to its knees. The screen will grey out for several seconds, then it will recover and run as expected.

I have installed Jaunty on an old desktop and so far, all the Pogo games I have tried works on it too without the initial freezing.

---

### Post by Craig73 on 2009-06-03
I'm on Jaunty as well and I've only tried Cribbage...it generally doesn't work :-(

(I'm looking around to see what people have done to get it to work)

---

### Post by crazypeppo on 2009-06-04
I am running 8.10 and have no problems running any of the games on pogo.
Could it be your connection speed? (ISP) I set up a 'puter for someone else using 8.04 never had any problems either. Make sure you get updates for java... and check connection speed.

---

