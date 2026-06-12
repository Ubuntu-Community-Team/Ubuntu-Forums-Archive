---
title: "Thunderbird SMTP Fails with GMail IMAP Account"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by formidable on 2009-03-06
There are a lot of threads and posts on this issue and I've looked through them.  None, however, seem to have a solution.  

I have a GMail IMAP account that I like to access using Thunderbird.  Connecting, downloading, opening, and saving email is no problem.  The problem is that I can't send any mail.  Here's the (infamous) Thunderbird SMTP failure notice: 

[I][B]Sending of message failed. 
The message could not be sent because connecting to SMTP server smtp.gmail.com failed.  The server may be unavailable or is refusing SMTP connections.  Please verify that your SMTP server setting is correct and try again, or else contact your network administrator.[/B][/I]

I'm using Thunderbird 2.0.0.19 on a new Ubuntu 8.1 installation.  I also have Thunderbird 2.0.0.19 on a WinXP machine in the same room.  Thunderbird works fine on the XP machine.  

I have double checked the settings and re-referenced [Google's guidelines on setting up Thunderbird with GMail IMAP]("http://mail.google.com/support/bin/answer.py?hl=en&answer=77662").  The settings seem fine. 

My machines are set up in my lab here at work.  They are both on the same LAN, same subnet. 

My SMTP settings are as follows: 
Port: 587
Server: smtp.gmail.com
Secure Connection: TLS
These settings, along with my user name, have never failed on any machine I've ever set up on until now.  I don't have a firewall running on the problem machine.  

Is there something else going on here?  Where else can I look?

---

### Post by freak42 on 2009-03-06
Hi,

I am also using Thunderbird as a google imap client, I don't have any problems:

My Outgoing Server (SMTP Server) Settings for google are:
Server Name: smtp.gmail.com
Port: 25
checked Use name and password
username: [email]myemail@gmail.com[/email]
use secure connection: tls, if available

I just saw that these differe from what google suggests, however it works well, it might be however that my outgoing mail connections are not encrypted.

hth

---

### Post by Nepherte on 2009-03-06
Your outgoing messages are indeed not encrypted. Try using port 465 (SSL), that's what I'm using. The server is smtp**s**.google.com

---

### Post by freak42 on 2009-03-07
> **Nepherte said:**
> Your outgoing messages are indeed not encrypted. Try using port 465 (SSL), that's what I'm using. The server is smtp**s**.google.com

I can't get this to work.

However the official google settings with 'use TLS' and port 587 do work.

---

### Post by iamkrazee on 2009-03-07
Did you try it in kmail/evolution? The exact same settings that you´re trying in thunderbird?

---

### Post by Nepherte on 2009-03-07
Well, both the official TLS and my SSL method work. Perhaps you should verify all the settings again? Did you use your full gmail address as username? Or perhaps it's just a connection problem as the error suggests. Can you ping to smtp.gmail.com?

---

### Post by formidable on 2009-03-07
I've tried port 465 and ssl as suggested in other threads as well as port 25 and various combinations of ssl, tsl, and tsl(if available).  None of these seem to work.  I've not tried pinging the smtp server, I'll try that when I return to work on Monday.  However, as I said, there's a windows machine sitting right next to my Ubuntu box.  The Windows machine is running the same version of TBird with the same settings and works fine.  

I haven't tried another email program, so I'll give that a shot on Monday.  Is there an email program that will read my Gmail contacts?  Thunderbird has a plug-in that reads and writes to Gmail contacts nicely. 

Any ideas?

Thanks!

---

### Post by formidable on 2009-03-12
For fun, I copied a working version of Thunderbird Portable from my windows machine to my Ubuntu box.  (These computers are in the same room.)  I ran the windows version of Thunderbird using wine.  It behaved exactly like the Linux version.  I was able to log in.  View, change, delete, and create mail, but I couldn't send any.  I got the same error as when using the Linux version (see first post).  

I'm still not running a firewall on the Ubuntu box.  Is there anywhere else to look?

Thanks.

---

### Post by devolute on 2009-03-22
> **formidable said:**
> I've tried port 465 and ssl as suggested in other threads as well as port 25 and various combinations of ssl, tsl, and tsl(if available).  None of these seem to work.  I've not tried pinging the smtp server, I'll try that when I return to work on Monday.  However, as I said, there's a windows machine sitting right next to my Ubuntu box.  The Windows machine is running the same version of TBird with the same settings and works fine.

I'm in exactly the same situation. I can ping the smtp and that's fine. I can send mail from the web interface and store drafts, but not sending from the client is becoming old :/

---

### Post by PapaNerd on 2009-03-25
I found a workaround to a similar problem between TBird on a client machine when doing an SMTP connection to my mail server.  See "Thunderbird fails to communicate with mail server" over in the Server forum.

---

### Post by PapaNerd on 2009-03-25
The link is [http://ubuntuforums.org/showthread.php?t=1105722](http://ubuntuforums.org/showthread.php?t=1105722)

---

