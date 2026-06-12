---
title: "More Telnet Problems"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Swenghk on 2009-12-21
Okay... When I try to telnet to any server, I get a message. Even localhost!:

```
seth@SETH-LAPTOP:~$ telnet localhost
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
seth@SETH-LAPTOP:~$ 

```

```
seth@SETH-LAPTOP:~$ telnet pop.gmail.com 995
Trying 74.125.155.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.
user sethrobert94@gmail.com
Connection closed by foreign host.

```

And I also keep getting the ```
Connection closed by foreign host.
```message! What is that about? Any help is appreciated! Cheers

---

### Post by falconindy on 2009-12-21
Telnet is an unsecure protocol and has been fairly deprecated in favor of its secure counterpart, ssh. It makes sense that you're being denied, particularly from localhost.

What is it you're trying to accomplish?

---

### Post by Swenghk on 2009-12-21
Well... I'm trying to learn telnet. Just for the purpose of learning it. I want to learn about TCP/IP. But I have it fixed now. Hahaha

---

### Post by fromthehill on 2009-12-21
you've already learned telnet
you established a connection with a remote server
that's pretty much it

what happens next depends on where you trying to connect to
if you connect to a linux computer you'll get a linux command-line encironment
if you connect to a cisco router you'll get an IOS environment
etc.
the google smtp address does nothing (or at least not without the right commands.)

that has nothing to do with telnet itself

---

### Post by Swenghk on 2009-12-21
I just was trying to see if it was still possible to check your e-mail through telnet. Which it is not as it seems... Can you do it through SSH?

---

### Post by fromthehill on 2009-12-21
I got it working :)
will post the commands in a moment

ok not exactly working
I got it to do something :P

```
telnet gmail-smtp-in.l.google.com 25
```
```
HELO gmail-smtp-in.l.google.com
```
```
MAIL FROM: <mail@mail.com>
```
with brackets!. this can be anything (it doesn't seem to work anyway)

```
RCPT TO: <mail@mail.com>
```
where you send your mail to (can only be a gmail account)

```
DATA
```
start the mail
```
FROM: test
```
adds something in 'from' field of the e-mail
```
SUBJECT: test
```
the subject of the mail

```
.
```
end of mail

```
QUIT
```
stop telnet session

after saving the mail as eml and opening with gedit
> Delivered-To: *****@gmail.com

Received: by 10.239.132.137 with SMTP id 9cs636552hbr;

        Mon, 21 Dec 2009 07:34:33 -0800 (PST)

Received: by 10.213.110.201 with SMTP id o9mr9062181ebp.35.1261409673214;

        Mon, 21 Dec 2009 07:34:33 -0800 (PST)

Return-Path: <mail@mail.com>

Received: from gmail-smtp-in.l.google.com ([193.141.75.234])

        by mx.google.com with SMTP id 3si294327ewy.27.2009.12.21.07.32.56;

        Mon, 21 Dec 2009 07:34:33 -0800 (PST)

Received-SPF: neutral (google.com: 193.141.75.234 is neither permitted nor denied by domain of [email]mail@mail.com[/email]) client-ip=193.141.75.234;

Authentication-Results: mx.google.com; spf=neutral (google.com: 193.141.75.234 is neither permitted nor denied by domain of [email]mail@mail.com[/email]) smtp.mail=mail@mail.com

Date: Mon, 21 Dec 2009 07:34:33 -0800 (PST)

Message-Id: <4b2f9589.0367f10a.5072.7dedSMTPIN_ADDED@mx.google.com>

FROM: test

SUBJECT: lala

everything you type between 'DATA' and '.' will be sended to the e-mail adress. if you type some random things it will be at the bottom of the file. your email client won't do anything with that

---

### Post by Swenghk on 2009-12-21
Mine seems to freeze up on```
Trying 209.85.222.50...

```Hm... How long should it normally take?

---

