---
title: "Connecting to Yahoo mail"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-04-12
I found Thunderbird via the Synaptic package manager and installed it. From my reading it seems I need YPops! as well. Does anyone know if that is automatically installed when I installed Thunderbird, and if not where can I find YPops and any needed instructions. BTW, I have Ubuntu 8.04 and I want to connect to my Yahoo email account. Many Thanks.

---

### Post by halitech on 2009-04-12
I use thunderbird fine with no addons to get my yahoo mail. 

I use pop.mail.yahoo.ca for the incoming mail server on port 995 with SSL on.

I think you do need to enable pop access in yahoo to use this though.

---

### Post by lisati on 2009-04-12
In addition to requiring it to be enabled from within Webmail, I think Yahoo requires you to pay for *some* (but not all) yahoo accounts to have POP access.

I use SSL for both send and receive (995 for receive, 465 for send). I have "yahoo.co.nz" email accounts: although Yahoo's "enable pop access" web page told me to use a ".co.nz" server I've never managed to get it to work, so I've used the ".com.au" equivalents.

---

### Post by Sidewinder1 on 2009-04-12
Why not just touch your Yahoo email with Firefox? That's the way I do it. I use Thunderbird for my personal (read private / protected) email account through my ISP. Both methods work well for me.
HTH
Side

PS Same with Hotmail (Firefox) and Gmail; They're my throw-away accounts...If that makes any sense... :-)

---

### Post by jwaclawsky on 2009-04-12
What do you mean by "touch" your email? How do you do that. When I try to connect I get "pop not allowed for user"

---

### Post by halitech on 2009-04-12
> **lisati said:**
> In addition to requiring it to be enabled from within Webmail, I think Yahoo requires you to pay for *some* (but not all) yahoo accounts to have POP access.

I use SSL for both send and receive (995 for receive, 465 for send). I have "yahoo.co.nz" email accounts: although Yahoo's "enable pop access" web page told me to use a ".co.nz" server I've never managed to get it to work, so I've used the ".com.au" equivalents.

I've never paid for pop access for hotmail or yahoo mail and both work for me with no addons

> **jwaclawsky said:**
> What do you mean by "touch" your email? How do you do that. When I try to connect I get "pop not allowed for user"

did you enable pop access in yahoo mail?

---

### Post by jwaclawsky on 2009-04-12
I don't see any places where you can specify Pop or iMap in yahoo. Can you direct me to where this setting is in Yahoo. As far as I can tell you have to pay for PoP, but I am not an expert. Thanks

---

### Post by lisati on 2009-04-12
> **halitech said:**
> I've never paid for pop access for hotmail or yahoo mail and both work for me with no addons
Seems you've had it good: a few years ago (before I'd even heard of Linux) I'd setup Outlook Express to access my hotmail account. I was without internet access for a few weeks and when I got it back, the hotmail system refused access, citing something about having to pay a fee. A similar thing happened a few years later when I had a "yahoo.com" email account. I haven't had a problem with having to pay to access "yahoo.co.nz" email though.....

In summary: in spite of hiccups we sometimes experience, POP access can be done.

---

### Post by halitech on 2009-04-12
> **jwaclawsky said:**
> I don't see any places where you can specify Pop or iMap in yahoo. Can you direct me to where this setting is in Yahoo. As far as I can tell you have to pay for PoP, but I am not an expert. Thanks

Log into your yahoo mail. go to Options (upper right corner) then click on Pop and forwarding. Then click on setup or edit POP & forwarding. Then select Web & Pop access and decide what you want to do with messages it thinks is spam. Click Save and you should be good to go.


> **lisati said:**
> Seems you've had it good: a few years ago (before I'd even heard of Linux) I'd setup Outlook Express to access my hotmail account. I was without internet access for a few weeks and when I got it back, the hotmail system refused access, citing something about having to pay a fee. A similar thing happened a few years later when I had a "yahoo.com" email account. I haven't had a problem with having to pay to access "yahoo.co.nz" email though.....

In summary: in spite of hiccups we sometimes experience, POP access can be done.

A few years ago I couldn't access hotmail via pop unless I wanted to pay for it but I think a few months back (when they changed over to live mail) it started working without having to pay for it.

---

### Post by lisati on 2009-04-12
> **halitech said:**
> A few years ago I couldn't access hotmail via pop unless I wanted to pay for it but I think a few months back (when they changed over to live mail) it started working without having to pay for it.
Thanks. I might check that out. I currently use a plugin on MS Outlook (the trial copy of MS Office I sometimes use should've run out a couple of weeks back but hasn't), and might investigate my options for checking it via one of the Ubuntu-friendly mail clients.

---

### Post by jwaclawsky on 2009-04-12
When I go to yahoo and under options I click on pop and forwarding 
I get a blank page with the following: 

 Upgrade to mail plus: so you can:

    * download your Yahoo! Mail in an email client, such as Outlook
    * forward your Yahoo! Mail to a different address

nothing else on tha page.  I am in the new email. I will try to go back to mail classic and see if it works there.

---

### Post by jwaclawsky on 2009-04-12
...no settings for POP in mail classic that I can find...

---

### Post by halitech on 2009-04-12
not sure why, maybe they are only giving it for free to Canadian users.

---

### Post by jwaclawsky on 2009-04-12
What mail server should I be specifying (I am in the US) to connect to Yahoo mail in Thunderbird?

---

### Post by jwaclawsky on 2009-04-12
If anyone has this working (does in the US matter) what email servers are you using and port numbers. Could you please share your set-up information? Thanks

---

### Post by Sidewinder1 on 2009-04-12
I'm in the US and I just go to yahoo.com (with Firefox) then click on "login" and enter my username and password. Then I'm in. Works the same way with Hotmail and Gmail...No fees no set-up, no nothin'. Not sure what you're doin' wrong. With all due respect, you may be making it harder than it really is...
HTH
 Side

---

### Post by jwaclawsky on 2009-04-12
Yes, that works for firefox (web based e-mail) but i wanted to get thunderbird running 9email client in my machine) so I can do email offline too. ...and it does seem to be harder than it looks  :-)

---

### Post by Jacdeb6009 on 2009-04-13
Hi there,

I have Yahoo! running under Thunderbird as POP3, but in order to do this I had to buy a Plus account.  I fiddled around with this for a number months, but eventually this was the only solution.

It seems that at some point Yahoo! made this feature available for free (could also be that this was only in certain areas, don't rightly know), but for me the only option was to buy an account (at $20 year it's not really a biggie).

The other option, which I also use and works well, is to use Gmail.  This gives you POP3 access for free and it also works well.

(You have another question elsewhere regarding Thunderbird, I have played around with a number of mail clients and eventually find that Thunderbird best meets my needs, I used to run The Bat! under Windows, and Thunderbird is the closest I can find as a replacement).

Anyway, sorry it's not all good news, but I hope this helps.

Cheers,

---

### Post by jwaclawsky on 2009-04-26
I finally bought the $20 plus account at Yahoo and now I am working just fine.

---

