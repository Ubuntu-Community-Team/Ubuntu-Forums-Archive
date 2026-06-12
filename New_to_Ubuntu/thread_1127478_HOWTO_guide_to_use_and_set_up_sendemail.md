---
title: "HOWTO guide to use and set up sendemail"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by steve101101 on 2009-04-16
In case you do not know you can send email messages from the terminal to any email address or user. I find it to be particularly useful to send emails to myself after my computer completes automated tasks.

One such task is when I used a cron command to backup my computer weekly. It is important to me to know this was done successfully without having to dig through log files.

Here is how to setup sendemail ...

First

```

sudo apt-get install sendemail

```
```

sudo apt-get install libio-socket-ssl-perl

```

These two commands get all the needed files from the repositories and installs them. Now to actually send a message. 

```

sendEmail -f username@foo.com -t destination@foo.com -cc carboncopy@foo.com -u "Message title" -m "The body of the message" -s smtp.foo.com:25 -xu username -xp password

```

This will work with a variety of smtp hosts including gmail. To use gmail change the last line to this ...

```

sendEmail -f username@foo.com -t destination@foo.com -u "Message title" -m "The body of the message" -s smtp.gmail.com:25 -xu username -xp password

```


thanks to 'lovinglinux' for helping me with this

---

### Post by lovinglinux on 2009-04-16
> **steve101101 said:**
> thanks to 'lovinglinux' for helping me with this

You are welcome. SendEmail is great if you want a simple method of sending messages through cli without messing with MTA and mail servers.

---

### Post by steve101101 on 2009-04-16
yes it is. Its great.

---

### Post by Zyprexa on 2009-12-14
I'm trying to use sendEmail to mail me virus scan report from an ftp server. But it fails to send the mail if the scan takes too long. I try:```
$ sudo clamscan <clamscan options> | sendEmail -f <my mail on server> -t <my email> -u "Virus Report" -s <my isp's smtp>
```I get:```
Reading message body from STDIN because the '-m' option was not used.
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.

Dec 15 03:53:52 <hostname> sendEmail[8906]: EXITING: Received SIGALRM
```a simple echo or a short scan will send just fine :(

How can i disable this timelimit?

EDIT: my bad, i just found the "-o timeout=" option :)

---

### Post by steve101101 on 2009-12-14
glad you found the option.

---

### Post by kitama on 2013-02-18
I am a newbie and have a few questions.

If I send an email through my gmail account I get the following error message:

```
server sendmail [15257]: ERROR => ERROR => SMTP-AUTH: Authentication to smtp.gmail.com: 25 failed.
```How do I send an e-mail:

```
sendEmail -f username@foo.com -t destination@foo.com -u "Message title" -m "The body of the message" -s smtp.gmail.com:25 -xu username -xp password
```Should I replace [EMAIL="username@foo.com"]username@foo.com[/EMAIL] with my own email address and [EMAIL="destination@foo.com"]destination@foo.com[/EMAIL] with that of the recipient?

And what do I fill in at: -xu username and -xp password? My gmail account details or something else? Can someone give an example, thanks!

Sorry, for my bad English.

---

### Post by QIII on 2013-02-18
Thank you for sharing.  Everyone’s questions and answers are valuable.

But if a thread has had no activity for about a year or more, it is best to start a new thread of your own because you will be more likely to get a response.  

Please feel free to add a link to this thread in the new one you start.

*Thread** closed.***

---

