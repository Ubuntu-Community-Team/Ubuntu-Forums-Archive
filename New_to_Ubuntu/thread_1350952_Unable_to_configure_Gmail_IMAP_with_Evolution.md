---
title: "Unable to configure Gmail IMAP with Evolution"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Xnux on 2009-12-09
I am attempting to set up my Gmail account with Evolution's IMAP settings, but I cannot get Evolution to work for some reason. I feel like I am missing something obvious, because I have tried all of the following:


[LIST]
[*]Enabled IMAP settings on mail.google.com
[*]Have set up my Evolution account settings according to [this previous forum post]("http://ubuntuforums.org/showthread.php?t=641590")
[*]Specified the port 993 for IMAP and 587 (or 465) for SMTP
[*]Entered my Gmail password when prompted
[/LIST]
The strange thing is that when I entered my password, the status bar at the bottom appeared to be syncing my Gmail folders... yet nothing new showed up on my side bar, just the default folders. Any suggestions?

---

### Post by ramjet_1953 on 2009-12-09
This link should help you:

[http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml](http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml)

Regards,
Roger :D

---

### Post by musarraf172 on 2009-12-10
> **Xnux said:**
> I am attempting to set up my Gmail account with Evolution's IMAP settings, but I cannot get Evolution to work for some reason. I feel like I am missing something obvious, because I have tried all of the following:


[LIST]
[*]Enabled IMAP settings on mail.google.com
[*]Have set up my Evolution account settings according to [this previous forum post]("http://ubuntuforums.org/showthread.php?t=641590")
[*]Specified the port 993 for IMAP and 587 (or 465) for SMTP
[*]Entered my Gmail password when prompted
[/LIST]
The strange thing is that when I entered my password, the status bar at the bottom appeared to be syncing my Gmail folders... yet nothing new showed up on my side bar, just the default folders. Any suggestions?



Why dont you use POP3 ? I am using gmail pop3 with evolution without any issue.

---

### Post by Xnux on 2009-12-10
I hate POP3. I use several computers throughout the day, and several email addresses as well. When I use POP3, I can only download a copy of each email once before it is deleted from the server--therefore, I am unable to access that email on other computers using the same POP3 address. IMAP is awesome because it automatically detects what emails you don't have and syncs them.

I would just use the Gmail web site, but these days Google seems intent on leaving anybody who is not using Chrome behind. :(

---

### Post by Xnux on 2009-12-10
> **ramjet_1953 said:**
> This link should help you:

[http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml](http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml)

Regards,
Roger :D
I have set up everything according to these exact specifications, even though mine were pretty similar (I hadn't clicked on "Remember password"). It still is not working.

I can't shake the feeling that Evolution has already synced my information (I distinctly recall the status bar loading my Gmail folders), but that I have somehow not enabled an option that will show my Gmail folders in the side bar.

---

### Post by putu.sundika on 2009-12-10
> **Xnux said:**
> 
I would just use the Gmail web site, but these days Google seems intent on leaving anybody who is not using Chrome behind. :(

really ? then i must have chrome on my ubuntu.

sorry can't help you with an answer, but i really want to ask you this : is your Evolution Sent Folder work ? my Sent Folder totally blank. Now i switch to Thundirbird for my GMAIL account. Everthing works fine then. What version of your evo ? If your Sent Folder is working, did you setup something?

---

### Post by joes7 on 2009-12-10
Use Thunderbird.

---

### Post by Xnux on 2009-12-11
> **putu.sundika said:**
> really ? then i must have chrome on my ubuntu.

sorry can't help you with an answer, but i really want to ask you this : is your Evolution Sent Folder work ? my Sent Folder totally blank. Now i switch to Thundirbird for my GMAIL account. Everthing works fine then. What version of your evo ? If your Sent Folder is working, did you setup something?
My Sent folder is blank too. However, one time when I clicked Send/Receive, it appeared to be syncing. Nothing followed, though. :(

I have been using Thunderbird, but I find it to be a mediocre program at best. It is extremely slow at loading Gmail messages, plus its Google Calendar support is just awful. I want to see if Evolution can handle it better.

---

### Post by stigb on 2009-12-13
Bump! I have the same problem. I have also compared my settings to the weakish tutorial, and it appears that everything is set up correctly. I can send messages over my gmail, but I can't receive them.
I tried running Evolution from the terminal, and this is my output. (My email adress replaced by [email]example@gmail.com[/email]) I ran the program, tried to receive new messages and then closed Evolution again. Nb: I also have a functioning hotmail account configured in Evolution.
```
stig@stig-laptop:~$ evolution
** (evolution:24657): DEBUG: mailto URL command: evolution %s
** (evolution:24657): DEBUG: mailto URL program: evolution

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:24657): DEBUG: New Indicator: Innboks pop:
** (evolution:24657): DEBUG: New Inbox inidicator
** (evolution:24657): DEBUG: New Indicator: example imap://example%40gmail.com@imap.gmail.com:993/
** (evolution:24657): DEBUG: New account: example (imap://example%40gmail.com@imap.gmail.com:993/)
** (evolution:24657): DEBUG: Number of email accounts: 2
** (evolution:24657): DEBUG: EI: SHELL STARTUP

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:24657): DEBUG: EI: mail_read_notify
** (evolution:24657): DEBUG: Setting Innboks to 0 unread messages
** (evolution:24657): DEBUG: Setting example to 0 unread messages

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:24657): DEBUG: New Indicator: example imap://example%40gmail.com@imap.gmail.com:993/
** (evolution:24657): DEBUG: New account: example (imap://example%40gmail.com@imap.gmail.com:993/)
** (evolution:24657): DEBUG: Number of email accounts: 2

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:24657): DEBUG: New Indicator: example imap://example%40gmail.com@imap.gmail.com:993/
** (evolution:24657): DEBUG: New account: example (imap://example%40gmail.com@imap.gmail.com:993/)
** (evolution:24657): DEBUG: Number of email accounts: 2

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:24657): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:24657): DEBUG: New Indicator: example imap://example%40gmail.com@imap.gmail.com:993/
** (evolution:24657): DEBUG: New account: example (imap://example%40gmail.com@imap.gmail.com:993/)
** (evolution:24657): DEBUG: Number of email accounts: 2
stig@stig-laptop:~$ 

```
And just for the sake of correctness: The word 'example' is not present in the output anywhere but where I have replaced it.

---

### Post by stigb on 2009-12-13
All right, just never mind. I found that the inbox for Gmail had its own category in the side panel. Everything works just fine. Might this be the solution for the OP as well? :P

---

### Post by woodnymph on 2009-12-13
i have it in pop3 no problem - and also use thunderbird ..

---

