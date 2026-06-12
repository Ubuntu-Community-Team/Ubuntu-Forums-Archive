---
title: "New User on Gutsy w/ WUSB54GSC"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by mLes-_- on 2007-12-19
Okay,  first off I am a brand new user to Linux, but an advanced Windows user so I am not an idiot.  Although, networking is my stronger side of computers, you can probably understand why im completely frustrated about not being able to make this work.  I have basically installed a new HDD today and partitioned it to dual boot both Linux Ubuntu 7.10 and Windows XP Pro.  I finished all the installations, and the only thing I lack is to make my Linksys WUSB54GSC adapter work!!!  Everything else works great.  The only reason I am interested in using Linux is to become more than familiar with this for school and work.  I have tried multiple tutorials and instuctional posts on how to do it, but I can not make it work.  All the terminal does is give me error after error.  Any help will be greatly appreciated.  Thanks.

---

### Post by Skidpad on 2007-12-19
Can you post the output of "lsusb" - that's a lower-case "L".  This will show us what chipset is in your usb adapter.

---

### Post by mLes-_- on 2007-12-20
Sure... I typed "lsusb" in Terminal and this was the output:

Bus   004   Device   005:   ID   13b1:0026   Linksys
Bus   004   Device   001:   ID   0000:0000
Bus   003   Device   001:   ID   0000:0000
Bus   002   Device   004:   ID   0bc7:0005   X10 Wireless Technology, Inc.
Bus   002   Device   001:   ID   0000:0000
Bus   001   Device   005:   ID   03f0:7304   HP DJ 35xx
Bus   001   Device   004:   ID   046d:C041  Logitech, Inc.
Bus   001   Device   001:   ID   0000:0000

I hope thats it b/c i had to type all that rofl...
Also, I want to add that i did not have wired Ethernet support dring the Live CD isntallation.  Therefore, I recieved an error message about updates not being accessible.  Is this a problem?  If so where and how can I get them w/o a working network connection.

---

### Post by mLes-_- on 2007-12-20
UPDATE:!:!:!

I got the wirless adapter to work finally... However once again there is a problem.  It picks up the network and asks for the key.  I enter in all the info correctly, bt it just keeps timing out.  Is there a network monitor available for linux so that i can look at the packets being sent and recieved to find out where the problem is?????????

---

### Post by mLes-_- on 2007-12-20
okay this is getting REALLY STUPID.  Anyway, I thought I found a fix that has to do with modifying my /ect/network/interfaces FILE.  

BUT GUESS WHAT?!?! 

It says I dont have the permissions to modify it.  So I used my knowledge of Users and Groups from Windows and added my account to the root group.  This didnt work.  Is there like a SAFE MODE or how can i log in as the "root" user to modify this file.

P.S.  the sooner I get an answer the quicker ill shut up b/c all my problems will be solved and I'll be able to go to sleep (which I havent done in almost 2 days b/c I cant figure this out).

---

### Post by Vadi on 2008-01-01
Where are you at atm?

---

