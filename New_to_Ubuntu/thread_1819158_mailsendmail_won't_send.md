---
title: "mail/sendmail won't send"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by bneva on 2011-08-05
Hi there, I need to use either mail or sendmail for part of my project and I am just trying to fool around with it but it won't send any emails.

The commands I used were:

```
mail -s "Hello World" myemail@email.com
```

followed by a CTRL D to send the mail

For sendmail I used the same thing
```
sendmail -s "Hello World" myemail@email.com
```
I didn't press anything after this because I read ctrl D doesn't work for send mail.  So basically it just sits there.

I tried it with a hotmail and gmail account but I didn't receive anything.  Is my syntax wrong or am I missing something?

---

### Post by haqking on 2011-08-05
> **bneva said:**
> Hi there, I need to use either mail or sendmail for part of my project and I am just trying to fool around with it but it won't send any emails.

The commands I used were:

```
mail -s "Hello World" myemail@email.com
```followed by a CTRL D to send the mail

For sendmail I used the same thing
```
sendmail -s "Hello World" myemail@email.com
```I didn't press anything after this because I read ctrl D doesn't work for send mail.  So basically it just sits there.

I tried it with a hotmail and gmail account but I didn't receive anything.  Is my syntax wrong or am I missing something?


i take it you have sendmail installed right ? ;-)

see here for a simple explanation on how to use [http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/](http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/)

---

### Post by bneva on 2011-08-05
> **haqking said:**
> i take it you have sendmail installed right ? ;-)

see here for a simple explanation on how to use [http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/](http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/)

haha yes just the usual sudo apt-get install sendmail and I believe for mail I downloaded heirloom-mailx

when I use that guide everything is fine until I use the telnet commands.

```
telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 bneva ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu1; Fri, 5 Aug 2011 16:16:44 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
mail from:test@test.com
503 5.0.0 Polite people say HELO first
rcpt to:root@localhost
503 5.0.0 Need MAIL before RCPT

```

instead of [email]test@test.com[/email] I put my actual email in but this is what happens.

---

### Post by haqking on 2011-08-05
> **bneva said:**
> haha yes just the usual sudo apt-get install sendmail and I believe for mail I downloaded heirloom-mailx

when I use that guide everything is fine until I use the telnet commands.

```
telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 bneva ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu1; Fri, 5 Aug 2011 16:16:44 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
mail from:test@test.com
503 5.0.0 Polite people say HELO first
rcpt to:root@localhost
503 5.0.0 Need MAIL before RCPT

```instead of [EMAIL="test@test.com"]test@test.com[/EMAIL] I put my actual email in but this is what happens.
it is case sensitive

ehlo or helo first

then mail should MAIL FROM:
RCPT TO:

etc

then DATA
type your message and finish with a period .

---

### Post by bneva on 2011-08-05
> **haqking said:**
> it is case sensitive

ehlo or helo first

then mail should MAIL FROM:
RCPT TO:

etc

then DATA
type your message and finish with a period .

but do I give HELO my actual IP address or what do I put in?

---

### Post by haqking on 2011-08-05
> **bneva said:**
> but do I give HELO my actual IP address or what do I put in?
  you type

EHLO or HELO (you are saying hello)

then:

MAIL FROM:bob@bob
RCPT TO: xxxxx
DATA
this is my email mesage etc etc
.

remember its case sensitive so capitalise commands, your commands were lower case

---

### Post by bneva on 2011-08-05
> **haqking said:**
> you type

EHLO or HELO (you are saying hello)

then:

MAIL FROM:bob@bob
RCPT TO: xxxxx
DATA
this is my email mesage etc etc
.

remember its case sensitive so capitalise commands, your commands were lower case

yes but what I am saying this is what happens when I type HELO/EHLO
```
telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 bneva ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu1; Fri, 5 Aug 2011 16:42:27 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
EHLO
501 5.0.0 EHLO requires domain address

```

---

### Post by haqking on 2011-08-05
> **bneva said:**
> yes but what I am saying this is what happens when I type HELO/EHLO
```
telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 bneva ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu1; Fri, 5 Aug 2011 16:42:27 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
EHLO
501 5.0.0 EHLO requires domain address

```

oh gotcha

yeah type

EHLO or HELO (EHLO is more upto date and some dont accept it, all will accept HELO)

so HELO localhost

it will then greet you

---

### Post by bneva on 2011-08-05
ok well that sent the email to root, but it still doesn't help me with sending an email through the cmdline (without telnet).

---

### Post by haqking on 2011-08-05
> **bneva said:**
> ok well that sent the email to root, but it still doesn't help me with sending an email through the cmdline (without telnet).


ha do you want me to do it for you ? LOL

sendmail does not by defatul allow realying to external sources if your are trying to achieve that.

however the link i first posted exaplins that [http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/](http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/)

so using hotmail and gmail wont work as it wont allow it.

---

### Post by bneva on 2011-08-05
> **haqking said:**
> ha do you want me to do it for you ? LOL

sendmail does not by defatul allow realying to external sources if your are trying to achieve that.

however the link i first posted exaplins that [http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/](http://www.linuxmaza.com/sendmail/simple-steps-to-send-mail-using-sendmail-on-linux-fedora-centos-ubuntu/)

so using hotmail and gmail wont work as it wont allow it.

ok but what about the MAIL command?  my friend has it working, and mine doesn't.  He doesn't know how to help me because his just worked.  I don't know if I installed the wrong package for mail, which one should it be?  He said he just found one called "mail" but I don't see it anywhere.

---

### Post by haqking on 2011-08-05
> **bneva said:**
> ok but what about the MAIL command?  my friend has it working, and mine doesn't.


what about the mail command ?

You said the it worked a minute ago and sent to root ?

you have installed sendmail, you could telnet to localhost and you sent a mail which you said worked so whats wrong with the MAIL command ?

as for sending to externally you will need to edit a file (i cant remember which offhand) to send mail externally as  by default it does not allow relaying

this will set it up for external relaying [http://www.recital.com/index.php?option=com_content&view=article&id=71%3Ahowto-configure-linux-sendmail-to-use-external-isp-as-smtp-mail-relay&Itemid=59](http://www.recital.com/index.php?option=com_content&view=article&id=71%3Ahowto-configure-linux-sendmail-to-use-external-isp-as-smtp-mail-relay&Itemid=59)

---

### Post by bneva on 2011-08-05
> **haqking said:**
> what about the mail command ?

You said the it worked a minute ago and sent to root ?

you have installed sendmail, you could telnet to localhost and you sent a mail which you said worked so whats wrong with the MAIL command ?

as for sending to externally you will need to edit a file (i cant remember which offhand) to send mail externally as  by default it does not allow relaying

this will set it up for external relaying [http://www.recital.com/index.php?option=com_content&view=article&id=71%3Ahowto-configure-linux-sendmail-to-use-external-isp-as-smtp-mail-relay&Itemid=59](http://www.recital.com/index.php?option=com_content&view=article&id=71%3Ahowto-configure-linux-sendmail-to-use-external-isp-as-smtp-mail-relay&Itemid=59)

But I SHOULDN'T have to edit a file.  I'm just confused because all my friend did was download "mail" and it worked perfectly, nothing wrong.  I had to use mail like a year ago for a project and it worked fine, I've never edited any files and it sent emails externally.

---

### Post by haqking on 2011-08-05
> **bneva said:**
> yea I attached a file but it still isn't working.

mail -s "foo" "email@gmail.com" < text.txt

you need to be clearer about what you are asking.

you first were typing lower case which i told you about, you then asked about ehlo, i explained.

then you said what about the MAIL command ?

now its about file attachments ?

you said an email sent ok to root ?

so its working correct ?

the current problem is you want to add an attachemt ? is this correct ?

and you want to send to an external email ? is this also correct ? if so then you need to change configuration as i stated

---

### Post by haqking on 2011-08-05
> **bneva said:**
> But I SHOULDN'T have to edit a file.  I'm just confused because all my friend did was download "mail" and it worked perfectly, nothing wrong.  I had to use mail like a year ago for a project and it worked fine, I've never edited any files and it sent emails externally.


ok upload a screen dump of what you are typing and the error you are getting

---

### Post by bneva on 2011-08-05
Ok my question is this..........

I download "heirloom-mailx" and "sendmail" because as far as I know, mail and sendmail are 2 different things.

I simply googled examples and was using this as my example

```
mail -s "hello" email@gmail.com
```

I also tried putting the email in quotations but that didn't work either.

My question originally was, why is this not sending to my gmail account?

.............
Additional Info

My friend who is doing the same thing basically all he did was download "mail" not "heirloom-mailx" but just "mail"  I don't see any package using apt-get install mail.  For him, everything worked fine.  For me though, nothing works.

To reply to your last post....

I don't get any error messages, nothing happens.  I get the message "EOT" after I press ctrl D and then no email is even sent.

---

### Post by haqking on 2011-08-05
> **bneva said:**
> Ok my question is this..........

I download "heirloom-mailx" and "sendmail" because as far as I know, mail and sendmail are 2 different things.

I simply googled examples and was using this as my example

```
mail -s "hello" email@gmail.com
```I also tried putting the email in quotations but that didn't work either.

My question originally was, why is this not sending to my gmail account?

.............
Additional Info

My friend who is doing the same thing basically all he did was download "mail" not "heirloom-mailx" but just "mail"  I don't see any package using apt-get install mail.  For him, everything worked fine.  For me though, nothing works.

To reply to your last post....

I don't get any error messages, nothing happens.  I get the message "EOT" after I press ctrl D and then no email is even sent.

ok so your format it correct and you are getting no error messages ?

it just doesnt arrive in your inbox ? have you checked your spam ?

---

### Post by bneva on 2011-08-05
> **haqking said:**
> ok so your format it correct and you are getting no error messages ?

it just doesnt arrive in your inbox ? have you checked your spam ?

yes there is no error message, everything seems fine but nothing arrives at my inbox.  There is nothing in my spam folder.  I tried hotmail and gmail

---

### Post by bneva on 2011-08-05
just to show you what I mean

---

### Post by haqking on 2011-08-05
> **bneva said:**
> yes there is no error message, everything seems fine but nothing arrives at my inbox.  There is nothing in my spam folder.  I tried hotmail and gmail


ok so i just tried it on a virtual machine of mine and worked fine, i did the following:

sudo apt-get install sendmail

this installed then from prompt i typed:

**mail -s “Hello” [email]myemail@gmail.com[/email]** and hit enter
this is a test message (i yped this on the new line afer hitting enter) ctrl+d
cc: ctrl+d
 

then i checked my mailbox and it arived into evolution where i pick up my mail

---

### Post by bneva on 2011-08-05
> **haqking said:**
> ok so i just tried it on a virtual machine of mine and worked fine, i did the following:

sudo apt-get install sendmail

this installed then from prompt i typed:

**mail -s &#8220;Hello&#8221; [email]myemail@gmail.com[/email]** and hit enter
this is a test message (i yped this on the new line afer hitting enter) ctrl+d
cc: ctrl+d
 

then i checked my mailbox and it arived into evolution where i pick up my mail

ok I went sudo apt-get remove heirloom-mailx and sendmail....

I only reinstalled sendmail

sudo apt-get install sendmail

when I type mail -s &#8220;Hello&#8221; [email]myemail@gmail.com[/email] and press enter

"/usr/bin/mail: No such file or directory"

this is driving me nuts lol I always have stupid problems like this.

---

### Post by haqking on 2011-08-05
> **bneva said:**
> ok I went sudo apt-get remove heirloom-mailx and sendmail....

I only reinstalled sendmail

sudo apt-get install sendmail

when I type mail -s “Hello” [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL] and press enter

"/usr/bin/mail: No such file or directory"

this is driving me nuts lol I always have stupid problems like this.

ok so in terminal type:

cd /usr/bin

then do a 

ls

to see if mail is  present in the list

if not then i would restart machine to clear things out and do a reinstall of sendmail

try ccleaning the other thing you instaled with synaptic

---

### Post by bneva on 2011-08-05
> **haqking said:**
> ok so in terminal type:

cd /usr/bin

then do a 

ls

to see if mail is  present in the list

if not then i would restart machine to clear things out and do a reinstall of sendmail

try ccleaning the other thing you instaled with synaptic

Alright I removed all the sendmail things with synaptic, restarted, and sudo apt-get install sendmail.

Now when I type the mail command I get this
```
brendan@bneva:~$ mail
The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: sudo apt-get install <selected package>

```

what should I do?

---

### Post by bneva on 2011-08-05
anyone else?

---

### Post by haqking on 2011-08-06
> **bneva said:**
> anyone else?

ok so type the full mail syntax as before to send an email ?

---

### Post by bneva on 2011-08-06
> **haqking said:**
> ok so type the full mail syntax as before to send an email ?

it says the same thing if I do the whole command, it's like mail doesn't even get installed.  

I actually managed to get ONE email out of the like 50 times I tried but I didn't even realize it until an hour or two later so I have no clue which one I actually typed.

---

### Post by haqking on 2011-08-06
> **bneva said:**
> it says the same thing if I do the whole command, it's like mail doesn't even get installed.  

I actually managed to get ONE email out of the like 50 times I tried but I didn't even realize it until an hour or two later so I have no clue which one I actually typed.

well they can often take a long time with this method, you might find a full Inbox over the next few days...LOL

so use synpatic to make sure sendmail and all its dependencies are installed correctly.

and can you still telnet to localhost 25, is the MTA still running in your processes ?

---

### Post by bneva on 2011-08-06
> **haqking said:**
> well they can often take a long time with this method, you might find a full Inbox over the next few days...LOL

so use synpatic to make sure sendmail and all its dependencies are installed correctly.

and can you still telnet to localhost 25, is the MTA still running in your processes ?

yea I figured when I woke up this morning I would see a ton of emails but unfortunately not lol  I'll try uninstalling and reinstalling send mail one more time when I get home from work

Thanks for tryin to help me!

---

### Post by haqking on 2011-08-06
> **bneva said:**
> yea I figured when I woke up this morning I would see a ton of emails but unfortunately not lol  I'll try uninstalling and reinstalling send mail one more time when I get home from work

Thanks for tryin to help me!

no problems, sounds like there is a configuration issue due to removal now.

It was working somewhere along the line so.......

---

### Post by SeijiSensei on 2011-08-06
Yes, you need to install heirloom-mailx to get the mail command.

With both it and sendmail installed, the default configuration ought to allow you send a message like this:

```
echo 'this is a test' | mail -s test you@example.com
```

If you don't receive the message at [email]you@example.com[/email], there are a variety of possible reasons for this, most of them having to do with SMTP issues and spam filtering.

1)  Your ISP may not allow you to send mail directly to other servers over SMTP (port 25).  To test for this, try connecting directly to Google's inbound server like this:

```
telnet gmail-smtp-in.l.google.com 25
```

If the connection times out, your ISP is probably blocking outbound port 25.  They might offer you the option of relaying the mail through one of their servers, but they might not accept mail for relaying using From addresses not within the ISP's domain.  So you might be able to use addresses like "me@myisp.com" but not "me@example.com" where the latter is some arbitrary domain.

2)  Messages sent from your machine may not have a fully-qualified domain name or otherwise look suspicious.  What is the result of the "hostname" command?  Do you have a FQDN like "natasha.example.com", or just a hostname like "natasha"?  If the latter, the mail will be addressed as from "you@natasha".  Most SMTP servers won't accept that.  If you are using a domain, is it legitimately registered with a DNS registrar?

In all of this, your best friend is /var/log/mail.log.  It will report whatever problems sendmail is encountering.  See what it says.

---

### Post by haqking on 2011-08-06
> **SeijiSensei said:**
> Yes, you need to install heirloom-mailx to get the mail command.

With both it and sendmail installed, the default configuration ought to allow you send a message like this:

```
echo 'this is a test' | mail -s test you@example.com
```If you don't receive the message at [EMAIL="you@example.com"]you@example.com[/EMAIL], there are a variety of possible reasons for this, most of them having to do with SMTP issues and spam filtering.

1)  Your ISP may not allow you to send mail directly to other servers over SMTP (port 25).  To test for this, try connecting directly to Google's inbound server like this:

```
telnet gmail-smtp-in.l.google.com 25
```If the connection times out, your ISP is probably blocking outbound port 25.  They might offer you the option of relaying the mail through one of their servers, but they might not accept mail for relaying using From addresses not within the ISP's domain.  So you might be able to use addresses like "me@myisp.com" but not "me@example.com" where the latter is some arbitrary domain.

2)  Messages sent from your machine may not have a fully-qualified domain name or otherwise look suspicious.  What is the result of the "hostname" command?  Do you have a FQDN like "natasha.example.com", or just a hostname like "natasha"?  If the latter, the mail will be addressed as from "you@natasha".  Most SMTP servers won't accept that.  If you are using a domain, is it legitimately registered with a DNS registrar?

In all of this, your best friend is /var/log/mail.log.  It will report whatever problems sendmail is encountering.  See what it says.

When i origainlly responded to his question he had heirloom mailx

I dont have heirloom mailx, as stated previously i just added sendmail and then issued the mail command locally and it worked and via telnet.

He also did at one point have mailx and the local mail to root worked. and one email he sent did arrive so ISP is not blocking.

---

### Post by SeijiSensei on 2011-08-06
> **haqking said:**
> When i origainlly responded to his question he had heirloom mailx

I dont have heirloom mailx, as stated previously i just added sendmail and then issued the mail command locally and it worked and via telnet.

He also did at one point have mailx and the local mail to root worked. and one email he sent did arrive so ISP is not blocking.

In general, I still think it's important to tell people to use logs in diagnosis.  Too many people here seem unaware at how many logs are created and how useful they can be.  (People coming from Windows are probably especially unaware of the existence or value of logs.)  Seeing a few lines from /var/log/mail.log in response to a failed message can be enormously helpful and eliminates the need to guess where the problem might lie.

---

### Post by bneva on 2011-08-06
when I look at /var/log/mail.err I see this

```
Aug  6 14:05:04 bneva sendmail[2201]: unable to qualify my own domain name (bneva) -- using short name

```

and in var/log/mail.log I see this:
```
Aug  6 14:05:04 bneva sendmail[2201]: unable to qualify my own domain name (bneva) -- using short name
Aug  6 14:05:04 bneva sendmail[2201]: p76L54fr002201: from=root, size=234, class=0, nrcpts=1, msgid=<201108062105.p76L54fr002201@bneva>, relay=root@localhost
Aug  6 14:05:05 bneva sm-mta[2218]: p76L545R002218: from=<root@bneva>, size=455, class=0, nrcpts=1, msgid=<201108062105.p76L54fr002201@bneva>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Aug  6 14:05:05 bneva sendmail[2201]: p76L54fr002201: to=*****************@hotmail.com, ctladdr=root (0/0), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30234, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p76L545R002218 Message accepted for delivery)

```

I'm just confused because one of my emails actually went through, which is weird.  I did try telnet into gmail and it didn't work and I googled around and I guess my provider does block port 25

---

### Post by SeijiSensei on 2011-08-06
> **bneva said:**
> I'm just confused because one of my emails actually went through, which is weird.  I did try telnet into gmail and it didn't work and I googled around and I guess my provider does block port 25

No, that's just the local server confirming that it received the message.  If you look in /var/spool/mqueue, I'll bet you'll see a bunch of files starting with qf and df.  If so, they're queued for delivery by sendmail because they couldn't reach their destinations.  The qf* files are headers; the df* files contain the message bodies.

A message accepted by an external SMTP server will generate a log entry like this:

```
Aug  6 13:02:51 hostname sendmail[6907]: p76H2nDr006907: to=<xxx@example.com>, delay=00:00:02, xdelay=00:00:01, mailer=esmtp, pri=41845, relay=mail.example.com. [10.10.10.10], dsn=2.0.0, stat=Sent (Ok: queued as 696A08604C)
```

You'll see the remote domain's MX hostname and IP address instead of "mail.example.com" and "10.10.10.10".

---

### Post by bneva on 2011-08-06
what I mean is, I got an email in my hotmail inbox, well junk folder from root@localhost.  Only ONE though out of many many tries.  That is what confuses me, it worked once, but never again.  I didn't even realize I had the email until several hours after because it showed up in my junk folder.

edit I just tried it again and in my /var/log/mail.log

```
Aug  6 20:48:20 bneva sendmail[2146]: p773mKcx002146: to=***********@hotmail.com, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30232, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p773mKDF002187 Message accepted for delivery)
```

---

### Post by SeijiSensei on 2011-08-07
> **bneva said:**
> what I mean is, I got an email in my hotmail inbox, well junk folder from root@localhost.  Only ONE though out of many many tries.  That is what confuses me, it worked once, but never again.  I didn't even realize I had the email until several hours after because it showed up in my junk folder.

edit I just tried it again and in my /var/log/mail.log

```
Aug  6 20:48:20 bneva sendmail[2146]: p773mKcx002146: to=***********@hotmail.com, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30232, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p773mKDF002187 Message accepted for delivery)
```

Once again, that log entry is from the instance of sendmail running on the localhost interface with address 127.0.0.1 confirming that it received the message.  What you haven't shown us is an equivalent log entry with the relay= field containing the name and address of a server at hotmail, not 127.0.0.1.

---

### Post by bneva on 2011-08-07
> **SeijiSensei said:**
> Once again, that log entry is from the instance of sendmail running on the localhost interface with address 127.0.0.1 confirming that it received the message.  What you haven't shown us is an equivalent log entry with the relay= field containing the name and address of a server at hotmail, not 127.0.0.1.

how about this one

```
Aug  5 20:37:24 bneva sm-mta[3457]: p7606Kc7002749: to=<*******@hotmail.com>, ctladdr=<root@bneva> (0/0), delay=03:31:04, xdelay=01:38:01, mailer=esmtp, pri=120445, relay=mx1.hotmail.com. [65.54.188.72], dsn=2.0.0, stat=Sent ( <201108060006.p7606KqP002736@bneva> Queued mail for delivery)
```

20:37, also being the time I received the email

---

### Post by SeijiSensei on 2011-08-07
Yes, that's what you want to see.

I'm a bit surprised you could use a From address with no domain part and have it accepted by HotMail.  (That's a big security and spam problem in my mind.)  It looks like the server only has a hostname ("bneva") but not a fully-qualified name like "bneva.example.com".  My incoming server would probably reject your message depending on what happened in the SMTP exchange, and even if it were accepted, it would probably get a high spam score from my scanner.

---

### Post by bneva on 2011-08-08
> **SeijiSensei said:**
> Yes, that's what you want to see.

I'm a bit surprised you could use a From address with no domain part and have it accepted by HotMail.  (That's a big security and spam problem in my mind.)  It looks like the server only has a hostname ("bneva") but not a fully-qualified name like "bneva.example.com".  My incoming server would probably reject your message depending on what happened in the SMTP exchange, and even if it were accepted, it would probably get a high spam score from my scanner.

yea but why did it only work once? that's what confused me.  I've done it a countless number of times, but only the 1 time actually worked, weird.  Maybe I will just have to try a ton of different combos to see what works.

---

### Post by bneva on 2011-08-11
So is there a way around this somehow?

---

### Post by bneva on 2011-08-14
anyone?  Is there a way around my ISP blocking port 25?

---

### Post by bneva on 2011-08-14
sorry for bumping this so many times, just trying to figure out a solution!

---

### Post by alphacrucis2 on 2011-08-14
> **bneva said:**
> sorry for bumping this so many times, just trying to figure out a solution!

Ask your ISP. They will probably say no, as if you started spamming they could get their ip address block blacklisted. I'm not saying that you would generate spam but your ISP would be taking a risk.

---

### Post by bneva on 2011-08-20
OK an update...

My friend who I talked about before also has the same ISP but his mail works.  So I don't know what is going on now.

---

### Post by bneva on 2011-08-22
sorry for so many bumps again!

---

