---
title: "Networking between Ubuntu Hardy Heron and Windows Vista"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Shadow-Sleeper on 2008-08-16
Hello All

Here, i am again. Maybe it is a silly question.
How can i get my files on Ubuntu from my windows vista laptop?
I really dont wanna transfer everything with my tumb drive.

Both the computers are connecting to my wireless network. From my laptop (vista) i can see my friends laptop, (also vista) but i just cant see my ubuntu desktop!! i must be doing something wrong!

Please help.
Thanks in advance!

---

### Post by Naatan on 2008-08-16
I find it easier to connect to my windows computer with Ubuntu than the other way around.. samba shares are a hassle unless you know what your doing.

Simply open Nautilus and enter the ip address of your windows machine with the smb handles in front of it.. like so

smb://192.168.0.100

Make sure you have a folder shared on your Windows machine.

Sometimes it doesn't display the shares, you can connect to a specific share directly like so:

smb://192.168.0.100/sharename

hope that helps, goodluck

---

