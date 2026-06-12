---
title: "Evolution/Hotmail; cant find solution"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by jmedoro on 2009-04-29
hey everyone...

i'm trying to add my hotmail account to Evolution. I googled around and the first thing i found was a tutorial from this very forum.

i set everything up according to the instructions, and didnt seem to have a problem. when i hit the 'send/receive' button, however, i got the following error message:

Could not connect to 127.0.0.1: Connection refused.

I'm not finding any reason why i'm getting this, or how to fix it. Does the answer jump out at anyone? do you need any more info from me? i set up a gmail account afterward with no problem...

Edit: regarding the gmail, i see that i am getting the same message. however, i am seeing the messages in my gmail inbox through Evolution

---

### Post by Didius Falco on 2009-04-29
Give me a link to the tutorial, please.

127.0.0.1 is a loopback - in other words, when you try and connect to that address, you are trying to connect to yourself.

[http://www.tech-faq.com/127.0.0.1.shtml](http://www.tech-faq.com/127.0.0.1.shtml)

---

### Post by jmedoro on 2009-04-29
> **Didius Falco said:**
> Give me a link to the tutorial, please.

127.0.0.1 is a loopback - in other words, when you try and connect to that address, you are trying to connect to yourself.

[http://www.tech-faq.com/127.0.0.1.shtml](http://www.tech-faq.com/127.0.0.1.shtml)

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

there's a link...

wow, a frequent internet joke. if that was the type of joke i found myself playing on someone, i'd question my sense of humor.

---

### Post by jacksaff on 2009-04-29
Microsoft make it very difficult for any program other than a web browser or outlook to connect to hotmail.
Because of this the only way you can get your mail into a linux client like evolution or t-bird is to have a small program installed that connects to hotmail and pretends it,s outlook. Evolution then connects to this program to send/recieve, which is why it's trying to get mail from your own computer.
The failure suggests that it's the small program that's not working, not evolution. We need to see more detail about how you tried to set this up to get any further.

If you want full email access to a webmail account start switching to something else now (recommend gmail). Hotmail is the WORST at allowing you to access your mail using linux.

---

### Post by Didius Falco on 2009-04-29
That tutorial is fairly old. I think you can do this without going through all that.Here is a Google info page on setting up POP3 for Gmail.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=10350](http://mail.google.com/support/bin/answer.py?hl=en&answer=10350) 

I hope this helps...

On Edit:

Here is the total Hotmail settings from Wikipedia:

> 
[POP3]("http://en.wikipedia.org/wiki/POP3") access is now available for all Hotmail accounts, adding support to access Hotmail from any email client &#8211; including most notably the [iPhone]("http://en.wikipedia.org/wiki/IPhone") and other mobile devices
**POP3 Settings:**
**POP server:** pop3.live.com (Port 995)
**POP SSL required?** Yes
**User name:** Your Windows Live ID, for example [EMAIL="yourname@hotmail.com"]yourname@hotmail.com[/EMAIL]
**Password:** The password you usually use to sign in to Hotmail or Windows Live
**SMTP server:** smtp.live.com (Port 25 or 587)
**Authentication required?** Yes (this matches your POP username and password)
**TLS/SSL required?** Yes

[http://en.wikipedia.org/wiki/Hotmail#POP3](http://en.wikipedia.org/wiki/Hotmail#POP3)

I hope this helps...

---

### Post by jmedoro on 2009-04-29
thanks Jacksaff and Didius...

i deleted my hotmail account in Evolution and tried all suggestions for gmail, and still get the same 'could not connect to 127.0.0.1: connection refused' message.

this would make me think the problem is not specific to hotmail, but to any email account i try to configure.

i'm looking in edit/preferences/mail accounts to see what the problem is, but there doesnt seem too much that could go wrong here (i'm really only entering info into a few fields for both receiving and sending email, and everything matches what i've been seeing elsewhere online).

i'm wondering if the problem lies elsewhere, and how i can get Evolution to stop trying to connect to 127.0.0.1 if it should be doing something else.

---

### Post by jmedoro on 2009-04-29
the quest continues...

ok, disregard the above if this makes more sense. i googled the 'could not connect message' and got this:

> It sounds like your inetd daemon isn't running since your connections are being refused

now, aside from me knowing very little about an inetd daemon (which i will promptly google when i wake up), i'm pretty sure i installed the inetd daemon when trying to configure the hotmail. here's what i had to type in the terminal window, from the tutorial:


> Now, install the inet daemon

Code:

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies. Now on to the good stuff...

Code:

sudo apt-get install hotway hotsmtp

This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.

Code:

sudo gedit /etc/inetd.conf

Look for a line like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:

2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd

This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:

Code:

sudo /etc/init.d/inetutils-inetd restart



sorry for the length. if you can do something with that, that would be great, if not, thanks for all the help anyways, i'll get this running at some point i am sure.

---

### Post by mcrene on 2009-04-30
I am on the same page as you with this problem.
I haven't been able to get anywhere with it either.

I'll be watching this closely, please post up any results and I will do the same.

---

### Post by Didius Falco on 2009-04-30
You should undo all the changes you made with that HowTo.

When you are uninstalling things, watch out for any dependencies it removes. Some packages remove things you actually need installed along with the package.

---

### Post by philinux on 2009-04-30
Working great here.

[http://ubuntuforums.org/showthread.php?t=1094136&highlight=hotmail](http://ubuntuforums.org/showthread.php?t=1094136&highlight=hotmail)

---

### Post by caco on 2009-05-09
The simple settings posted by Didius works I just tried it without installing any extra packages or applications

Have fun ;)

---

### Post by RavanH on 2009-05-12
POP access for Hotmail / Live Mail as described earlier in this thread is working just fine. No need anymore for hotwayd or other workarounds. Gmail has POP access too (if enabled in your Gmail Settings) but you might consider using IMAP for Gmail. I use it with Opera 10 (alpha) and it works just GREAT :)

Any errors related to 127.0.0.1 loopback (localhost) must be due to a setting in any of your accounts setup in Evolution. Check them one by one to see if any have this IP address or any name (like localhost or the name of your computer) that points to the same IP, in its mail server fields...

---

### Post by Ms_Angel_D on 2009-05-12
There are instructions on setting up hotmail with evolution in the user documentation.

[https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

---

