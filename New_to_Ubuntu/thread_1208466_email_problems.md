---
title: "email problems"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by helmylin2 on 2009-07-09
Hello,
 
I have just bought a new Dell inspiron 10" net book with Ubuntu on it.  All was going fine until I tried to set up the email account.  I have put in the information from ntlworld.com.  It dosen't like it says no such server.  I even went onto my Windows computer and checked the settings.  They are the same.  Any help would be appriciated.  Thank you :D

---

### Post by pmlxuser on 2009-07-09
well it seems you have omitted some information, you are trying to set email account on what client. thunderbird or evolution ??.

unless you specify people might find it difficult to help..

---

### Post by alexlafreniere on 2009-07-09
Could you give us a little more information on what settings you put into your Ubuntu mail client, and what info you have to put into your Windows client? And I'm assuming you're using Evolution, the default email client in Ubuntu.

---

### Post by helmylin2 on 2009-07-09
Hello All, 
 
I'm new at this foum stuff. I'll try to give more information.
 
I'm using evolution.
 
The Information is POP3 Server: pop.ntlworld.com
SMTP: smtp.ntlworld.com
 
Now then on the pop 3 server it says port 110 and on the smtp server it says port 25. I can't find any place to put that information.
 
The settings are the same on windows. Windows works. Sorry I'm rambling.

---

### Post by Paddy Landau on 2009-07-09
> **helmylin2 said:**
> Now then on the pop 3 server it says port 110 and on the smtp server it says port 25. I can't find any place to put that information.
I haven't seen anywhere in Evolution to put ports, but ntlworld should work OK with it.

Receiving email: Server Type "POP", Server "pop.ntlworld.com", Username (your username), Security "no encryption", Authentication type "Password"

Sending E-mail: Server type "SMTP", Server "smtp.ntlworld.com", Security "No encryption".

If it doesn't work, we need the exact error message (how do you know it's not working?).

---

### Post by thomps on 2009-07-09
Correct me if I'm wrong, but I believe you can specify the port number at the end of the server location in Evolution.

For example:
```
pop.ntlworld.com:110
```

---

### Post by A_M_S on 2009-07-09
The pop3 and smtp services usually are available in ports 110 and 25.These  ports are used by default on most mail clients.

---

### Post by helmylin2 on 2009-07-09
Hello,
 
I must be incredibly stupid but I'm getting nowhere.  I have tried typing with and without the quotation marks.  No joy.
 
Error while performing operation.
 
Host hookup failed: POP, Server pop.ntlworld.com: Name or service not known.
 
Is there any way to get my hotmail account on this?  I'll settle for that.
 
Thank you

---

### Post by XCan on 2009-07-09
That kind of sounds like you can't resolve pop.ntlworld.com, what happens if you replace it with the IP, which I resolve to: 81.103.221.14.

Yes you can setup your hotmail account (pop3) using the addys provided by hotmail.

---

### Post by helmylin2 on 2009-07-09
HI,  I'm fast getting computer rage.  Error while performing operation.
 
Unable to connect to POP server 81.103.221.14: No suport for the requested authentication mechanism.
 
Did get one step further it asked for my password.
 
Think I will see if I can get on with hot mail.
 
Thanks again.

---

### Post by helmylin2 on 2009-07-09
Hello,
 
Thank you all, no joy at all I think I will just give it up.:(

---

### Post by jonobr on 2009-07-09
Man

What would general patton think? :-)

OPen a terminal window

In the terminal window type

```
telnet pop.ntlworld.com 110
```

It should say read or something

the type
```
USER <name>
```
where name is your login

Then 

```
PASS <password>
```

It should authenticate you 

Then type 

```
List
```

It should list your emails

Let us know if this works and what fails and where

We will get to SMTP in a second.

Additional- Just to explain, the commands you are using above are the commands evolution would use to access pop emails.
Your just doing it without an application.
This means if this works, and the settings for evolution are identical, then you have an evolution problem,
if this doesnt work, then you have either a networking or ISP issue

---

### Post by helmylin2 on 2009-07-10
Hello all,

Just to let you know I updated my system this morning.  194 updates were downloaded and installed.  After that I thought I would have one more go at setting up the email account.  Put in the original pop information and it accepted it.  I don't know if the updates did it or what.  But I'm ok now.  Now I'm happy with my little net book and Ubuntu.  Thank you all again.

---

### Post by jonobr on 2009-07-10
Great to hear its working,

:guitar:

I would recommend following the steps I outline as if and when you run into problems in the future, this method will let you know if its a application or ISP issue.

For smtp you can do the following commands to test smtp

```

telnet smtp.ntlworld.com
mail from:me@here.com
rcpt to: me@gmail.com
data
123121212121212

```

The escape sequence to send the email differs in applications but once you
enter your data it will tell you the send or escape sequence.

most often its a . on a line by itself.

You may think you are doing something wrong when trying this, or think it may be hacking, but its not, you are using the same commands an application would use to send and receive email

---

