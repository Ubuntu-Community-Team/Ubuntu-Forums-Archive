---
title: "Evolution settings"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by philk949 on 2009-07-07
Hi,
I have just attempted to configure my Evolution Mail Client.
The Send function completes but not so the Receive function.
I am using POP for receiving and SMTP for sending.
The Send error message is attached. Could you please help with this setup?
Thank you
Phil

---

### Post by wojox on 2009-07-07
It looks like you need TLS Encryption set for sending mail.
Who's your email account with?

---

### Post by lisati on 2009-07-07
> **philk949 said:**
> Hi,
I have just attempted to configure my Evolution Mail Client.
The Send function completes but not so the Receive function.
I am using POP for receiving and SMTP for sending.
The Send error message is attached. Could you please help with this setup?
Thank you
Phil

> **wojox said:**
> It looks like you need TLS Encryption set for sending mail.
Who's your email account with?

If it's Yahoo, I think it needs SSL for both send and receive... gmail has similar arrangements.

---

### Post by philk949 on 2009-07-07
Thank you for your replies. I am attempting to set up a Gmail account. Do I adjust my settings through Preferences in the mail client?
Phil

---

### Post by wojox on 2009-07-07
Yes Edit > Prefrences

Receiving Emails
Server POP
pop.gmail.com
SSL Encryption
Remember password

Sending Emails
SMTP
smtp.gmail.com
Server requires auth
SSL Encrypt

---

### Post by philk949 on 2009-07-07
Thank you.
Problem solved.
Phil

---

### Post by philk949 on 2009-07-13
Mark
Ohio, USA[/QUOTE]

Hi Mark,
With a little help from Forum friends, I was able to configure an account in Evolution for Gmail. The tricky part is in getting your Incoming (receiving) and Outgoing (sending) settings configured correctly. I have attached 2 screenshot images that show these server settings plus the Encryption settings that I entered for a successful result. Try these in your Evolution with a Gmail account (set up a Gmail account first, of course).
Let me know how you get on, Mark.
Phil

---

### Post by lisati on 2009-07-13
BTW, the last time I set up a gmail account on an email client, I had to log into gmail's website and edit the settings to allow pop access.

---

### Post by Rifester on 2009-07-13
Thank you, I switched to gmail last night and now wonder what took me so long.   I have Evolution up and running!

---

### Post by lg8302 on 2009-07-13
Hi,
I just checked my settings but have the same but do not manage to get evolution to work. As on the website login it is with [email]xxx@gmail.com[/email] I tried both with and without the @gmail.com  but it does not get me anywhere. Well I am not at all surprised because there is something strange in evolution ..password cannot be entered? I would love the look of evolution but I gave up and use Outlook 2007 again as I do not see how I can possibly get evolution to work! All 4 email accounts which are auto configured within seconds by Outlook 2007 do not work in evolution. For the Swiss accounts I need a passcode and do not see where I could enter this ? Am I blind?

---

### Post by t0p on 2009-07-13
> **lg8302 said:**
> Hi,
I just checked my settings but have the same but do not manage to get evolution to work. As on the website login it is with [email]xxx@gmail.com[/email] I tried both with and without the @gmail.com  but it does not get me anywhere. Well I am not at all surprised because there is something strange in evolution ..password cannot be entered? I would love the look of evolution but I gave up and use Outlook 2007 again as I do not see how I can possibly get evolution to work! All 4 email accounts which are auto configured within seconds by Outlook 2007 do not work in evolution. For the Swiss accounts I need a passcode and do not see where I could enter this ? Am I blind?

No, you're not blind. You just need to go through the process fully.  Go to **Edit > Preferences > Add Mail Account**, and go through the setup process.  When you get to the **Receiving Email** page, you will be asked for authentication type. Select "password".  Look at the first attached screenshot.  As you can see in the text box by the mouse pointer, "you will not be prompted for a password until you connect for the first time".  So, go through the rest of the setup process, click **Apply**.  Now, click on **Send & Receive**.  As you can see in Screenshot2, you'll now be prompted for the password.  If you tick **Remember this password**, you won't need to input it again in the future.

---

### Post by baldmancan on 2009-07-25
> **philk949 said:**
> Mark
Ohio, USA

Hi Mark,
With a little help from Forum friends, I was able to configure an account in Evolution for Gmail. The tricky part is in getting your Incoming (receiving) and Outgoing (sending) settings configured correctly. I have attached 2 screenshot images that show these server settings plus the Encryption settings that I entered for a successful result. Try these in your Evolution with a Gmail account (set up a Gmail account first, of course).
Let me know how you get on, Mark.

---

### Post by baldmancan on 2009-07-26
I may have posted this twice..
If so, my apologies in advance, 
as I am new to this forum.

In response to screenshots of gmail setups...
(previously posted by philak)
Thanks for such detailed help...
I looked at those screen shots. That was most helpful.

However,
I would like to configure evolution to send 
but not recieve mail from my gmail account. 
Is this possible?

I entered none at the the top of the receive mail server, then continued with the same format you did on the send mail set up.
I have no success. So far it just times out. I am assuming that entering my username and checking remember password, triggers a request for my password upon connection with gmail servers. 

(Odd that there is a check offbox to remember passwords but there is no blank to input one,. nor. is the oddity addressed anywhere) Am I alone in my thinking here.?

Please advise.

---

