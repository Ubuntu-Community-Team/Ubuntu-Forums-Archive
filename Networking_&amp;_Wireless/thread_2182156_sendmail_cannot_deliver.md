---
title: "sendmail cannot deliver"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by bak&#305;r on 2013-10-20
Dear all,

We have a desktop computer with 64 bit Ubuntu 13.04, on which we run our scientific simulations. Since the tasks take quite long time, it would be highly desirable if it could give us feedback via email.

I have tried using sendmail, but the mails are not delivered to the recipients, although it reaches the relevant domain, as far as I understand. A typical error message returned by the system can be found below.

I have no experience with networking before, so have no idea how I should approach the problem. My guess would be that they are blocked by the system responsible to get rid of spams. Do I need some kind of authentication (or SMTP)?

Any help will be highly appreciated. Thanks in advance.

```
 mail -s "test" name@gmail.com 
```

```
Return-Path: <>
X-Original-To: tk@TK
Delivered-To: tk@TK
Received: by TK (Postfix)
    id 54157CC2373; Sun, 20 Oct 2013 17:10:02 +0300 (EEST)
Date: Sun, 20 Oct 2013 17:10:02 +0300 (EEST)
From: MAILER-DAEMON@gmail.com (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: tk@TK
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
    boundary="29B15CC2368.1382278202/TK"
Message-Id: <20131020141002.54157CC2373@TK>


This is a MIME-encapsulated message.


--29B15CC2368.1382278202/TK
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii


This is the mail system at host TK.


I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.


For further assistance, please send mail to postmaster.


If you do so, please include this problem report. You can
delete your own text from the attached returned message.


                   The mail system


<name@gmail.com>: unknown user: "name"


<test@TK>: unknown user: "test"


--29B15CC2368.1382278202/TK
Content-Description: Delivery report
Content-Type: message/delivery-status


Reporting-MTA: dns; TK
X-Postfix-Queue-ID: 29B15CC2368
X-Postfix-Sender: rfc822; tk@TK
Arrival-Date: Sun, 20 Oct 2013 17:10:01 +0300 (EEST)


Final-Recipient: rfc822; name@gmail.com
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "name"


Final-Recipient: rfc822; test@TK
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "test"


--29B15CC2368.1382278202/TK
Content-Description: Undelivered Message
Content-Type: message/rfc822


Return-Path: <tk@TK>
Received: by TK (Postfix, from userid 1000)
    id 29B15CC2368; Sun, 20 Oct 2013 17:10:01 +0300 (EEST)
Subject: test
To: <name@gmail.com>
Cc: <test@TK>
X-Mailer: mail (GNU Mailutils 2.99.97)
Message-Id: <20131020141001.29B15CC2368@TK>
Date: Sun, 20 Oct 2013 17:10:01 +0300 (EEST)
From: tk@TK (acer)

```

---

### Post by sanderj on 2013-10-20
Use the tool 'mailsend' instead. See [http://code.google.com/p/mailsend/](http://code.google.com/p/mailsend/) . Much easier for sending standard messages: just one command line.

---

### Post by bak&#305;r on 2013-10-20
I installed mailsend, but it asks for SMTP IP ?

---

### Post by sanderj on 2013-10-20
> **bak&#305 said:**
> I installed mailsend, but it asks for SMTP IP ?

Yes. Correct. You can use your ISP's SMTP smart host.

Or, if you want to send to a gmail.com address:

```
echo "hello, this is my mail" | mailsend -f someone@gmx.net -t  someoneelse@gmail.com -smtp gmail-smtp-in.l.google.com. -sub "Hello there" -v

```

Does that help?

---

### Post by bak&#305;r on 2013-10-20
I used your template command. Here is the error report:

```

libmsock: using getaddrinfo
 AF_INET IPv4
 IPv4 address:
 EINPROGRESS=115, EWOULDBLOCK=11
 connect(): socket=3,rc=-1, errno=115
(Debug) Try socket 3
Socket Error: [113]: No route to host
Error: Connection is closed unexpectedly
Could not send mail

```

---

### Post by sanderj on 2013-10-20
On what kind of network are you? Is your ISP (or your own firewall) blocking outgoing SMTP sessions? If your ISP is blocking: ask your ISP for his SMTP smart host

Easy test: 

```
telnet gmail-smtp-in.l.google.com. smtp
```

what does that result in?

---

### Post by bak&#305;r on 2013-10-20
The computer is directly connected to the internet via a router, currently at home. I have no idea about the other two questions, as I am not very knowledgeable in computer science. Here is the error message:

```

Trying 173.194.70.26...
Trying 2a00:1450:4001:c02::1a...
telnet: Unable to connect to remote host: Network is unreachable

```

---

### Post by sanderj on 2013-10-20
At home? Who is your ISP (Internet Service Provider)?

---

### Post by bak&#305;r on 2013-10-20
Yes. Just to avoid any confusion, we are not talking about a server, but a PC.

Google says "[COLOR=#000000][FONT=sans-serif]Turksat Uydu-Net Internet, TURKSAT-NET"

By the way, why do you suspect that ISP is blocking the outgoing traffic? The mails are returned from [email]mailer-daemon@**gmail**.com[/email][/FONT][/COLOR][FONT=arial][COLOR=#000000]. Does not that mean that the packet can reach mailman successfully without any impediment?[/COLOR][/FONT]

---

### Post by sanderj on 2013-10-20
Server / PC: doesn't matter. Linux is Linux.

Turksat? I can't find a SMTP smart host for that.
You could try "mmail-2.Turksat.com.tr." or "mmail-1.Turksat.com.tr." in the mailsend and/or telnet command

Something is blocking your SMTP traffic, otherwise you would get a SMTP session like below.
Oh, wait: you *did* type ' smtp' at the end of the telnet, didn't you?




```
server:~ sander$ telnet gmail-smtp-in.l.google.com. smtp
Trying 173.194.66.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP gj18si3334639wic.71 - gsmtp
quit
221 2.0.0 closing connection gj18si3334639wic.71 - gsmtp
Connection closed by foreign host.
server:~ sander$ 
```

and

```
sander@flappie:~$ telnet mmail-2.Turksat.com.tr. smtp
Trying 94.55.112.102...
Connected to mmail-2.Turksat.com.tr.
Escape character is '^]'.
220 Turksat Welcomes You!
quit
221 2.0.0 Service closing transmission channel
Connection closed by foreign host.
sander@flappie:~$
```

---

### Post by bak&#305;r on 2013-10-20
Here is my command:
```
 ~$ telnet gmail-smtp-in.l.google.com. smtp 
```

No improvement with these new ones, either. 
```
 ~$ telnet mmail-2.Turksat.com.tr. smtp
Trying 94.55.112.102...
telnet: Unable to connect to remote host: No route to host

```

```

~$ mailsend
SMTP server address/IP: mmail-1.Turksat.com.tr.
From: name   
To: mymail@gmail.com
Subject: test
test
Socket Error: [113]: No route to host
Error: Connection is closed unexpectedly
Could not send mail

```

Similarly for others.

---

### Post by sanderj on 2013-10-20
So that's more proof SMTP sessions are blocked. If you're not using a firewall on your Ubuntu machine, it must be your ISP

Are you on a wired Internet connection (DSL, cable) or wireless (3G, 4G)?
Are you the paying customer of Turksat? Or is the bill paid by someone else?
Do you have a mail client set up on your Ubuntu system? So Thunderbird or Evolution? Is that working? If so: what is the SMTP server you have filled out?
Can you find on Turksat's website how to set up a mail client Outlook? That should tell what SMTP server they provide

---

### Post by bak&#305;r on 2013-10-20
The connection is via a wireless cable router, service paid by me. I use web-based clients, but thunderbird does work for my colleagues' emails without trouble.

posta.uydunet.net is suggested somewhere, but it does not work, either.

I think SMTP and Telnet use ports 23 25, right? If so, I checked them, and they are unreachable from the web.

Maybe easiest thing could be to take the computer back to office tomorrow, and see whether I encounter the same problems there, on a completely different network?

By the way, thank you for your time.

---

### Post by sanderj on 2013-10-20
[QUOTE=bak&#305;r;12822198]but thunderbird does work for my colleagues' emails without trouble.

Those colleagues are not on your LAN, I suppose?

Yes, try the same test at your work.

---

### Post by bak&#305;r on 2013-10-20
They use this computer at the office from time to time. I will give you feedback, once I try.

---

### Post by bak&#305;r on 2013-10-21
I checked it at work, and everything worked without a trouble, including successful delivery of the mail. They mostly end up in spam folders, though.

Thank you very much for your help sanderj, I would never think about closed ports. Strange that my network was somehow blocking the traffic.

---

### Post by bak&#305;r on 2013-10-21
So, my ISP at home blocks some ports (including 25) to avoid spam attacks and will not enable them unless I use a static IP (which has some additional costs). Are there other ports to use or am I a hopeless case?

---

### Post by sanderj on 2013-10-21
> **bak&#305 said:**
> So, my ISP at home blocks some ports (including 25) to avoid spam attacks

Is that a fact? Or an assumption?

If it is a fact: how do you know? Did you ask them? Website? If so, I expect them to provide a SMTP server / SMTP smart host. Did you ask for that?

---

### Post by bak&#305;r on 2013-10-21
Fact. I called them. All the information I could extract was that the following three would be available to use only with a static IP via port 587 (?):
 mmail-50.turksat.com.tr
 mmail-1.turksat.com.tr
 mmail-2.turksat.com.tr

---

### Post by sanderj on 2013-10-22
I would say it's guessing from now on.

Or set up a VPN to send out mail, but you will need a VPN / SSH provider for that.

---

### Post by smtp on 2013-10-22
[FONT=arial]The reason that your first example was not delivered to gmail is that you sent it to non-existing user, namely [/FONT]
[email]name@gmail.com[/email]

[FONT=arial]If your network is okay now, please try to send a message to a real e-mail address.[/FONT]

---

