---
title: "execute something on ping"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by AliTabuger7 on 2008-09-10
Here's the WHY:
I have a Windows laptop with iTunes, and I have set up a scheduled task so that iTunes will play music and function as an alarm. However, Windows sucks and sometimes crashes and reboots while I'm sleeping. Since it isn't logged in, it can't play the music.

What I WANT to do:
I would like to add a third line to the Windows scheduled task that would ping or send a packet to my Ubuntu based desktop. 
Then I want to have a scheduled task that runs slightly after the windows one that checks to see if it received the signal from the laptop. If it didn't it should start up rhythmbox.

What I NEED in order to do this:
I'm not sure where to start looking to learn how to send the "no alarm" packet.

---

### Post by pansz on 2008-09-11
I think what you want to do is some socket programming.

You can find them easily in Python examples. type 

    apt-get source python2.5 

in terminal, you can download python source, and the example is in it, you find something named python2.5-2.5.2/Demo/sockets/udpecho.py which is a good example of simple communication between two computers.


Python is a programming language, easy to learn for beginners. It runs both in Windows and Linux, so you can have the client in Windows and Server in Linux.

---

