---
title: "Noob problem:  Evolution POP -ERR Login Failure"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Popeye.Tom on 2010-08-10
Hi all,

I'm new to Ubuntu and Linux.  I've just installed 10.04 on a rebuilt box for a friend (my idea  ;))  I'm posting this here 'cause I'm an Absolute Beginner.  If there's a more appropriate topic - I can move this!

Except for the addition of WINE, the installation of 10.04 is stock.

Searching the forums here came up with a similar posting by user "Truemedia" but no resolution in this thread.

I took the settings from the user's Outlook Express on his XP laptop. Secure Password Authentication has not been set there for POP3 or SMTP.  POP3 in, SMTP out.  I've duplicated server name, user name, & password from Outlook Express into Evolution.  After going through the Evolution 'wizard' I then push the Send/Receive button and get:

  [COLOR=Blue]Unable to connect to POP server ######
  Error sending password:  -ERR Login Failed
[/COLOR] 
I had some concern that the user didn't remember the correct password and so I got a password discovery program (ShowPW) to verify the password in Outlook Express and that is correct.  It is correct as I've entered it in Evolution when trying to Send/Receive.

I did use the "Check for Supported Types" in the Evolution setup wizard and Evolution did pop up "Querying Server for list of supported authentication mechanisms" and for both the Outgoing and Incoming tabs in editing this mail definition, non supported types were crossed out.  So, I am assuming that Evolution was able to communicate with the email server.  For POP the only supported type is Password.  For SMTP both Plain and Login are supported & I have tried both with no success.

I have also varied Network Preferences in Evolution Preferences and tried both options:
    * Use System defaults
and
    * Direct connection to the internet  

No difference.

There is no firewall on the router, I currently have it turned off.  The settings for Evolution appear to be identical to Outlook Express on XP 32.  The internet connection is through an Actiontec DSL modem/router.

Firefox in 10.04 seems fine, loads web sites and streams music OK, even got his Slacker radio to work.  Ubuntu updates after installation ran as well as a few new ones today, all worked fine.

It almost seems like there is a firewall problem.  Firewall is *turned off on the router*  Could it be an Ubuntu Firewall issue?  (Searching the forums for "firewall" did not turn up anything that appeared immediately appropriate to me.)

Suggestions?  Thoughts?  Experiments?  I really want to make Ubuntu work on this system!  (Should I forget Evolution and try Thunderbird or something else?)

Thank you,
Tom

---

### Post by wojox on 2010-08-10
What mail server are you trying to connect to?

---

### Post by Popeye.Tom on 2010-08-10
I have opened a terminal shell and did a ping on the server by name.  No failed replies.  Average 107.334ms

---

### Post by Popeye.Tom on 2010-08-10
> **wojox said:**
> What mail server are you trying to connect to?

It is the email server for my friends hosted domain.  The URL for his domain is riderschoicebikes.com

The POP3 and SMTP server are the same name:   mx.riderschoicebikes.com

I have been successful in pinging the server, by name, from both my WinXP box as well as this Ubuntu 10.04 x32.  The average responce time on Ubuntu is 107.334ms.

---

### Post by wojox on 2010-08-11
I'd talk to your friend who's hosting and try and figure it out. It sounds like an email client problem and not so much Ubuntu or your firewall.

---

### Post by mastablasta on 2010-08-11
it could be (just guessing) that you have to define a port in Evolution next to your email service provider. 
 
for example:
 
pop3.example.com:26
 
i think this is not necessary in Outlook.

---

### Post by Popeye.Tom on 2010-08-16
> **wojox said:**
> ...snip... It sounds like an email client problem and not so much Ubuntu or your firewall.

You were right, Wojox...in a fashion!  I was able to resolve it with the help of the guy that is hosting.

The problem, I'm embarrassed to admit was the font used both on the printout of the passwords, but also in the server configuration tab of Outlook Express, where I copied the server information from.

It was a font, unlike this one, that *did not* put the bars on the top and bottom of the upper case I.  So I had entered the password using a lower case "L" rather than "I"

As soon as that was done, Evolution was just fine & I am very red in the face!

Thank you Mastablasta and Wojox for taking the time to read and make suggestions!

Cheers,
Tom

---

