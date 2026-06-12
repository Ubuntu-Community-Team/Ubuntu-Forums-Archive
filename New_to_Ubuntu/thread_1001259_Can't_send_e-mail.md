---
title: "Can't send e-mail"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Chris Hansen on 2008-12-03
Hi everyone,

I'm new here and I just installed Ubuntu on my pc as a dual boot with Vista. It's exciting having a system that's not windows but I still have a few issues to address.

I seem to be able to receive e-mail but I can't send it. When I click on "send/recieve" the little window comes up, e-mail is received without a problem and then it sits there. The status bar for sending mail doesn't move and, if I wait long enough, I get a message that it can't connect to the server and that the connection timed out.

I tried to put in the same settings that are in the windows e-mail but the settings in the two systems look so different I'm not really sure what to put for some of them.

If anyone has some advice I sure could use it.

Thanks.

---

### Post by evilkastel on 2008-12-03
Welcome. First what client are you using? evolution? thunderbird? what kind of account are you trying to get? gmail? hotmail?. Without this, no one can help you.

---

### Post by Chris Hansen on 2008-12-04
> **evilkastel said:**
> Welcome. First what client are you using? evolution? thunderbird? what kind of account are you trying to get? gmail? hotmail?. Without this, no one can help you.

Oh, sorry.

I'm trying to access a hotmail accout and I'm using the program that comes with the ubuntu install, I believe it's evolution.

---

### Post by LowSky on 2008-12-04
this sould help
Bear in mind it is out dated and from what I keep reading, hotamil has been acting up for many linux users since Microsoft updated the serice in the last few months

[http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html](http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html)

---

### Post by Chris Hansen on 2008-12-04
Thanks for the help. It still doesn't work but I feel like it's getting closer.

I followed the directions and when I click on "send/recieve" I'm asked to enter a password. I enter my password and it says:

"Unable to authenticate to SMTP server.
Bad authentication response from server.

Please enter the SMTP password for 
[email]Chris_Hansen@q.com[/email] on host 127.0.0.1"

I believe I only have the one password to enter for that e-mail and it doesn't seem to work.

I also tried putting in the server name that they gave me, smtp.live.com, and I get the message:

"Error while performing operation.

MAIL FROM command failed: Must issue a STARTTLS command first"

I just checked online and the e-mail is working, it also works fine from windows.

If it makes a difference: when I sign on to hotmail it brings me to "Qwest Mail by Windows Live"

When I set up my windows mail I also had to change the outgoing server port but I didn't see a place to do that in evolution.

Sorry to be a bother, I really appreciate the help, I'm starting to feel like I'm the problem that won't go away.

---

### Post by Zzl1xndd on 2008-12-04
I think I know what the problem might be. 

When sending outgoing mail most service providers block all out going SMTP trafic on port 25 except for their own SMTP server. So your out going server is probably not the hotmail one.

Did your ISP set you up with an Email account? if so you might need to use that information for the SMTP server.

Or use SSL that will change the port on the server and let you use Hotmail SMTP server (provided hotmail allows for that).

---

### Post by Chris Hansen on 2008-12-04
Thanks for the reply.

My ISP did set me up with an email account through hotmail, it looks like I get redirected to a Qwest place though and my e-mail is q.com instead of hotmail.com. I did try to use the information they gave me but I couldn't find some of the settings in Evolution. I couldn't find how to change the outgoing port setting and I don't really understand security algorithms but I didn't see that setting in Evolution either.

Is there a different e-mail program that might work better or are they all about the same?

---

### Post by sydbat on 2008-12-04
Thunderbird is about the same as Outlook Express. Applications > Add/Remove > Search for Thunderbird and install. Will be as easy to configure too.

But the real problem might be Windows Live. My father changed completely from XP to Ubuntu and could not get his hotmail account to work right either...so he decided to drop it and now has a Gmail account. It has to do with the 'locking in' that Microsoft wants from their clients (like having to use Silverlight, inability to access your hotmail from another email service, etc)...something most other free email services do not require. This is not meant as a Microsoft bashing statement, it is simply the facts.

---

### Post by Chris Hansen on 2008-12-05
Part of the problem seems to be that Evolution doesn't show some of the settings I might need to change. Is there a file where you can enter the settings manually?

---

### Post by Chris Hansen on 2008-12-05
I think I got it!!

Qwest said to use SSL but when I set it to TLS it seemed to work.

---

### Post by Captain_tux on 2008-12-05
With regard to email clients, this isn't the first time I hear of instructions saying to use SSL and being wrong... TSL seems to be the difference maker.

---

### Post by Chris Hansen on 2008-12-05
My windows e-mail is set to SSL and it works fine so I didn't question it but I was lucky enough to stumble on an old post where someone else had the same problem.

---

### Post by javaman_jg on 2009-01-28
I was getting exactly the same problem using Evolution on Hardy:
"MAIL FROM command failed: Must issue a STARTTLS command first"
from exactly the same server: smtp.live.com. This was after Qwest advised me to use SSL encryption. No good. Then I took a look here and got a bit closer with TLS, but, here is the trick- I had to clear my Outbox and THEN set the TLS encryption. Something about the old outgoing messages that were created with the wrong settings was throwing the error.

---

### Post by mrbreese on 2009-01-30
**Help too!!!!** 

My wife got this mini dell from work for a service reward. It came with Ubuntu which I barely heard of till now. 

Evolution receives mail but won't send. I get the same error;
"Unable to authenticate to SMTP server, Bad authentication response from server."

My cable provider said outgoing mail shouldn't need to authenticate. Last night the send/receive" box went completely inactive. I forced it by replying to inbox mail and thats when it seemed to get mad and shut down the send/receive box.

We're older and not very savvy with this level of trouble...


Any help would be most appreciated.

---

### Post by physeetcosmo on 2009-02-10
> **mrbreese said:**
> **Help too!!!!** 

My wife got this mini dell from work for a service reward. It came with Ubuntu which I barely heard of till now. 

Evolution receives mail but won't send. I get the same error;
"Unable to authenticate to SMTP server, Bad authentication response from server."

My cable provider said outgoing mail shouldn't need to authenticate. Last night the send/receive" box went completely inactive. I forced it by replying to inbox mail and thats when it seemed to get mad and shut down the send/receive box.

We're older and not very savvy with this level of trouble...


Any help would be most appreciated.

mrbreese,

Please check your evolution settings by opening the application, click Edit >> Preferences

In the popup window select your email address in the right-half pane and select Edit. From there select the Sending Email tab and verify that:

Authentication Method

Is set to 'PLAIN' and not to TLS or SSL.

Let me know if this helps. :) The reason is that Evolution does not support STARTTLS commands, let me guess you are using Gmail? :)

---

### Post by rlwilen on 2009-05-15
i try to to use linux program to send e-mail and i get to where it ask for the pass word but the pass word won't work for some reason


> **Chris Hansen said:**
> Thanks for the help. It still doesn't work but I feel like it's getting closer.

I followed the directions and when I click on "send/recieve" I'm asked to enter a password. I enter my password and it says:

"Unable to authenticate to SMTP server.
Bad authentication response from server.

Please enter the SMTP password for 
[email]Chris_Hansen@q.com[/email] on host 127.0.0.1"

I believe I only have the one password to enter for that e-mail and it doesn't seem to work.

I also tried putting in the server name that they gave me, smtp.live.com, and I get the message:

"Error while performing operation.

MAIL FROM command failed: Must issue a STARTTLS command first"

I just checked online and the e-mail is working, it also works fine from windows.

If it makes a difference: when I sign on to hotmail it brings me to "Qwest Mail by Windows Live"

When I set up my windows mail I also had to change the outgoing server port but I didn't see a place to do that in evolution.

Sorry to be a bother, I really appreciate the help, I'm starting to feel like I'm the problem that won't go away.

---

