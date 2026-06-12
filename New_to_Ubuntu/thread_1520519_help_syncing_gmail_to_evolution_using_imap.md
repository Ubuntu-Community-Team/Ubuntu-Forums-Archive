---
title: "help syncing gmail to evolution using imap"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by aaron_kai on 2010-06-29
I've looked everywhere, but can't find anyone with my problem exactly.   I am a new user.

I am trying to allow evolution to check and send email through my gmail account using IMAP.  I am running ubuntu 10.04

I have done the following:
1.  Changed settings at gmail to 'enable IMAP'
2.  Done the Wizard twice in evolution through edit--> preferences
3.  I've tried all kinds of combinations.  I have tried inputting the server as [EMAIL="xxx@gmail.com"]xxx@gmail.com[/EMAIL] and [EMAIL="xxx@googlemail.com"]xxx@googlemail.com[/EMAIL].  I have tried putting the port number :993 after the server name.
4.  When I restart evolution, I am asked for my IMAP password.  I enter it.  Fine.  If I enter the wrong password I get an error message until I enter the right one.  
5.  I can send mail to my gmail account from evolution.

So why can't I import my new mail to my Evolution account.  POP worked.  When I click send receive, it says "scanning folders at imap.gmail.com" but nothing appears.  

Am I missing something?
thanks

---

### Post by plucky on 2010-06-29
The server name should be **imap.gmail.com:993** and **smtp.gmail.com** and you have to have SSL encryption enabled.

> I have tried inputting the server as [email]xxx@gmail.com[/email] and [email]xxx@googlemail.com[/email]

That would be your username as supplied by google.

See [Configuring Mail Clients](http://mail.google.com/support/bin/answer.py?answer=78799)

Good Luck

---

### Post by aaron_kai on 2010-06-29
Ok.  I entered the information as you said.  Evolution  succeeded in logging into my gmail account, as I could see it scanning my folders.  The problem remains that after that, Evolution does not seem to retrieve/display any of the new mail. 

I don't know what end the problem is on.  Is the new mail retrieved, but I can't see it, making it a problem with Evolution (/me not knowing to check some box or click on some menu option) or is it with gmail?

As I said, I don't have any problem sending mail.

Thanks.

---

### Post by plucky on 2010-06-29
Do you have the **Sidebar** open?

In Evolution go to **View > Layout > Tick Show Sidebar** and you should be able to see all your folders.

It should create your IMAP folders in the sidebar.

Good Luck

---

### Post by gandaran on 2010-06-29
check again your gmail settings

your gmail

select imap server

your gmail username 

> imap.gmail.com:993 
just fill in  imap.gmail.com without the port number and select/enable SSL encryption.
when you enable SSL encryption the 993 port is automatically used by evolution, theres no need to write it.
it should work with just this information.

---

### Post by aaron_kai on 2010-06-29
Google settings :  IMAP enabled (this is the only one as far as I know)

Evolution Settings: Receiving Tab

Server Type = IMAP
Server = Imap.gmail.com
Username = [EMAIL="xxx@gmail.com"]xxx@gmail.com[/EMAIL]
Security = SSL encryption
Authentication = Password

Settings: Sending Email Tab
Server Type = SMTP
Server = smtp.gmail.com
Requires server authentication box checked
Security = SSL encryption
type = plain
username= xxx

Evolution is logging into IMAP.  The info at the bottom says it is "fetching information" from folder X.  But then nothing happens.  I've checked everything 20 times now.  I'm starting to wonder why I just don't log into my gmail instead.

I do have a sidebar and my imap account is there.  When I click on it , it remains empty.

---

### Post by gandaran on 2010-06-30
> Server = Imap.gmail.com?
imap.gmail.com, without any capital letters.

---

### Post by aaron_kai on 2010-06-30
Screw it.  Downloaded Thunderbird.  It works.

---

