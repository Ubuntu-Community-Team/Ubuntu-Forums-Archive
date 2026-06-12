---
title: "Cannot access files/folders and cursor always busy."
date: 2010-09-20
forum: New to Ubuntu
---

### Post by DerekA on 2010-09-20
First of all, hello! I'm a first time ubuntu user (netbook remix) and this is my first post on these forums.

I've come across a problem that I have no idea how to solve (despite much googling) and am feeling a bit overwhelmed. 

Here are the symptoms: 
The mouse cursor is always "busy", except in Firefox, although it performs as normal.
The hard drive appears to be working a lot harder than usual, making a bit of noise (90% sure this is new although I suppose I could be fooling myself).
I cannot access any of my files or folders. When I click on one it says it's loading but nothing happens. Programs such as Firefox and Empathy work as normal. I opened up the file browser from the terminal but it tells me my desktop has 0 items.

Any help is much appreciated!

---

### Post by sikander3786 on 2010-09-20
Fist of all make sure your laptop is not heating up. It is a usual cause of slow performance. Are you sure the sound is from the HDD, it might be the fans spinning hard.

Secondly type **top** in a terminal and see how much processor, RAM etc are being used. Which processes are running and search for any processes you don't expect to be there.

---

### Post by DerekA on 2010-09-20
You may be right about the fans, although it doesn't happen when I boot as Windows 7.

I tried looking at the running processes before but nothing seemed too abnormal to my amateur eyes. The top CPU processes were dbus-daemon (13%), Xorg (5%), and Swiftfox (6%). The only thing using a significant amount of ram is Swiftfox.

---

