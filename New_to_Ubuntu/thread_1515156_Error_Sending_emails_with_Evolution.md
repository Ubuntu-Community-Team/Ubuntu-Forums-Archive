---
title: "Error: Sending emails with Evolution"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-06-21
I am using Evolution for the first time and I am able to receive messages but unable to send messages. I get the following message:```
Sender address rejected: not logged in
```

---

### Post by jtarin on 2010-06-22
What email service are you using? Your POP configuration is possibly not correct. Sending would be your smpt configs. There is probably a checkbox for using name and password authentication.

---

### Post by muddpup64 on 2010-06-22
I do not know how to find smpt configurations. And I am using Aol.

---

### Post by dwel on 2010-06-22
> **muddpup64 said:**
>  I am using Aol.

If your receiving messages they must have pop3 available. 
Look in their help about pop3 setup. you may even be able to get a clue from your get mail server, which is usually pop3.*domain*.com and perhaps the send mail server is smtp.*domain*.com


Just a thought

---

### Post by muddpup64 on 2010-06-22
I'm lost.

---

### Post by dwel on 2010-06-22
[http://email.about.com/od/accessingaolmail/f/AOL_Mail_POP3_Settings.htm](http://email.about.com/od/accessingaolmail/f/AOL_Mail_POP3_Settings.htm)

[http://email.about.com/od/accessingaolmail/f/AOL_Mail_SMTP_Settings.htm](http://email.about.com/od/accessingaolmail/f/AOL_Mail_SMTP_Settings.htm)

---

### Post by muddpup64 on 2010-06-22
> Sorry, 'www.smtp.aol.com' does not exist or is not available. I can  not find it.

---

### Post by plucky on 2010-06-22
> **muddpup64 said:**
> I can  not find it.

no www in [www.smtp.aol.com](www.smtp.aol.com)

Setup as screenshot.

Good Luck

---

### Post by muddpup64 on 2010-06-22
I have no clue what you want me to do because I tried:> [smtp.aol.com]("http://www.smtp.aol.com/") and it still won't work. I'm sorry but this is starting to become very frustrating and I know how you must feel. But I just don't understand.

---

### Post by dwel on 2010-06-22
try thunderbird

what is thunderbird?
It is a top notch email client

How easy is it?
A cave man could use it

How do I install it?
Sudo apt-get install thunderbird

I installed it, wheres the icon?
Menu>internet>thunderbird or:
Applications>internet>thunderbird Or:
Accessories>terminal type:'thunderbird'


Thunderbird should already know everything you need to know.

---

### Post by muddpup64 on 2010-06-22
Thanks.

---

### Post by dwel on 2010-06-22
Thanks as in: it worked?

---

### Post by muddpup64 on 2010-06-22
No, not really, but I can ask a buddy of mine, he is literally IBM's best employee. He uses evolution on his Ubuntu and I am 100% sure he can help. But thanks anyway.

---

### Post by dwel on 2010-06-22
I swore to everything good and holy that I would never sign up for a aol email account, but I did, just for you.


Thunderbird asked me my name, email address and password.....scanned....clicked create account, and I checked my email, and then mailed myself something. It worked flawlessly.


Edit: now I have to go bathe, I feel infected.

---

### Post by dwel on 2010-06-22
[http://postmaster.aol.com/Postmaster.Errors.html]("http://postmaster.aol.com/Postmaster.Errors.html")

I found this, there is a massive amount of reasons that it might not be working. Its not your fault or Ubuntus or even thunderbird. Sorry, and good luck.

---

### Post by lisati on 2010-06-22
> Sender address rejected: not logged in
I'm scratching my head here. I remember seeing a similar error message several years ago with another email provider and another email program on another OS, but can't remember what the solution was. What I'm thinking has already been suggested: check the settings on Evolution/Thunderbird/whatever.

---

### Post by jtarin on 2010-06-22
[Take your pick of solutions.....there's one for everyone.]("http://www.google.com/#hl=en&source=hp&q=setting+up+pop+account+evolution+aol&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=45835207582d5ee7")

[They probably have a block on your range of Dynamic IP addresses.]("http://postmaster.aol.com/Postmaster.Errors.html")
Time to ditch AOHELL and go gmail.

---

### Post by muddpup64 on 2010-06-22
Is thunderbird like evolution or is it like aol? If so then I will drop aol in a heart beat, trust me I hate it to.

---

### Post by jtarin on 2010-06-22
> **muddpup64 said:**
> Is thunderbird like evolution or is it like aol? If so then I will drop aol in a heart beat, trust me I hate it to.

Thunderbird and Evolution are both clients. AOL is a server where your mail account is hosted.They have a web-based client that their customers use. You should change servers. Gmail, Yahoo etc.

---

### Post by dwel on 2010-06-23
> **jtarin said:**
> You should change servers. Gmail, Yahoo etc.

I absolutely agree with this.

---

### Post by muddpup64 on 2010-06-23
Then gmail it is. Thanks it works now. 
Awesome :guitar:

---

