---
title: "help setting up mail through evolution in 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-05-01
Hey every one, just wondering if you could help me to set up evolution to access my hotmail email, and if possible yahoo aswell? I've been using linux for 24 hours so please keep it as simple as possible!

Thanks in advance!

---

### Post by madjr on 2010-05-01
this may help

[http://screencasts.ubuntu.com/Introduction_to_Evolution](http://screencasts.ubuntu.com/Introduction_to_Evolution)

[https://help.ubuntu.com/community/Evolution](https://help.ubuntu.com/community/Evolution)

[https://wiki.ubuntu.com/Evolution](https://wiki.ubuntu.com/Evolution)

---

### Post by Shalefist on 2010-05-14
Hi. I am new to Ubuntu and the Evolution mail system. I have tried the guide [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution) to no avail, and I am not asked for my password despite having both checked the boxes and set the security protocols for it. I also run Firestarter, could that pose any problems? Thank you for your time.

Nevermind. Firestarter was blocking the transmissions. Add the Ports 587 and 995 to both inbound and outbound and it clears right up!

---

### Post by pricetech on 2010-05-20
I found some instructions related to outlook express in hotmail's help section and managed to extract enough information to set it up in evolution.  Here's what I have:

Under the Identity tab, it's all pretty much self explanatory.

Receiving Email tab:
The server type is pop.
The server is pop3.live.com
The username is your email address, not just the username.
Set Security for SSL Encryption and Authentication Type as Password.
Saving the password is optional.

Receiving Options tab:
The Check for new messages..... box should be checked by default.
Leave messages on server should be checked.  Otherwise you'll end up deleting messages you don't want to delete.

Sending Email tab:
Server type is SMTP
Server is smtp.live.com and Server requires authentication should be checked.
Security should be TLS Encryption
Authentication should be Login and, again, use your email address as the username, not just the username portion.  remember password is optional.

Defaults and Security tabs should require no input to make hotmail work.

Good luck with it and let the forum know how it goes.

---

### Post by completeidiot on 2010-06-02
I'm trying to set up email in Evolution for a gmail account that uses my domain. it's not an @gmail.com address. I've done it before, but I can't remember how I did it for the life of me. My @gmail.com address is set up perfectly. Please point me in the right direction. I just upgraded to 10.04 and forgot to back this up.

thanks

---

### Post by Phil Binner on 2010-06-03
Looks like there are lots of people with similar problems to mine. I am trying to get evolution mail set up with gmail and imap. I can send mails fine through my smtp gmail account, but i don't recieve anything from imap. Imap is enabled in gmail. I have unlocked my 'CAPTCHA, whatever that means. I have been through the tutorial linked above, but still nothing arrives.

In their setup instructions Google say you should configure imap on port 993. In Outlook there is a box to do that, but not in Evolution. There is an entry for a Custom Command in the Receiving Options tab. Do I use that to enter the port. Is this a total red herring. 

Help anybody?

---

### Post by WilliamJr on 2011-02-06
Worked fine for me. Thank you.
 
> **pricetech said:**
> I found some instructions related to outlook express in hotmail's help section and managed to extract enough information to set it up in evolution. Here's what I have:
 
Under the Identity tab, it's all pretty much self explanatory.
 
Receiving Email tab:
The server type is pop.
The server is pop3.live.com
The username is your email address, not just the username.
Set Security for SSL Encryption and Authentication Type as Password.
Saving the password is optional.
 
Receiving Options tab:
The Check for new messages..... box should be checked by default.
Leave messages on server should be checked. Otherwise you'll end up deleting messages you don't want to delete.
 
Sending Email tab:
Server type is SMTP
Server is smtp.live.com and Server requires authentication should be checked.
Security should be TLS Encryption
Authentication should be Login and, again, use your email address as the username, not just the username portion. remember password is optional.
 
Defaults and Security tabs should require no input to make hotmail work.
 
Good luck with it and let the forum know how it goes.

---

### Post by CodeRage on 2011-08-22
I found a way to get mine to work very well. I logged into the email account via the browser, which loads up outlook web app. From there I went into [COLOR="Red"]**options [COLOR="Black"]>[/COLOR] about**[/COLOR]. The lines I found that gave me the pop/smtp servers were: ```
External POP Setting:
Server Name:  [COLOR="Red"]**pod51004.outlook.com**[/COLOR]
Port: 995
Encryption Method: [COLOR="Magenta"]**SSL**[/COLOR]
``` 
```
External SMTP Setting:
Server Name:  [COLOR="Red"]**pod51004.outlook.com**[/COLOR]
Port: 587
Encryption Method: [COLOR="DarkOrchid"]**TLS**[/COLOR]
```

My email is actually a college addressed (and custom address) email that operates via hotmail, but this solution should work the same (hopefully) for others using hotmail/live.com. I used the pod51004.outlook.com for both pop and smtp servers in evolution and it worked flawlessly. On first send/receive a bunch of emails came in, and a test email out was successful. 

I would advise following the same investigative steps above where you log in via the web and if it loads up outlook web app, tap into the *options > about* and see if it gives you information pertaining to your pop/imap/smtp servers and use what it tells you it is using. 

Good Luck!

---

