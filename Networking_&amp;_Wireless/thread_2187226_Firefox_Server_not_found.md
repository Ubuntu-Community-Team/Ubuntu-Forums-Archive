---
title: "Firefox Server not found"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by Cyber72 on 2013-11-11
When I try to open Firefox i get Server not found.
It is not my home hub as my windows desktop is connecting OK with Firefox
I don't have another browser on my Ubuntu laptop.
The problem first occurred a few days ago. I had some updates to install. I clicked to install them and they required downloading some files from the internet. This went Ok and while the updater was connected to the internet I managed to get Firefix to connect. But yesterday I shutdown my laptop and afeter starting it today it just gives the message server not found.

---

### Post by Cyber72 on 2013-11-11
I have gone to the ubuntu software and clicked on installed software.
I found  Empathy Internet Messaging and launched it from Dash but it won't connect either (I haven't used Empathy Internet messaging before but I thiught it might be able to connect me to the Internet)

---

### Post by houstonbofh on 2013-11-11
Bring up a terminal. (ctl-alt-t)  And report the answers to the following.  This will give us a quick look at where things are failing...  You will need to manually exit ping, but the rest will exit fine.  You do not need sudo for any of these commands.

ping [www.google.com](www.google.com)
(hit ctl-c to exit after a few lines)
ping 4.2.2.2
(hit ctl-c to exit after a few lines)

ifconfig
route
arp -a

---

### Post by Cyber72 on 2013-11-11
Thanks I tried pinging and it wouldn't work.
I get the popup message "Wired network disconnected you are now offline".
I have put the router in the living room and connected it to my Windows XP desktop this connects OK and if I then connect my Ubuntu laptop the lap top will connect to the internet but when the desktop is not connected to the router the laptop won't connect.

---

### Post by houstonbofh on 2013-11-12
You have a physical connectivity problem.  I would try a new router, or some new cables.

---

### Post by Cyber72 on 2013-12-12
Update:
The problem seemed to have resolved itself. Occasional "server not found" problems were resolved by resetting the router.
Today I had an update for Firefox that required restarting the linux laptop. Since then it won't connect and won't ping.
 I have 3 cables for connecting the router to a computer, I have tried them all but still can't connect to the internet, all three work OK on my Windows desk top. The fact that resetting the router worked when I couldn't connect suggests that it was not the cables.

---

### Post by pascalfares on 2013-12-13
what is the result of ifconfig, when you have thjis problem?

---

### Post by Cyber72 on 2013-12-13
solved by
sudo modprobe b43

---

