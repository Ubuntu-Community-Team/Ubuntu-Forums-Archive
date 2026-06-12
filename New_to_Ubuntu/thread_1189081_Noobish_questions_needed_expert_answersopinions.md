---
title: "Noobish questions needed expert answers/opinions"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by r3cht3r on 2009-06-16
wth, now there's a first. I was going to shutdown my box when all of a sudden a dialog appeared saying that I need to authenticate first before shutting down because there were other **users who have logged in?!? **I was OFFLINE then though my modem was active or powered on. 

1. How is it possible for other users to logged in when I am not even connected to the Internet? I don't have a server though I got wineserver but its only active when you are using Windows applications right? Everything is dropped from the firewall or so I thought. 

2. What set of commands am I going to do to know if some users are logging into my box? Or, any applications to do just that? 

3. Just some scenarios I could think of: Is it possible that somebody's have gotten access while I was online and installed a file that would automate and connect by itself to the Internet at boot time? 

thanks.

---

### Post by SunnyRabbiera on 2009-06-16
As long as you have the modem plugged in and active you run the risk of attracting rouge users wanting to leech off of you.
It happens on all OS's, even linux isnt 100% bulletproof.
If i were you I would install firestarter, just in case.
Also make sure to keep changing your passwords often.

---

### Post by prvteprts on 2009-06-16
Maybe you or someone else accidentally enabled guest session or something. Seems like a noob answer, but hey, it's possible.

---

### Post by jerrrys on 2009-06-16
Code:
     finger

in terminal

---

### Post by r3cht3r on 2009-06-16
> **SunnyRabbiera said:**
> As long as you have the modem plugged in and active you run the risk of attracting rouge users wanting to leech off of you.
It happens on all OS's, even linux isnt 100% bulletproof.
If i were you I would install firestarter, just in case.
Also make sure to keep changing your passwords often.

even if I am not connected to the Internet? 

well, the problem with firestarter is that it flushes out my customized firewall settings.. although grc.com would oftentimes report that I have stealthed ports with firestarter on.

thanks for replying.

---

### Post by lyghtkruz on 2009-06-16
Most likely scenario: 
I agree with prvteprts.  If you see the little running man in the corner with your name (Click on it) there is a "Guest Session" option there.  If you clicked on Guest Session, then yes, you logged in twice.  Multiple people being logged in doesn't mean you are Online or even on a Network.  If you have "multiple" accounts setup, then you could be logged in multiple times.  This can happen if you mean to "lock" your computer and misclicked, it can also happen if you hit a Hotkey that is setup to switch users.  (root, your user and guest are 3 accounts)

Worse case scenario: 
You have a wireless router that you are plugged into.  One of your neighbors is very knowledgeable and can access your wireless router even if you have WEP/WPA setup on the router.  That person would easily get a list of the computers on said network and be able to log in by rooting your box.

Easy solution to figure out which: 
Open the Terminal via Applications -> Accessories -> Terminal. Type who <enter>
You should get a screen like so: 

kruz@Calypso [~] $ who
kruz     tty7         2009-06-16 12:55 (:0)
kruz     pts/0        2009-06-16 13:46 (:0.0)
kruz     pts/1        2009-06-16 14:43 (14x.16x.25x.6x)
kruz@Calypso [~] $ 

This tells you who is logged in and where.  

The tty7 is the X Session I have on :0 
The pts/0 is my Terminal Window that I have open in the X Session
Note the 3rd entry has a 14x.16x.25x.6x.  That is the ip address I am connecting from at work.  Had someone logged into your system remotely, you would be able to see their ip located there.  More than likely a 192.168.1.x address. (Please note the X's were numbers.. i put x's to protect my work IP address)

Hope this helps a little. 
-Kruz

---

