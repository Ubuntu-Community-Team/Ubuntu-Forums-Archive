---
title: "Server Port Numbers - POP3 &amp; SMTP"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by LucyDog on 2010-12-01
Hi

For me, this is day two of the Linux experience, and so far so good.

My first task of the day is to set up my email accounts in Evolution. Can anyone tell me how to configure the server port numbers for pop3 and smtp?

Any help would be appreciated.

Oh, and so far, I am loving Ubuntu. I think this is the beginning of a beautiful friendship.

LucyDog

---

### Post by bioterror on 2010-12-01
Here you go

```
POP3 - port 110
IMAP - port 143
SMTP - port 25
HTTP - port 80
Secure SMTP (SSMTP) - port 465
Secure IMAP (IMAP4-SSL) - port 585
IMAP4 over SSL (IMAPS) - port 993
Secure POP3 (SSL-POP) - port 995
```

And hope you like your experience with Ubuntu.
We are glad to have you onboard ;)

---

### Post by plucky on 2010-12-01
In Evolution add the port number after your server name

```
pop.your-isp.com:**280**
smtp.your_isp.com:**35**
```

to specified port number by you email provider.

Good Luck

---

### Post by bioterror on 2010-12-01
One more thing, for a some reason I've never liked Evolution myself and the rules and stuff like that works alot better in Thunderbird.

And if you're migrating from Windows to Linux, I bet you've used Thunderbird and it's easier to use it.

And here's link [https://help.ubuntu.com/community/UsingGmailWithEvolution]("https://help.ubuntu.com/community/UsingGmailWithEvolution")

---

### Post by LucyDog on 2010-12-01
Hi

The only problem I have is that I'm not sure where to configure the port numbers. In Outlook, I would go to Internet E-Mail Settings, Advanced tab and then enter the server Port Numbers. In evolution, I can't see a place that let's me enter the values.

In my case, I need to enter 2525 as the Outgoing server (SMTP) port number.

Many thanks.

---

### Post by LucyDog on 2010-12-01
> **plucky said:**
> In Evolution add the port number after your server name

```
pop.your-isp.com:**port_#**
smtp.your_isp.com:**port_#**
```as specified by you email provider.

Good Luck

Perfect. Many thanks indeed.

---

### Post by LucyDog on 2010-12-01
> **plucky said:**
> In Evolution add the port number after your server name

```
pop.your-isp.com:**port_#**
smtp.your_isp.com:**port_#**
```as specified by you email provider.

Good Luck

Hi

I've added the port number as suggested, i.e.

hosts.co.uk:port_2525

but I notice that the :**port_2525** is not saved. Only the hosts.co.uk remains unchanged.

Any ideas?

LucyDog

---

### Post by LucyDog on 2010-12-01
Okay. I'm there now. It's working fine.

Many thanks for your help.

LucyDog

---

### Post by Stacey Borden on 2010-12-10
I have entered pop.optonline.net and smtp.optonline.net.  It does not let me enter pop.optonline.net:port_110 and smtp.optonline.net:port_25.  What am I missing?

---

### Post by Stacey Borden on 2010-12-10
I am trying to write :port_110 but it makes a happy face and :port_25

---

### Post by plucky on 2010-12-11
> **Stacey Borden said:**
> I have entered pop.optonline.net and smtp.optonline.net.  It does not let me enter pop.optonline.net:port_110 and smtp.optonline.net:port_25.  What am I missing?

Try pop.optonline.net:110
and smtp.optonline.net:25

You don't need to put port_110 and port_25.Also as those are the defaults for email,you shouldn't have to enter anything.It is only if your ISP doesn't use the default ports for email that you have to enter the port number.

Good Luck

---

### Post by Stacey Borden on 2010-12-11
I finally figured it out.  first there is a little plug icon at the lower left of the screen that means you are working with the machine OFF-LINE. click it and it is plugs in and the send/receive button lights up.  then for optonline.net only both the POP and SMTP are mail.optonline.net.  Yeah!  I figured it out myself.  thank you!

---

