---
title: "Mail virus - ubuntu 10.04"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by ve1drg on 2010-05-17
I have recently set up ubuntu; upgrading up to the latest 10.04.  I have done this on my laptop and so I run either ubuntu or windows (vista) depending on my interest.
 
Something I have found over the last few days is a bunch of returned mail by my mail subscriber - that I am trying to send out dirty mail to various people that are not on my mailing list. At  least I think they are not on my mailing list.
 
My question is;   is Ubuntu susceptile to mail  viruses.  I mean to sending out virus mail?   I personally have never heard of linux having such a problem but perhaps someone could help me out here.  Is Linux (ubuntu) capable of passing out virus mail?
And if so how can I stop this?   It is my Gmail account that is doing this,  in case this helps..

---

### Post by hashimoto on 2010-05-17
> **ve1drg said:**
> It is my Gmail account that is doing this,  in case this helps..

Maybe your gmail account has been compromized. Change the password now...

---

### Post by mlentink on 2010-05-17
Most likely there is nothing wrong with your mail-account. But very likely you left your e-mailaddress at some website. It is now being used by spammers as their spoofed 'from'-address.

---

### Post by Grenage on 2010-05-17
> **mlentink said:**
> Most likely there is nothing wrong with your mail-account. But very likely you left your e-mailaddress at some website. It is now being used by spammers as their spoofed 'from'-address.

This is by _far_ the most likely explanation.

> **ve1drg said:**
> My question is;   is Ubuntu susceptile to mail  viruses.

Not really, no.

---

### Post by lisati on 2010-05-17
> **mlentink said:**
> Most likely there is nothing wrong with your mail-account. But very likely you left your e-mailaddress at some website. It is now being used by spammers as their spoofed 'from'-address.

> **Grenage said:**
> This is by _far_ the most likely explanation.

I've had the exact same thing happen for the exact same reason.

---

### Post by oldsoundguy on 2010-05-17
It could also be a re-mailer virus .. they abound in the Windows world.
Here is an explanation that I have on my Windows service site:

An explanation about a remailer worm/virus. 

Someone you know has a virus on their computer .. how they got it is immaterial, but they have it. 

That virus/worm is a remailer. 

On their computer is an address book (usually associated with Outlook or Outlook Express.) 

The nasty goes into that address book and randomly selects an address to "spoof" as an originator and proceeds to replicate itself and send itself to every other address in that aforementioned address book. 

If YOUR address was selected as the spoofed originator, then all others in that book will get an eMail supposedly from YOU that contains that virus/worm. 

SOME (not enough by any means) ISP's and E-Mail services actually spot that virus with a software program. 

IF it is an "ON TOP OF IT" ISP, it will detect not only the virus, but the fact that the sender (your) address has been "spoofed" and that ISP will just kill the mail. 

If it is a Mickey Mouse ISP with just the bare requirements of catching nasty mail, it will return the mail to YOU as it thinks you sent same! 

(Of course that is better than an ISP that MISSES that mail and lets it get through to infect some one else.) As long as the original infected machine is NOT cleaned out or has NOT crashed, you will continue to get those "returned" emails.

There is absolutely NOTHING you can do about it, as the ISP that is "bouncing" that eMail is doing so with a "daemon" .. an automatic program. Returning that eMail and complaining about it goes NOWHERE as there is no live body at the return address of the daemon at that ISP! 

The ONLY way to stop that crud is to keep your Internet Explorer/Outlook whatever updated with all the critical updates, and keep your AntiVirus updated every day ... 

OR ........ change to Firefox/Thunderbird, or almost any other browser/mail program.

---

### Post by Gone fishing on 2010-05-17
I agree the most likely things are:

Your address is being spoofed by a spammer.
Your address is being spoofed by a Windows box infected by a mass mailer virus.

It may be possible to find out which by examining the full headers of one of the emails.

---

