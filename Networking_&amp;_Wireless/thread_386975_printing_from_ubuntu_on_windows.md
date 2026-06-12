---
title: "printing from ubuntu on windows"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by cr4z3d on 2007-03-17
I've got a printer hooked up on one of my windows computers on the network and was able to find it no problem through printer settings in ubuntu edgy. The driver i choose was the recommended one for the HP PSC-1410. (HPIJS)

I try printing  a test page and in the print status on Ubuntu it says printing then goes away after about a minute as if it printed successfully. Then I walk into the room with the printer and I hear it move back a few times but nothing happens. Then I went to see what the print status said on the XP machine. It was at printing and not doing anything. So I waited a couple minutes to see if anything happened but nothing ever did. So just to make sure it wasn't the printer I got on my vista machine and printed out to the same printer without any problems. Am I forgetting to do something? The printer says ready right under it in the printers settings. 

Any help would be appriciated.
Thanks in advanced, 

cr4z3d

---

### Post by scrooge_74 on 2007-03-17
Try hooking the printer directly to your Ubuntu box and see what happens, that way you can rule out if there is any incompatibilities between Vista and Linux

---

### Post by cr4z3d on 2007-03-17
Sorry if I was unclear, the printer itself is hooked up to an XP home computer (my roommates) and the Vista machine is my laptop that I used to check if I could print in general over the network. So there shouldn't be any need to check for vista/linux incompatibility. Right now i'm in the process of trying out the HPLIP drivers to see if that helps at all. I did read somewhere that HPIJS are included in the HPLIP drivers but I'm going to go ahead and see if that helps

---

### Post by scrooge_74 on 2007-03-17
Any way try hooking the printer directly and see if the driver is working as it should.  Which printer model is?

---

### Post by cr4z3d on 2007-03-17
Wow now I have something really weird going on. Every 30 seconds or so another print job is added. Not sure why that is happening so I'm going to try restarting Ubuntu

EDIT: Thanks for fast responses, and it's a HP PSC-1410

---

### Post by scrooge_74 on 2007-03-17
Check Cups to delete print jobs either from the printer config or from the webpage manager, open your browser and type localhost:631/

---

### Post by cr4z3d on 2007-03-17
Ok, So I tried hooking it up directly to the computer and that printed out fine for the test page. Looks like there's something going wrong on the XP machine i guess?

---

### Post by cr4z3d on 2007-03-17
I've hooked it back up to the Xp machine and added the printer after deleting all the other ones, made sure I selected the same driver I had from before and for the login information I put in Alex (admin account on XP) with no password (since there's no password on the machine) and the print queue still just says Remote Downlevel Document with status of Printing and Owner is Guest. It just sits there doing nothing. 

On a side note, how do I get rid of print jobs from XP? I hit delete and it just freezes there and does nothing until i restart the computer. (Only seems to do this when the printjob comes from ubuntu)

---

### Post by scrooge_74 on 2007-03-17
I can only recommend you to read about CUPS at [http://www.cups.org](http://www.cups.org)

I dont have any XPs computers any more (thank the gods for that), only ubuntu machines at home, so I can't give you any more pointers.

sorry

---

### Post by cr4z3d on 2007-03-18
Damn.. Alright , well thanks man hopefully I can get this working it's the only thing I haven't been able to do so far using Ubuntu.

---

