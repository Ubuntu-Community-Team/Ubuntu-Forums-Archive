---
title: "Simple method to send mail to an external email address?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by beju0506 on 2009-03-09
Hey everyone,

This is my first time posting here. Let me explain what is going on. I'm trying to set up my Ubuntu 8.10 installation to be able to send a mail from the command line to my non-local email address. I've searched the forums, I've searched google, I've tried a TON of different things. I don't particularly care how the email is sent, or what mail program does it, as long as it can be done via a script. (I'm using it to notify me when a backup has been done on my home computer.) 
I tried setting up exim and doing it but could only get "remote connections not supported" or something like that in the /var/mail/user log... I spent several days trying to resolve it but no luck. I tried installing postfix and configuring that and it seems like it's sort of working but I don't have a qualified domain name, so I had to put a random name in there (I made sure it was an actual domain/website though). The config I have for postfix doesn't give me an error about sending remote mail, but it just times out when trying to send mail to my target email address. My ISP does not offer an SMTP relay server as far as I know, so I'm getting pretty frustrated. I don't want to get mail from my computer, I just want to send out a notice to my non-local email via a shell script. Does anyone have any suggestions? There must be some way? :(

Thanks!

-Justin

---

### Post by brian_p on 2009-03-09
> **beju0506 said:**
> 

I don't want to get mail from my computer, I just want to send out a notice to my non-local email via a shell script. Does anyone have any suggestions? There must be some way?

```
apt-get install sendemail
```

---

### Post by Kareeser on 2009-03-09
It's "sendmail"... unless "sendemail" is a different package...

---

### Post by brian_p on 2009-03-09
> **Kareeser said:**
> It's "sendmail"... unless "sendemail" is a different package...

```
apt-cache show sendemail
```

---

### Post by beju0506 on 2009-03-09
Brian,

Is that a different program than "sendmail"? What is the difference between them?

Thanks! :)

-Justin

---

### Post by beju0506 on 2009-03-09
Brian, 

I tried to install this but had two issues:

1. bash wouldn't recognize the command after install
2. It requires a separate SMTP server (I don't have one, so I need to be able to run my own on the computer)

Do you know how to do that?

Thanks!

-Justin

---

### Post by brian_p on 2009-03-09
> **beju0506 said:**
> 

1. bash wouldn't recognize the command after install

I forgot 'sudo'.

```
sudo apt-get install sendemail
```

Or use synaptic to install it.

> 2. It requires a separate SMTP server (I don't have one, so I need to be able to run my own on the computer)

No it doesn't. Read the package description, particularly the dependencies. sendemail is different from sendmail (which is similar to exim and postfix).

---

### Post by brian_p on 2009-03-09
> **beju0506 said:**
> Brian, 

I tried to install this but had two issues:

1. bash wouldn't recognize the command after install

I may have misunderstood you here. You meant the command

```
sendemail
```

did not work?

It's

```
sendEmail
```

---

### Post by beju0506 on 2009-03-09
Brian,

I was wrong about the SMTP thing, I had misread something in the description. I installed it via APT-GET but I could't run it (command not found). Then after finding the website I realized it's a perl script? How would I set up the system to allow me to run it from whatever directory I am currently in?

Thanks!
 :)

-Justin

---

### Post by brian_p on 2009-03-09
> **beju0506 said:**
> Brian,

How would I set up the system to allow me to run it from whatever directory I am currently in?

Does my last post answer that?

You may also need to install libio-socket-ssl-perl and libnet-ssleay-perl to connect to some mail servers.

---

### Post by benerivo on 2009-03-09
sendEmail (capital E?)

---

### Post by lovinglinux on 2009-03-09
sendEmail works pretty fine for me, but not with all accounts. I guess you need an account with smtp on port 25 to work.

Here is an example of command that works for me:

```
sendEmail -f **[COLOR="Red"]username@foo.com[/COLOR]** -t [COLOR="Red"]**destination@foo.com**[/COLOR] -cc **[COLOR="Red"]carboncopy@foo.com[/COLOR]** -u "**[COLOR="Red"]Message title[/COLOR]**" -m "[COLOR="Red"]**The body of the message**[/COLOR]" -s [COLOR="Red"]**smtp.foo.com**[/COLOR]:25 -xu **[COLOR="Red"]username[/COLOR]** -xp [COLOR="Red"]**password**[/COLOR]
```

Replace stuff in red accordingly.

---

### Post by beju0506 on 2009-03-09
Ahhh, ok. The uppercase E in the middle was what was causing the issue (the name in the apt-get response was 'sendemail' without the capital). However, I don't have an SMTP server and I've sent two mails through this with no results... (It says it sends them successfully, but I don't get anything in the receiver email account..) :( Any ideas?

Thanks for all of your help!! 

-Justin

---

### Post by lovinglinux on 2009-03-09
> **beju0506 said:**
> Ahhh, ok. The uppercase E in the middle was what was causing the issue (the name in the apt-get response was 'sendemail' without the capital). However, I don't have an SMTP server and I've sent two mails through this with no results... (It says it sends them successfully, but I don't get anything in the receiver email account..) :( Any ideas?

Thanks for all of your help!! 

-Justin

You don't need an SMTP server. All you need is an e-mail account with any service on the net that accept sending mails on port 25. I'm afraid GMail doesn't work, because it uses SSL authentication, but I'm sure you can find other free email services for this.

Look my code example. I used "smtp.foo.com:25", which means that you don't need a server installed locally. That's why send**E**mail is much easier than exim, postfix, sendmail etc.

EDIT: After sending the e-mail yous should see something like this:

```
Mar 09 21:44:57 mycomputer sendEmail[27485]: Email was sent successfully!
```

---

### Post by beju0506 on 2009-03-09
LovingLinux,

I wasn't clear about what I wanted, I think. I want to be able to send emails from my computer to an external email without the use of a separate email service or my ISP's smtp server. 
Basically, I want to have an SMTP server running on my machine and be able to send mail directly from that, rather than using say, gmail's smtp server to send mails to another address.
That is why I originally chose postfix, etc because I understood that would set up its own smtp server to preclude the need for a 3rd party "sender" email address. I also wanted to be able to send mail via the command line from a my backup shell script.

Hope that helps! :) 

Thanks! :)

---

### Post by beju0506 on 2009-03-09
LovingLinux,

After a second thought, I'll try your solution. I guess the reason I wanted to avoid that was that a lot of places revoke your account if you don't physically log in ever so often. But I can try to play around with it. Maybe if I just continually use it, it won't do that. It'll probably be easier than messing around with the SMTP server settings.

Thanks!

-Justin

---

### Post by lovinglinux on 2009-03-09
> **beju0506 said:**
> LovingLinux,

After a second thought, I'll try your solution. I guess the reason I wanted to avoid that was that a lot of places revoke your account if you don't physically log in ever so often. But I can try to play around with it. Maybe if I just continually use it, it won't do that. It'll probably be easier than messing around with the SMTP server settings.

Thanks!

-Justin

Yes, it simpler then messing with SMTP servers. The only problem I see is that sendEmail sends the username and password as plain text, without secure connection. But if you setup an account just for this, it shouldn't be a major problem.

If you still want to use a local server, then mut can be used to send e-mails trough command-line.

---

### Post by Vantrax on 2009-03-09
Ive used sendmail and a little scripting to great effect, but sendemail has a few extra features that you should definitely be trying to use to avoid your particular issues.

---

### Post by beju0506 on 2009-03-09
Alright, one last question... (It's the last one, I promise :))

Does anyone know of an email service this works for? I've signed up for several different accounts and none of them seem to work with this... 

Thanks! 

-Justin

---

### Post by lovinglinux on 2009-03-09
> **beju0506 said:**
> Alright, one last question... (It's the last one, I promise :))

Does anyone know of an email service this works for? I've signed up for several different accounts and none of them seem to work with this... 

Thanks! 

-Justin

[http://www.terra.com/](http://www.terra.com/)

But I'm not sure they provide free accounts.

---

### Post by beju0506 on 2009-03-09
Hey everyone!

I just wanted to say thanks! It worked just fine. My problem was that my email provider's SMTP port was 2525 instead of 25 :-P

Thanks again!

---

### Post by brian_p on 2009-03-10
> **lovinglinux said:**
> You don't need an SMTP server. All you need is an e-mail account with any service on the net that accept sending mails on port 25. I'm afraid GMail doesn't work, because it uses SSL authentication, but I'm sure you can find other free email services for this.

sendemail will work with gmail. Post #10.

---

### Post by lovinglinux on 2009-03-10
> **brian_p said:**
> sendemail will work with gmail. Post #10.

```
libio-socket-ssl-perl and libnet-ssleay-perl
```

Those work if I'm using bash scripts?

---

### Post by brian_p on 2009-03-10
> **lovinglinux said:**
> ```
libio-socket-ssl-perl and libnet-ssleay-perl
```

Those work if I'm using bash scripts?

From the command line:

```
sendEmail -f brian@example.com -t user@example.com -u test -m message -s smtp.gmail.com -xu gmail_username -xp gmail_password
```

works for me. There is no reason it wouldn't work in a script.

---

### Post by lovinglinux on 2009-03-10
> **brian_p said:**
> From the command line:

```
sendEmail -f brian@example.com -t user@example.com -u test -m message -s smtp.gmail.com -xu gmail_username -xp gmail_password
```

works for me. There is no reason it wouldn't work in a script.

I already used that command on a script. Actually I was asking if those perl libraries would make a difference when using bash, because I have tried gmail before (without the libraries installed) and it didn't worked. Anyway, I'm just curious, since I haven't used that script for a while.

---

