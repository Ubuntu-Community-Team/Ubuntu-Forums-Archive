---
title: "Help with mail"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by max00355 on 2010-11-22
i am using the mail program on ubuntu 10.04 but it keeps asking for my IMAP.gmail.com password and i dont know what it is what do i do

---

### Post by yankysunny on 2010-11-22
What type of mail program r u using?
Try to put ur email password

---

### Post by max00355 on 2010-11-22
im using gmail and i tried that already

---

### Post by Vi3GameHkr on 2010-11-22
If you check out the help section of GMail, and search "imap" the first result is [Getting started with IMAP for Gmail]("http://mail.google.com/support/bin/answer.py?hl=en&answer=75725") which has a nice introduction to IMAP and POP mail, as well as instructions to enabling them from GMail and configuring your email program.

Also, it would be helpful if you stated which email client you are using, although I would assume that by "mail program on ubuntu 10.04" you mean "Evolution Mail."  In that case, [this article]("http://mail.google.com/support/bin/answer.py?answer=78799") would be most useful to you, as long as you make sure you enable IMAP from your GMail settings.

Hope this helps you :)

EDIT: Also, when yankysunny asked what email program you used, I believe he meant which application in Ubuntu since you already implied that you are using GMail.  Again, I would assume you mean Evolution Mail (Under Applications > Internet)

---

### Post by spikoley on 2010-11-22
Maybe it is the user name causing the problem.  Make sure you are using the full email address like [email]me@gmail.com[/email].

Also, make sure you have IMAP enabled within your Gmail account.

---

### Post by max00355 on 2010-11-22
IMAP is enabled and i am using mail evolution the problem im having is that i cant see the mail i receve and i dont know what to do

---

### Post by yankysunny on 2010-11-22
Have you gone through the steps as told by [Vi3GameHkr]("http://ubuntuforums.org/member.php?u=935749")?

---

### Post by max00355 on 2010-11-22
umm ther is nothing by him can someone put met through the steps how you did it

---

### Post by yankysunny on 2010-11-22
[SIZE=-1]**Incoming Mail (IMAP) Server - requires SSL:**[/SIZE] [FONT=Courier New, Courier, mono][SIZE=-1]imap.gmail.com[/SIZE][/FONT][SIZE=-1]
**Use SSL**: Yes
**Port**: 993 [/SIZE]   [SIZE=-1][B]
Outgoing Mail (SMTP) Server - requires TLS:[/B][/SIZE] [FONT=Courier New, Courier, mono][SIZE=-1]smtp.gmail.com[/SIZE][/FONT][SIZE=-1] (use authentication)
**Use Authentication**: Yes
**Use STARTTLS**: Yes (some clients call this SSL)
**Port**: 465 or 587 
[/SIZE]   [SIZE=-1]**Account Name: **[/SIZE] [SIZE=-1]your full email address (including [FONT=Courier New, Courier, mono][SIZE=-1]@gmail.com[/SIZE][/FONT]) Google Apps users, please enter [/SIZE][FONT=Courier New, Courier, mono][SIZE=-1]username@your_domain.com[/SIZE][/FONT]   [SIZE=-1]**Email Address: **[/SIZE] [SIZE=-1]your full Gmail email address ([FONT=Courier New, Courier, mono]username@gmail.com[/FONT]) Google Apps users, please enter [/SIZE][FONT=Courier New, Courier, mono][SIZE=-1]username@your_domain.com[/SIZE][/FONT]   
[SIZE=-1]**Password: **[/SIZE] [SIZE=-1]your Gmail password 


[/SIZE]I think now u can do it

---

### Post by Vi3GameHkr on 2010-11-22
EDIT: For simplicity's sake, try following yankysunny's format.

I posted a link to a help file on GMail's website about setting up IMAP in external mail programs.  Here is a [morespecific tutorial](https://help.ubuntu.com/community/UsingGmailWithEvolution) that deals with working with POP in GMail and Evolution.  

As a side note, I don't know the exact differences between POP and IMAP, but generally I have understood that POP is better.  By searching Google for something like "IMAP vs POP" or something you might be able to find a detailed comparison though.

---

### Post by yankysunny on 2010-11-22
> **Vi3GameHkr said:**
> EDIT: For simplicity's sake, try following yankysunny's format.

I posted a link to a help file on GMail's website about setting up IMAP in external mail programs.  Here is a [morespecific tutorial]("https://help.ubuntu.com/community/UsingGmailWithEvolution") that deals with working with POP in GMail and Evolution.  

As a side note, I don't know the exact differences between POP and IMAP, but generally I have understood that POP is better.  By searching Google for something like "IMAP vs POP" or something you might be able to find a detailed comparison though.
I think IMAP is better though..:D

---

### Post by SeijiSensei on 2010-11-23
> **yankysunny said:**
> I think IMAP is better though..:D

IMAP allows you to keep all your mail, both your inbox and any folders you create, on the mail server.  This has some important advantages.  You will have the same view of your mail no matter which client you choose to use.  Your mail will be backed up and archived by the IMAP provider, Google in this case.  The drawback is that Google can see all your mail.  You should read the Privacy Notice at GoogleMail to see whether you're comfortable with Google's policies.

POP (usually POP3) provides only an inbox.  All the management of your mail after that happens on the client.  If you use the same machine to read your mail all the time, and never use a web interface or any other client, then POP works well.  It also has some semblance of privacy because your mail resides on the provider's servers only as long as the interval you choose to have the client check for new mail.  (Of course, every message can be archived and scanned by your provider before it ever reaches your inbox.  That's why I said POP has a "semblance" of privacy.)  However POP has the distinct drawback that all your mail resides on your local machine(s).  You can mitigate this problem somewhat by choosing the "leave mail on server" option that most POP3 clients offer.  Even using this method, you'll still only see your inbox.  Any stored messages in folders will reside on the client machine.  If you read mail from two different clients, you'll have two disjoint collections of saved mail.

IMAP stands for the "Internet Mail Access Protocol".  POP stands for the "Post Office Protocol".

---

### Post by max00355 on 2010-11-23
thank you it worked now i had to authenticate everything and i had to enable imap on my google account thsank you so much you have been a greagt help

---

