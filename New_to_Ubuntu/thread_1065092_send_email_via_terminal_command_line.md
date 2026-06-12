---
title: "send email via terminal/ command line"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by hanzj on 2009-02-09
I have a gmail account. I send and receive email via the web version (opening up firefox and going to [www.gmail.com]("http://www.gmail.com")). But I have to be able to send email via the Terminal / Command Line. How can I go about doing this? I just need this for a few weeks, so I don't care if things look ugly. I do NOT need to read email. I just need to do the following:


 send emails VIA terminal to 2 particular email address (abc@gmail.com AND [EMAIL="9392037433@mycellphonecompany.com"]9392037433@mycellphonecompany.com[/EMAIL]) at the same time  in one command line.
Be able to give the emails a subject line
be able to givet he emails a very short 1-5 word body for an email.


I need to send email ALL in one command line. (Because it will be triggered by the computer, and I won't be arround to answer yes/no questions or to hit the enter key)
So if you can help, please reply and tell me what I need to install and do.


Thanks!!!!!

---

### Post by Cl0ud9 on 2009-02-09
I get the sense you are not looking for a full email client. I can't help you with that, but I can point you toward [alpine]("http://www.washington.edu/alpine/") which is a great terminal email client which I use with my gmail account. It should be available in the repos.

---

### Post by pers3vs on 2009-02-09
sudo apt-get install sendmail

---

### Post by hanzj on 2009-02-09
after installing sendmail, then what? and will it work with Gmail (google mail)?

---

### Post by Nepherte on 2009-02-10
The first idea that comes to mind is to telnet into the google smtp server and type some smtp commands to compose and send your mail...on second thought a command line mail client might be better suited though..

---

### Post by brian_p on 2009-02-10
> **hanzj said:**
> 
)
So if you can help, please reply and tell me what I need to install and do.

Ideal for your needs:

```
sudo apt-get install sendemail
```

Worked with my gmail account a few minutes ago.

---

### Post by Neural oD on 2009-02-10
> **hanzj said:**
> after installing sendmail, then what? and will it work with Gmail (google mail)?

Have a look at the man pages for sendmail - hopefully it will point u in the right direction ;)

---

### Post by hanzj on 2009-02-10
> **brian_p said:**
> Ideal for your needs:

```
sudo apt-get install sendemail
```Worked with my gmail account a few minutes ago.
Dear brian_p,

thanks for suggestion. I've just installed sendemail. could you tell me how to make it work with my gmail account? 

Thanks!!!!

---

### Post by hanzj on 2009-02-10
By the way, I need a program that can send an email all in one command line. This is because a program will be the one that triggers this. In other words, I will not be in front of the computer to move on to the next prompt or blank. 

Will sendemail allow this?

by the way, with sendemail, I tried this:
> sendEmail -f [email]bob@bob.com[/email] -t [email]sue@sue.com[/email] -m howdy
Feb 10 15:17:29 ha-desktop sendEmail[7315]: ERROR => Connection attempt to localhost:25 failed: IO::Socket::INET: connect: Connection refused

---

### Post by speedman on 2009-02-10
You need to specify a SMTP relay host.

Cheers,

Chris

---

### Post by hanzj on 2009-02-10
how do i specify a smtp relay host within sendemail?

I see in the help file:
> 

-s SERVER[:PORT]          smtp mail relay, default is localhost:25according to [http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287), here's the SMTP info:
> [SIZE=-1]**Outgoing Mail (SMTP) Server - requires TLS:**[/SIZE]   [FONT=Courier New, Courier, mono][SIZE=-1]smtp.gmail.com[/SIZE][/FONT][SIZE=-1] (use authentication)
        **Use Authentication**: Yes
        **Use STARTTLS**: Yes (some clients call this SSL)
  **Port**: 465 or 587 [/SIZE]So, I then tried this:

> sendEmail -f [EMAIL="mygmailaccount@gmail.com"]mygmailaccount@gmail.com[/EMAIL] -s smtp.gmail.com:465 -xu [EMAIL="mygmailaccount@gmail.com"]mygmailaccount@gmail.com[/EMAIL] -xp mypasswordgoeshere -t [EMAIL="targetemail@mail.com"]targetemail@mail.com[/EMAIL] -o tls=yes -m howdy
I then got this:
> 
 sendEmail[7452]: ERROR => No TLS support!  SendEmail can't load required libraries. (try installing Net::SSLeay and IO::Socket::SSL)
So should I install both Net::... and IO::... files? I thought sendemail is a simple standalone email program? Am I mistaken?

Anyway, I tried installing both. but I got some error messages:

> haha@ha-desktop:~$ sudo apt-get install Net::SSLeay
[sudo] password for haha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Net::SSLeay
haha@ha-desktop:~$ sudo apt-get install IO::Socket::SSL
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package IO::Socket::SSL

thanks!!!

---

### Post by speedman on 2009-02-10
apt-cache search perl|grep ssl

That will show you perl packages available in your version of Ubuntu for SSL support. Install them and you should be good to go.

I would check for you, but I don't have any Ubuntu boxes handy.

Cheers,

Chris

---

### Post by hanzj on 2009-02-10
I did the grep command.
Which of the ff should I install? ( I have already installed  libnet-ssleay-perl)  Thanks.
> libcrypt-openssl-bignum-perl - Access OpenSSL multiprecision integer arithmetic libraries
libcrypt-openssl-random-perl - Access to the OpenSSL pseudo-random number generator
libcrypt-openssl-rsa-perl - Perl module providing basic RSA functionality
libio-socket-ssl-perl - Perl module implementing object oriented interface to SSL sockets
libnet-ssleay-perl - Perl module for Secure Sockets Layer (SSL)
libcrypt-openssl-dsa-perl - Module which implements the DSA signature verification system
libcrypt-openssl-x509-perl - Perl extension to OpenSSL's X509 API
libcrypt-ssleay-perl - Support for https protocol in LWP
libhttp-daemon-ssl-perl - A simple HTTP server class with SSL support
libnet-imap-simple-ssl-perl - Subclass of Net::IMAP::Simple with SSL support
libnet-smtp-ssl-perl - SSL support for Net::SMTP
libpoe-component-sslify-perl - abstracts SSL connections for other POE components
libxml-rsslite-perl - Lightweight, "relaxed" RSS (and XML-ish) parser


---

### Post by ByteJuggler on 2009-02-10
> **hanzj said:**
> I did the grep command.
Which of the ff should I install? ( I have already installed  libnet-ssleay-perl)  Thanks.

Probably: libio-socket-ssl-perl - Perl module implementing object oriented interface to SSL sockets

---

### Post by hanzj on 2009-02-10
I've just installed libio-socket-ssl-perl  

Now I get a "Segmentation fault" error after running the sendEmail command. Should I give up? 8-)

---

### Post by brian_p on 2009-02-10
> **hanzj said:**
> how do i specify a smtp relay host within sendemail?

One solution (there is another one) is to use your ISP's smtp server instead of trying to send through gmail's server.

```
sendEmail -f mygmailaccount@gmail.com -s smtp_server_at_your_isp.com -t targetemail@mail.com -m howdy
```

---

### Post by brian_p on 2009-02-10
> **hanzj said:**
> By the way, I need a program that can send an email all in one command line. This is because a program will be the one that triggers this. In other words, I will not be in front of the computer to move on to the next prompt or blank. 

Will sendemail allow this?

Put the sendEmail commands in a script and have cron run it.

---

### Post by ByteJuggler on 2009-02-10
> **brian_p said:**
> One solution (there is another one) is to use your ISP's smtp server instead of trying to send through gmail's server.

```
sendEmail -f mygmailaccount@gmail.com -s smtp_server_at_your_isp.com -t targetemail@mail.com -m howdy
```

That's probably a very good idea as google probably won't relay for you anyway, so is only good for sending mail to google addresses.

---

### Post by hanzj on 2009-02-10
brian_p, using my ISP's mail server is a success.
Thanks. 
Just wondering, what is other solutions?
(is it really very hard to get gmail to work with sendemail?)

Thank you everybody.

---

### Post by brian_p on 2009-02-11
> **hanzj said:**
> 

Just wondering, what is other solutions?
(is it really very hard to get gmail to work with sendemail?)

You require a Mail Transport Agent (MTA) to handle the mail sent.

Your ISP has an MTA. This works for you because you are at home and on the same network - you can be authenticated.

Google has an MTA. If you can authenticate to it you can get it to send mail to any domain for you. sendEmail v1.54 or higher is needed.

```
sudo apt-get install libnet-ssleay-perl libio-socket-ssl-perl
```

[INDENT]-s  smtp.gmail.com
-xu username_for_Google
-xp password_at_Google[/INDENT]

You can run your own MTA, which is what I do.

```
sudo apt-get install exim4
```

To alter its configuration:

```
sudo dpkg-reconfigure exim4-config
```

---

### Post by brian_p on 2009-02-11
> **hanzj said:**
> 

(is it really very hard to get gmail to work with sendemail?)


I forgot:

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

---

### Post by ByteJuggler on 2009-02-11
> **brian_p said:**
> 
You can run your own MTA, which is what I do.

```
sudo apt-get install exim4
```

To alter its configuration:

```
sudo dpkg-reconfigure exim4-config
```

Sorry for asking a lazy question -- how easy is exim to configure and so on?  I do the same as you (run my own MTA) but use postfix instead.  It took me a while to get fully working as I enabled TLS/authentication etc as I recall and had to mess about with certificates and things... wasn't exactly noob friendly, which is why I didn't suggest it.  Is exim config substantially easier?

---

### Post by brian_p on 2009-02-12
> **ByteJuggler said:**
> 

Is exim config substantially easier?

I've never used postfix. Setting up basic sending and receiving of mail with exim4 was easy enough but authentication was something I didn't need so I do not know how involved it is.

---

### Post by nhandler on 2009-02-13
I had this same problem a while ago. I wanted to automate the sending of emails. In the end, I ended up configuring mutt to work with my gmail account. Mutt is a full CLI email client. However, it also supports sending emails with one command (and no prompts). You can try following [this]("http://shreevatsa.wordpress.com/2007/07/31/using-gmail-with-mutt-the-minimal-way/") guide to get it working. If it doesn't work, let me know. I am not positive which guide I used to get mutt working nicely with gmail.

---

### Post by PhrankDaChickenGeek on 2009-02-14
Sweetness - I've got this working with Mutt
```
 sudo apt-get install mutt
```

Edit and add this to your ~/.muttrc file:
```

set imap_user = "username@gmail.com"
set imap_pass = "password"

set smtp_url = "smtp://username@smtp.gmail.com:587/"
set smtp_pass = "password"
set from = "username@gmail.com"
set realname = "Your Real Name"

set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"

set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates

set move = no

```

Start mutt once and send a message, setting accepting certificates to "always"

Then you can send a message via the command line:
```
echo "Message body" | mutt -s "Subject" phonenumber@carrier.com
```

---

### Post by hanzj on 2009-02-15
Phrank,
Thanks for your How-To-Send-Gmail-via-Mutt post. I've been able to send email via command line using sendEmail and with my ISP's mail server. If ever I need to do gmail via command line, I'll try your method.

---

### Post by spikenick on 2009-03-11
it doesn't appear to but as a desktop user does installing mutt and exim4 provide any firewall holes?

---

### Post by ByteJuggler on 2009-03-11
> **spikenick said:**
> it doesn't appear to but as a desktop user does installing mutt and exim4 provide any firewall holes?

mutt is a client user/application so does not in and of itself open any ports.  The only time it will do network I/O is when you as user run it.  exim4 however is an MTA (mail service) so will, depending on configuration listen on port 25 or others for SMTP and other requests.  While that in and of itself has no direct firewall implications, it means that its another avenue of attack for people to target, it isn't one I'd be particularly worried about though.  Nevertheless, something to factor in, since you asked.  You can of course then lock down access to this port/service using firewall rules (or a dedicated firewall e.g. one in your router, presuming you're using a router.)  (Or you of course also keep the service stopped/disabled and only run it when needed, although typically if you're actually running it as a proper mailserver it would need to run permanently, or at least be contactable permanently via e.g. inetd, in order to receive mail and so on when other mail hosts has mail for your domain.)

---

