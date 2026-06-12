---
title: "Sudden SMTP Error on Thunderbird"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Xalltar on 2011-04-26
Hello to all.

I've just got a strange problem on thunderbird.
I was using it and it worked like a charm when suddently (I had done nothing special), I got the error :

Sending of message failed.
The message could not be sent because connecting to SMTP server smtp.live.com failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server settings are correct and try again, or contact the server administrator.

On sending an email.
And everything works with evolution !!!

Can anyone help me ?

---

### Post by Dondermans on 2011-04-26
Are you able to rule out a temporary loss of your connection to the internet?

---

### Post by Xalltar on 2011-04-26
?? I don't really understand what you mean ...

How can I test if I can ?

---

### Post by Rex Bouwense on 2011-04-26
He means can you send the email now.  It is possible that at the instant you were sending your email before, Thunderbird could not connect.  It happens.  Just wait a minute and try to send it again.

---

### Post by Xalltar on 2011-04-26
No no i've been trying since yesterday noon. I've got my night on google searching (this is a common problem I think), i've remove thunderbird, reinstalled, deleted the passwords, deleted all the accounts. The only thing i haven't tried is removing and reinstalling Ubuntu ...

I've mixed every configuration possible for SMTP servers in thunderbird (pass, ports, encryption type ...). I wouldn't have posted if the solution was so easy :)

Maybe it's something i've done inbetween sending those mails but I can't see what ...

Here are my accounts' settings :

smtp.live.com port 587 (tried 25 and 465)
Connection : STATTLS (tried everyone mixed with port)
Normal Password
[EMAIL="xxxxx@hotmail.fr"]xxxxx@hotmail.fr[/EMAIL]

---

### Post by Dondermans on 2011-04-26
> **Xalltar said:**
> ?? I don't really understand what you mean ...

How can I test if I can ?

[QUOTE=Rex Bouwense;10722777]He means can you send the email now.  It is  possible that at the instant you were sending your email before,  Thunderbird could not connect.  It happens.  Just wait a minute and try  to send it again.[/QUOTE]

Rex Bouwense is correct. Because you were able to send e-mail using Evolution it is  possible that you were temporarily disconnected from the internet when  trying to send mail using Thunderbird.

The error you got stated:```
Sending of message failed.
The message could not be sent because connecting to SMTP server smtp.live.com failed. 
The server may be unavailable or is refusing SMTP connections.
```Are you still unable to send mail using thunderbird? If so, have you compared Thunderbird's settings to the settings in Evolution? [_This Mozillazine page_]("http://kb.mozillazine.org/Connection_errors_-_SMTP") might be an interesting read as it pertains to your error.

---

### Post by Xalltar on 2011-04-26
I've already checked out this webpage in fact ..

If I compare with evolution I'm on port 25 with TLS encryption (with evolution).

I then get :

An error occurred while sending mail. The mail server responded:  5.3.4 Requested action not taken; To continue sending messages, please sign in to your account.. Please check the message and try again.

Erf ?? Stuck on status "Delivering Mail".

My UFW firewall is disabled ... in case of ...

The configuration that worked was port 587 with STARTTLS ... odd ... cuz port 587 doesn't work with evolution

---

### Post by Dondermans on 2011-04-26
> **Xalltar said:**
> I've already checked out this webpage in fact ..

If I compare with evolution I'm on port 25 with TLS encryption (with evolution).

I then get :

An error occurred while sending mail. The mail server responded:  5.3.4 Requested action not taken; To continue sending messages, please sign in to your account.. Please check the message and try again.

Erf ?? Stuck on status "Delivering Mail".

My UFW firewall is disabled ... in case of ...

The configuration that worked was port 587 with STARTTLS ... odd ... cuz port 587 doesn't work with evolution

Alright. I happen to use Thunderbird as well (version 3.1.8). I created a hotmail account and had Thunderbird configure the SMTP-settings automatically. I took screenshots of the settings. I've tested these settings successfully by sending an e-mail from my Hotmail-account to another e-mailaddress using the live.com SMTP server.

Perhaps you could try these settings as well and let us know if this works for you?

---

### Post by Xalltar on 2011-04-26
Well, those are my settings already ...

I've deleted the account and tried to make a new one.

I've got the same informations exept that my adress is ".fr" and not ".com".

And ... nothing exept the same SMTP error ...

(No kidding)

However receiving messages works like a charm ...

---

### Post by Dondermans on 2011-04-26
Receiving messages is dependant on POP3, that's not related to SMTP.

Have you tried deleting any existing SMTP-servers in the 'Outgoing (SMTP) settings' window *before* creating a new account within Thunderbird (please view the attachment)?

I noticed upon deleting my temporary ubuntuforums[at]hotmail.com account that the associated SMTP-server was not deleted automatically. I suppose the reason is that I set it to 'Default' for testing purposes. Perhaps Thunderbird tries to access a SMTP-server using wrong parameters.

---

### Post by Xalltar on 2011-04-26
Hem .... evey other smtp server exept the one by default is removable.
There was only the default one when I tried creating my new account.

---

### Post by Dondermans on 2011-04-26
Were you able to have Thunderbird set the POP3 and SMTP settings automatically, as shown in [_message #8_]("http://ubuntuforums.org/showpost.php?p=10722931&postcount=8")? If so, did you set 'Microsoft Live Hotmail' as default SMTP-server in 'Outgoing Server (SMTP) Settings'?

If you tried these suggestions (and you still cannot send email) you could try the following:
You mentioned reinstalling Thunderbird. Did you also empty the ~/.thunderbird directory? It is hidden by default in your home directory. To display hidden files you need to press CTRL + h when viewing your home directory in your file browser.

I think reinstalling Thunderbird won't do any good if you left them  untouched. Your new installation will probably search for the (faulty)  settings in your home folder.

**[COLOR=Red]Caution: [/COLOR]**[COLOR=Red]this directory also contains any e-mails and rss-messages you might have stored on your computer. While emptying this directory *will* reset Thunderbird, you will also delete these messages permanently, unless you backup the files that contain said messages.[/COLOR]

---

### Post by Xalltar on 2011-04-26
Yup, automatics settings were never a problem

I must just precise i'm behind a squid type proxy, maybe it can help ?

In fact, I've tried to uninstall it with a

"Sudo apt-get remove thunderbird" but it ... crashed a bit, and stopped in the middle. I've fought for 15 minutes with those FU**** locks to remove with rm /opt/var/lock, sudo dpgk --configure -a and sudoIDon'tKnowWhatStuff etc ... commands .... but whatever ...

In the Synaptics package manager, when I tried to uninstall thunderbird ... it bugged.

So I just went into the folder and deleted the .thunderbird folder. Then I typed "Sudo apt-get install thunderbird" to reinstall and it worked.

But I think maybe thunderbird is not properly removed nor installed now ...
Is there any commande to "normally" remove somehting ?

However if it works it will still be strange cuz before it worked normally ...

I've remember I had some problem to remove LAMP to install XAMPP. Problems such as "another mail daemon is running".

I had to do 

dpkg -l *apache* *mysql* phpmyadmin | grep ^ii | awk '{ print $2}' | xargs sudo apt-get -y purge --auto-remove

Then

apt-get remove --purge apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert

And then XAMPP stopped displaying another daemon is running etc ... (BTW what does those commands mean ???)

So Maybe ....

But then i've sent mails without problems for some times ... then it begun to FU"""" crash SMTP server ...

So ... for a clean reinstall, what are the steps ?

I've searched the internet for hours, everybody who has that problem had never had any solution ... exept the "oh ! it suddently worked again" thing ...

EDIT : If someone has the interest of chatting with me to discuss of linux and tricks and so one that would be AWESOME ! I love linux since i've tested Ubuntu !

Re-EDIT / FU*** ^ 50 !! I've removed thunder with the synaptic packet manager (this time it worked), kicked out the folder in /home/ tried again .... same error (automatic configuration with thunder) !!! How frustrating !!!!

Re-EDIT : Also tryed as root ... with "sudo thunderbird"

---

### Post by Dondermans on 2011-04-26
I am afraid I do not have any other suggestions than the ones I provided.

---

### Post by hipodilski on 2012-07-17
I've experienced a similar error like the one you experience. I've figured out the problem is caused by DNS record issues. Check here for how I solved it - [http://www.pc-freak.net/blog/fixing-qmail-mail-server-smtp-auto-configure-issues-in-thunderbird-and-other-mail-imap-pop3-mobile-clients/](http://www.pc-freak.net/blog/fixing-qmail-mail-server-smtp-auto-configure-issues-in-thunderbird-and-other-mail-imap-pop3-mobile-clients/)

Best
Georgi

---

