---
title: "EASY tutorial for sending email to gmail account"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by fixnodecomputer on 2011-03-21
Ok so after about 18 hours non stop reading tutorials online I finally decided to post online for help.
 
Here is my situation:
 
I need to setup email service in ubuntu server edition that uses my gmail account to send email (actually I don't care how I send email as long as it goes to ANY external email account on the internet) all I need is to send email not recieve email.
 
The reason I need this is so I can create an perl script to send an email to my phone when someone connects to my VNC repeater.
 
I looked at hundreds of tutorials on how to setup CA certificate and how to relay emails etc.. NONE WORK!!!!
 
I'm new to Ubuntu, Ive been using it for 3 months now (even though I grew up on mac) and desperatly need help!
 
I setup everything else with no problem (vnc repeater, apache, ftp, bind) but I can't get mail to work
 
I've tried postfix,sendmail,qmail, etc probably 6 different mail servers with no avail.
 
Please Help and give me a noob tutorial (step by step) on how to send email!
 
Thanks in Advance!.
Phillip K
 
 
P.S. assume that my ISP does not supply me with SMTP server, if needed let me know how to [FONT=Calibri]Reverse all my changes that I have done to default. running ubuntu 10.10 server edition[/FONT]

---

### Post by lmarmisa on 2011-03-21
You can see here the outgoing mail configuration for sending messages to Gmail:

[http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)

Check this other link too:

[http://stackoverflow.com/questions/560491/how-do-i-send-email-to-my-gmail-account-using-smtp-and-perl](http://stackoverflow.com/questions/560491/how-do-i-send-email-to-my-gmail-account-using-smtp-and-perl)

---

### Post by Stephen Morgan on 2011-03-21
So all you want is to send a mail message from the command line or a script via the gmail SMTP server, yes?

Well, I can't help you to get postfix or sendmail working, but if you install msmtp, that'll send the mail for you. ssmtp would do the job too, but that would replace postfix which you might not want to do, but it does work with gmail.

For msmtp, you just need a ~/.msmtprc set up like this:

```
#Gmail account
defaults
logfile ~/msmtp.log

account gmail
auth on
host smtp.gmail.com
from @gmail.com
auth on
tls on
# tls_trust_file /etc/ssl/cert.pem
tls_trust_file /usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt
user @gmail.com
password passwd
port 587

account default : gmail

```Put your details in, of course.

Then add ```
 set sendmail="/usr/bin/msmtp"
 set message-sendmail-extra-arguments="-a gmail"

```to ~/.mailrc

After that just use the mailx command (might have to install heirloom-mailx for that) in the normal way, `mail -s "subject" person@address < message.txt`

---

### Post by fixnodecomputer on 2011-03-21
> **Stephen Morgan said:**
> So all you want is to send a mail message from the command line or a script via the gmail SMTP server, yes?
 
Well, I can't help you to get postfix or sendmail working, but if you install msmtp, that'll send the mail for you. ssmtp would do the job too, but that would replace postfix which you might not want to do, but it does work with gmail.
 
For msmtp, you just need a ~/.msmtprc set up like this:
 
```
#Gmail account
defaults
logfile ~/msmtp.log
 
account gmail
auth on
host smtp.gmail.com
from @gmail.com
auth on
tls on
# tls_trust_file /etc/ssl/cert.pem
tls_trust_file /usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt
user @gmail.com
password passwd
port 587
 
account default : gmail

```Put your details in, of course.
 
Then add ```
 set sendmail="/usr/bin/msmtp"
 set message-sendmail-extra-arguments="-a gmail"

```to ~/.mailrc
 
After that just use the mailx command (might have to install heirloom-mailx for that) in the normal way, `mail -s "subject" person@address < message.txt`
 
 
So hold on, I installed msmtp, you want me to create a file in ~ that is called "msmtprc"? put in all that information above? and then create a second file in ~ called "mailrc" and put  ```
 set sendmail="/usr/bin/msmtp"
 set message-sendmail-extra-arguments="-a gmail"

``` into it? is that about right??
 
Thanks for reply, sorry your pretty much talking to a noob when it comes to CLI

---

### Post by Stephen Morgan on 2011-03-21
> **fixnodecomputer said:**
> Thanks for reply, sorry your pretty much talking to a noob when it comes to CLI

That's alright, we've all been there. The files to create are .msmtprc and .mailrc, with the dots in front. Put them in ~/, which is to say in your home directory, /home/username. .msmtprc is read by msmtp for your account information, .mailrc is read by mailx for which programme to use to send mail. 

The mail command will then use msmtp to send via the smtp server specified in .msmtprc

And don't forget to replace @gmail.com with your address and username and passwd with your password

---

### Post by fixnodecomputer on 2011-03-21
> **Stephen Morgan said:**
> That's alright, we've all been there. The files to create are .msmtprc and .mailrc, with the dots in front. Put them in ~/, which is to say in your home directory, /home/username. .msmtprc is read by msmtp for your account information, .mailrc is read by mailx for which programme to use to send mail. 
 
The mail command will then use msmtp to send via the smtp server specified in .msmtprc
 
And don't forget to replace @gmail.com with your address and username and passwd with your password
 
 
THANK YOU!!!! YOU  ARE A GUINNESS!!!, I've spent all night trying to figure this out! (3 red bulls in from last night) and now it works :D... all I need to do is create a perl script that will email me when my vnc repeater gets a connection (easy work)
 
Thanks Again,
Phillip K

---

