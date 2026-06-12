---
title: "Evolution receives e-mail but won't send"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by SPQQKY on 2007-07-23
I asked this in absolute beginners section, but after 2 and a half hours of bumping and getting really frustrated, no one seems to want to help.
I have set up Evolution properly (proper incoming and outgoing and proper port open). I have no software firewall ATM and I have my router firewall disabled. I have also installed and attempted to use Thunderbird with the same results.....
I can receive email, but I cannot send it. I have set up both of my personal and my work email and configured them properly (same settings work fine in Outlook 2007 in Vista). 
Is there something about ubuntu that is keeping me from sending mail? PLEASE HELP!!! I have been at this ALL DAY!!!

Thank you.

---

### Post by zanglang on 2007-07-24
Don't think Ubuntu would be somehow causing your mails to fail, but it could be that Outlook does some automatic configuring that Evolution is missing... Have you checked if your SMTP settings require TLS/SSL, specific ports or authentication options (Plaintext etc) that you might have missed?

---

### Post by Mr. C. on 2007-07-24
SPQQKY,

Relax a little more - you'll live longer.

You haven't provided very many specific details about the mail server you are trying to use to relay mail and its configuration requirements.  We can guess, but its better if you actually help us avoid this.  You'll find you get faster help the clearer your details are.

Does the mail server require authentication ?

Outlook uses LOGIN authentication; thunderbird and evolution do not support that form of authentication.  If your mail server only supports LOGIN, you will be out of luck.

What is the mail server domain name and port you use ?  I will check to see what it supports.

MrC

---

### Post by gixxerjasen on 2008-02-18
I just came across this thread and I don't know if SPQQKY ever got this fixed but the above help wasn't very helpful.  None of that info was needed.  I actually had the same problem and found some of the answer elsewhere on this forum and figured I'd add in the solution in case someone else comes across this thread via google like I did.

Go into Outlook and look up your server settings.  There should be an advanced tab (maybe, I'm not using 2007 so I don't know for sure) and take note of the outgoing mail server port.  In my case it was 366.

Go into Evolution's Sending Mail tab in your settings and add this after the server name with a colon in between like this

mail.servername.com:366

I put that in and it worked like a champ.  Thanks to Rodneyck in the other thread for the nudge in the right direction.

---

### Post by Mr. C. on 2008-02-18
Port 366 is not a standard SMTP port: port 25 (SMTP) and 587 (submission) are.

Knowing what port the mail provider requires to submit email is important and necessary, otherwise you're shooting in the dark.

MrC

---

