---
title: "Evolution - Hotmail (POP3) can't send messages"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by jc-sama on 2010-06-29
Hi, I have Evolution and Im trying to set up two email accounts, Gmail and Hotmail. My problem is that i can send and receive with Gmail (main/default account) using IMAP, but Hotmail with POP3 just receive, because when i try to send an email, evolution tries to send it through gmail and never finish. What could be the problem? thanks =)

This is my setup to send emails with hotmail:

Server type - SMTP
Server - smtp.live.com
Server requires authentication - checked
Use safe connection - SSL encrypting
Authentication type - Plane
User - [EMAIL="xxxxx@hotmail.com"]xxxxx@hotmail.com[/EMAIL]
Remember password - checked

This is my setup to send emails with Gmail (main/default account):

Server type - SMTP
Server - smtp.gmail.com
Server requires authentication - checked
Use safe connection - TLS encrypting 
Authentication type - Plane
User - [EMAIL="xxxxxxx@gmail.com"]xxxxxxx@gmail.com[/EMAIL]
Remember password - checked

---

### Post by ubunterooster on 2010-06-29
How about: 

> **Indras said:**
> Okay everyone, after digging around in these  forums and googling like I've never googled before, I figured out how to  send and receive e-mail through hotmail using Evolution.  I'm throwing  together a rough HOWTO for others.  If things need more clarification,  let me know and I'll update it.
<snip>
**Receive Server type:** POP
**Server:** 127.0.0.1
**Username:** *xxx*@hotmail.com (same as above)
**Security:** No encryption
**Authentication type:** Password
(Remember password checkbox is up to you)

**Send Server type:** SMTP
**Server:** 127.0.0.1:2500
**[X] Server requires authentication** (check this box)
**Use Secure Connection:** [COLOR=Red]No encryption[/COLOR]
**Authentication Type:** [COLOR=Black]PLAIN[/COLOR]
**Username:** *xxx*@hotmail.com (same as above)
(Optional Remember password checkbox)

---

### Post by dilei on 2010-10-06
> **ubunterooster said:**
> How about:

This did not work for me.

Anything else I can try?

Thanks in advance.

---

### Post by claracc on 2010-10-06
When you click on new in evolution to send a mail, you have to change in the from box and write your hotmail address, otherwise it will try yo send the message with your default  gmail account.

---

### Post by dilei on 2010-10-06
> **claracc said:**
> When you click on new in evolution to send a mail, you have to change in the from box and write your hotmail address, otherwise it will try yo send the message with your default  gmail account.

I get what you are saying, but it applies for the other guy who needed help. I don't have a Gmail account, I'm only having trouble with outgoing mails in Live. Already tried with the settings Microsoft provides.

---

### Post by claracc on 2010-10-06
I didn't notice I was answering a so old post.

For you get quick and better answers, you should try to open your own thread.

Anycase, the following link, [http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/) explains howto configure your hotmail account in evolution.

I hope it can help

---

### Post by philinux on 2010-10-06
Hotmail in evolution.

pop3.live.com:995 and ssl to receive.

smtp.live.com:25 and tls to send.

---

### Post by dilei on 2010-10-10
> **philinux said:**
> Hotmail in evolution.

pop3.live.com:995 and ssl to receive.

smtp.live.com:25 and tls to send.


Awesome, that did the trick!

Thanks!
Ivo

---

