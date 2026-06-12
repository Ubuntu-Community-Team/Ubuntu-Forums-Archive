---
title: "Using MUTT"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by CosmicFlux on 2009-07-25
Hey,

I want to try using MUTT for email. I've executed the following;
[B]
sudo apt-get install mutt[/B]

Am I right in thinking that MUTT is just a reader and that I will need separate programs to send mail and fetch mail?

Also, to set this all up am I going to have to create a muttrc file in my home directory?

Cosmic

---

### Post by llamabr on 2009-07-25
[http://www.google.com/search?q=muttrc&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=muttrc&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Mutt is a very powerful email reader, sender, and much more.  Once you start mutt, you already have a muttrc.  It is infinitely configurable, as you can follow the above link.

---

### Post by andrew.46 on 2009-07-26
Hi CosmicFlux,

> **CosmicFlux said:**
> Am I right in thinking that MUTT is just a reader and that I will need separate programs to send mail and fetch mail?

Mutt can be set up many different ways and you are describing the traditional method. This is the method I use myself with:

[LIST=1]
[*]'Fetchmail' to grab the mail
[*]'Procmail' to sort, filter and deliver the mail
[*]'Mutt' to read the mail and compose replies and new mail
[*]'Msmtp' to deliver the mail
[/LIST]

But mutt can also be configured to directly access IMAP mailboxes and I believe can also be configured to access pop3 mailboxes directly.

> Also, to set this all up am I going to have to create a muttrc file in my home directory?

Indeed you are, although normally this is a dot file: $HOME/.muttrc.

All the best,

Andrew

---

### Post by CosmicFlux on 2009-07-26
Thanks for your advice, I'll give it a go. Suspect I may be in over my head a little bit though! 

Tried to use Fetchmail to retrieve mail from my ISP mail server. This is what I got;

[B]fetchmail -u [email]myusername@mydomain.com[/email] pop.mymailserver.com
Enter password for [email]myusername@mydomain.com@pop.mymailserver.com[/email]: 
fetchmail: connection to pop.myusername.com:imap [217.146.188.192/143] failed: Connection refused.
IMAP connection to pop.mymailserver.com failed: Connection refused
1 message for [email]myusername@mymailserver.com[/email] at pop.mymailserver.com (2556 octets).
reading message [email]myusername@mymailserver.com@pop-smtp1-f.bt.mail.vip.ird.yahoo.com[/email]:1 of 1 (2556 octets).fetchmail: connection to localhost:smtp [::1/25] failed: Connection refused.
. flushed[/B]


As you can see, the connection is being refused. Although it says I have 1 message waiting. Confusing.

Cosmic

---

### Post by CosmicFlux on 2009-07-26
Just an update;

I've managed to get Fetchmail to retrieve my messages, although it still throws up a connection refused error.

Do I have to retrieve the mail using Fetchmail first before going into Mutt, or can I have it configured so that when I open mutt fetchmail automatically checks for new messages?


Cosmic

---

### Post by andrew.46 on 2009-07-26
Hi CosmicFlux,

> **CosmicFlux said:**
> Do I have to retrieve the mail using Fetchmail first before going into Mutt, or can I have it configured so that when I open mutt fetchmail automatically checks for new messages?

Put the following in your $HOME/.muttrc:

```
macro index,pager I '<shell-escape> fetchmail -v<enter>'
```

and then you will simply have to open mutt and press the 'I' key and fetchmail will check your mail according to the settings in $HOME/.fetchmailrc.

All the best,

Andrew

---

### Post by CosmicFlux on 2009-07-26
OK, thanks. That worked!

I can now send mail and receive it, although in getting the sending sorted I've somehow managed to stop mail showing up in Mutt. Using fetchmail from the command line I can see i have unread messages on my server, but Mutt says there is no new messages and shows nothing.

I think the problem may be related to the fact that fetchmail is trying to open my local smtp port to forward the mail. Should it not be forwarding it to my /var/spool/mail/user file for Mutt to read?

This is the code I get;

**fetchmail: SMTP transaction error while fetching from [email]myemailaddress@myhost.com@pop.mailserver.com[/email] and delivering to SMTP host localhost**

Also, I notice that the directory at the top left corner of the Mutt interface is /var/mail/me. Should it be /var/spool/mail/me instead?



Cosmic

---

### Post by andrew.46 on 2009-07-26
Hi CosmicFlux,

> **CosmicFlux said:**
> I can now send mail and receive it, although in getting the sending sorted I've somehow managed to stop mail showing up in Mutt. Using fetchmail from the command line I can see i have unread messages on my server, but Mutt says there is no new messages and shows nothing.

I think the problem may be related to the fact that fetchmail is trying to open my local smtp port to forward the mail. Should it not be forwarding it to my /var/spool/mail/user file for Mutt to read?

I think you have hit the nail on the head there, Fetchmail must hand the mail off to something. The conventional way is to pass it to procmail and typically the $HOME/.fetchmailrc looks something like this:

```

poll [COLOR="Red"]*smtp.address*[/COLOR]         
with proto POP3       
user '[COLOR="Red"]*username_for_account*[/COLOR]'        
there with password '[COLOR="Red"]*password_for_account*[/COLOR]'        
is '[COLOR="Red"]*local_username*[/COLOR]' here                              
mda "/usr/bin/procmail -d %T"

```

while the typical $HOME/.procmailrc file looks like:

```
PATH=/bin:/usr/bin:/usr/local/bin 
VERBOSE=off              
MAILDIR=$HOME/mail
DEFAULT=/var/spool/mail/*[COLOR="Red"]your_username [/COLOR]*  
LOGFILE=$HOME/.procmaillog 
```

This delivers all mail to /var/spool/mail/*username* while allowing local delivery of any sorting recipes to $HOME/mail.


> Also, I notice that the directory at the top left corner of the Mutt interface is /var/mail/me. Should it be /var/spool/mail/me instead?


This can be set several different ways but the easiest is a setting in your $HOME/.muttrc:

```

set spoolfile = /var/spool/mail/*[COLOR="Red"]username[/COLOR]*

```

Have a look at the following guide which outlines some of this information and just ignore the Gmail stuff :-).

[Howto] Use Mutt with Gmail 
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

All the best,

Andrew

---

### Post by CosmicFlux on 2009-07-27
Great! That solved it!

Thanks very much!


Comsic

---

### Post by andrew.46 on 2009-07-27
Hi Comsic,

> **CosmicFlux said:**
> Great! That solved it!

Thanks very much!

No problem :). I wish you all the best with mutt which I will admit is my most favourite linux app of all time!

Andrew

---

### Post by CosmicFlux on 2009-07-27
It's funny, installing and configuring the email system has been a very frustrating experience and yet now that it's done I can say I've learned a LOT from it. 

You don't realize just how much goes on in the background when you're using a GUI client!

Cosmic

---

### Post by andrew.46 on 2009-07-27
Hi Cosmic,

> **CosmicFlux said:**
> It's funny, installing and configuring the email system has been a very frustrating experience and yet now that it's done I can say I've learned a LOT from it. 

Well, if you enjoyed that you may be interested to know that there is a Usenet client that shares a similar look and feel to mutt called slrn. I have just finished writing the wiki page for it:

slrn - Community Documentation
[https://help.ubuntu.com/community/slrn](https://help.ubuntu.com/community/slrn)

It can look a little complex to install and configure but the similarity to mutt is unmistakable.

Andrew

---

