---
title: "Problem Printing to Networked HP Printer (WinXP Hosted).  Starts and Then Hangs."
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by SendDerek on 2007-03-06
Printing from my Ubuntu box to my HP 1210 Printer hosted on my WinXP box, the print job starts (the printer physically starts to move) and then it just sits there and hangs.

A while ago, I was able to print just fine.  I think it had something to do with updates to the CUPS drivers.  It suddenly stopped working and it hasn't worked for a while.  I just now got fed up with it and I am looking for answers.  

I've had this same problem before, but it was easily remedied by placing a check next to "Enable Bidirectional Support" under the "Ports" tab in the printer properties.  That worked for a while, now I'm back in the same boat as before even with the bidirectional support enabled.

Basically, here's what I see in the print queue when printing a spreadsheet:

{Document Name} Remote Downlevel Document
{Status} Printing
{Owner} Guest
{Pages} N/A
{Size} 64.0KB/5.51MB
{Port} USB001

I then have to delete the job from the queue and then turn off the power to the printer and then back on again before I can try and print anything to it again.

The printer works perfectly when it is directly connected to my Ubuntu box.  Any help would be greatly appreciated!

Thanks,
Derek

---

### Post by SendDerek on 2007-03-06
I know it's only been 6 hours, but uh...

Bump?

---

### Post by SendDerek on 2007-03-07
Is there a solution in the house? lol ;)

---

### Post by SendDerek on 2007-03-08
:)

---

### Post by SendDerek on 2007-03-09
JAB...






(Just Another Bump) ;)

---

### Post by SendDerek on 2007-03-10
Okay, so there has been *maybe* a little more light shed on the situation...

I was goofing around and found the CUPS admin panel ([http://localhost:631](http://localhost:631)) and decided to see what would happen if I tried to print from there.  Immediatly following my print submission, I got this error message for a few seconds, and then it went away:
> 
Can not get the ticket cache for <username>


I've googled, but I havn't found anything yet.  Does anybody know what this might mean?

---

### Post by SendDerek on 2007-03-13
Hello Again!

I would really like to get this printer issue resolved as school is starting up pretty soon (a few weeks) and I'm sure that I'll need it!  :)

Is there anybody here that might be able to help me out on this one?

---

### Post by SendDerek on 2007-03-15
Any clue or tip would be much appreciated...

---

### Post by SendDerek on 2007-03-23
Where would I go to maybe help me find an answer to this?  Do I need to be posting on a different forum maybe more specialized in this issue?

---

### Post by tengil on 2007-04-02
I have the same smb printing problem. Here's what I get in the log:

E [02/Apr/2007:09:16:01 +0200] [Job 350] Session setup failed: NT_STATUS_LOGON_FAILURE
E [02/Apr/2007:09:16:01 +0200] [Job 350] No ticket cache found for userid=1000
E [02/Apr/2007:09:16:01 +0200] [Job 350] Can not get the ticket cache for kurt
E [02/Apr/2007:09:16:01 +0200] [Job 350] Session setup failed: NT_STATUS_LOGON_FAILURE
E [02/Apr/2007:09:16:01 +0200] [Job 350] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [02/Apr/2007:09:16:01 +0200] [Job 350] Unable to connect to CIFS host, will retry in 60 seconds...

Grateful for any help.

---

### Post by SendDerek on 2007-04-22
So, I have updated to Fiesty and I still have the same problem.  I was hoping that something would've changed in the process.

I feel like I have tried just about everything.  Any help would be highly appreciated!

---

