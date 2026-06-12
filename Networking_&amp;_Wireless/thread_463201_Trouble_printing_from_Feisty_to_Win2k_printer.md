---
title: "Trouble printing from Feisty to Win2k printer"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by timzak on 2007-06-03
I've gone through the network printing tutorials in the Documentation Pages here and have searched the forums but can't figure this one out.  I have a local network shared between two computers on a router.  The Win2k computer has a printer attached (HP Photosmart C3100) via USB.  Also, the Win2k printer logs into Administrator without username/password.  Here is the procedure I used in Feisty:

System->Admin->Printing

Enable "Detect LAN Printers"

Add Printer->Network Printer->Windows Printer (SMB)

An "Authentication Required" window pops up asking for Identy and Password for the Windows Workgroup.  Since there is none, I leave the Username and Password fields blank and hit Connect.

I click on the down arrow to the right of the Host line, and select the computer name that correctly pops up (the Win2k computer with the printer).  Another Authentication Required window pops up asking for Identity and Password of the computer in question.  Again, I blank out both fields and hit Connect.

Then I click on the down arrow to the right of the Printer line and the printer name correctly displays.  I select it.  It's called HPPhotos.

I leave Username and Password fields blank and hit the Forward button at the bottom right corner.
 
Then I select the Manufacturer (HP) and Model (PhotoSmart C3100), leave the default driver (hpijs) and click Forward in the lower right corner.

Now I'm on the Step 3 of 3 page.  The printer name is there (PhotoSmart-C3100) and I leave Description and Location fields blank and hit Apply.

Now I have a PhotoSmart-C3100 Ready icon in my Printers.  

I try to print a test page.  It tells me a test page has been sent to PhotoSmar-C3100.  A printer icon shows up in my tray that says "Printing".  But nothing ever prints.  After awhile, it tells me the job is paused, but that's as far as it ever gets.

Can anyone help me?  I have no interest in sharing my Feisty computer with the Win2k computer in any other way.  I just want to be able to use its printer.

I also understand that I can only print while the Win2k computer and printer are powered on.

From my Feisty computer, I have a Win2k partition that I dual boot into and from there (Win2k to Win2k) I can print across the network to the other Win2k computer.

Help?  The fact that it is finding and installing the printer driver over the network shows that it is connecting through the network okay, so I don't understand why it won't go the final step to actually printing.

Thanks.

---

### Post by timzak on 2007-06-04
Can anyone help?  It seems like it should be working.  I can see the Win2k computer on the network and even see the printer.  Just when I send a print job it never gets to the printer.

Thanks.

---

### Post by timzak on 2007-06-04
Can someone at least look over my procedure in the first post and tell me if I did anything wrong?  

Thanks :p

---

### Post by lexdave on 2007-06-04
I had the same thing at my home network but with Win XP hosting an HP Deskjet 3115.  I went through the same process, but when it asked for username/password I entered the admin account name with password thinking it needed that.  I got the document to load into the windows print spooler and the printer made its normal pre-printing noise (print heads moving about) but the printer never feed the first page.  Looked at the print spooler the dovument was there, but it timed out after awhile of waiting.  Then I couldn't delete the document from the spooler (had to manually shut it down and delete the file).  I tried multiple documents but all failed in the same fashion.

In the end I gave up and just got a printer for my Ubuntu machines to share (3 Ubuntu's :p)

Sorry about that, would love to see if you can get this working.  Heck you can even e-mail/IM me if you want to give it another try.  Maybe something with Samba can help, or even wine.  LOL, I'm such a newb to this Linux stuff (2 months) just switched 3 of my 5 to Ubuntu jut to learn.

---

### Post by timzak on 2007-06-04
Thank you for the reply.  Even if you couldn't solve my problem, I'm glad you were able to commiserate.  Here's what I don't get:  all this I'm trying on my home network.  At work, I tried the same thing with a backup computer using Feisty, hooked into my 3 computer network in the office and I was able to print from Feisty to a WinXP printer!  I used the exact same procedures.  The only differences are that:
1) at home (what's not working) my Windows machines are Win2k SP4 while at work, they are WinXP
2) the printer models are different (I think at work they are HP OfficeJet 5750)
3) at home I use cable modem with D-Link router while at work I use DSL with Linksys router.

I can't figure out why it works at work but not at home.  Anyone else have any ideas?

---

### Post by lexdave on 2007-06-05
I blame it on the printer model theory.  Maybe only some work and others don't.

I'm going to try later tonight with me new printer and see if I get better results that way.

I don't think win2k would have anything to do with it - it was the same as XP in almost every way.
I'll post back later with some results.

---

