---
title: "3 Computers (differing OS's), One Printer Connected Through a Switch"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by Billsey on 2006-10-12
I have a Mac 9600 running OS9, a Mac running OSX (10.3.9), a PC running Ubuntu 6.06 LTS, and a Samsung CLP-550N networked together through a switch. My problem is that the Ubuntu box doesn't seem to want to play well with others, so to speak (I've obviously boxed up some settings somewhere). The Macs can see each and access other and can both use the printer, while the Ubuntu Box can see the printer, but not use it (although it can access and manipulate the printer through the printer's built-in web site) and cannot see the two Macs; and the Macs cannot see the Ubuntu Box.

Are there any networking geeks here that can give me a clue on this? :D

---

### Post by Billsey on 2006-10-12
OK, small, but probably important update:

I posted the earlier message from work, more than 30 miles away from my home network. I am now back at home. I pinged the Ubuntu Box from the OSX box. ***SUCCESS!!!*** It pings fine, most pings being less than a millisecond. Next I did a port scan. ZERO, Zip, Zilch, NADA! So, the question now becomes opening the appropriate ports on the Ubuntu box. :rolleyes: 

I'll check back with you later. I've got some reading to do. :-k

---

### Post by Billsey on 2006-10-13
After reading, trying, and sleeping, I am back. As far as I can determine without help, Ubuntu only prints via network over port 631. My printer requires port 515. So far, I have not found any way of modifying either one to match the other. It strikes me that since Ubuntu is software and printer is hardware, it might be easier to change the port that Ubuntu uses to print over a network. I only need to know how to do that. Any help is appreciated. ;)

---

### Post by Iowan on 2006-10-13
When I set up my HP5M via JetDirect, I was given a port option.  Dunno if that's missing in the "ordinary" network setup option.

---

### Post by Billsey on 2006-10-13
I do know that I have to actively open the ports needed, but I don't know, (a) how to do that; (b) how to get a particular service to a particular non-standard port, like my printer using 515 instead of 631; or (c) why, even though my OSX Mac has both ports open, and my Ubuntu Box can see all of the printers for which my OSX Mac has drivers (even if the actual printer no longer exists :D ) but can't print to any of those printers.

Once I have that problem licked, I hope to move on to actual file exchange, puter to puter; then to accessing the Internet through the machine that is actually connected to the Internet. I've got some fun ahead, don't I? :D

---

### Post by Billsey on 2006-10-17
Well, I now have things to the point that the Ubuntu Box can see the MacOSX Box and even log into it, but it still can't seem to read anything from it or write anything to it. Still, that is progress. :)

---

