---
title: "Running windows e-mail from Ubuntu?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Chris Hansen on 2009-01-12
Hello,

On a dual boot system, with Vista and Ubuntu, is it possible to use wine to run windows e-mail?

Thanks.

---

### Post by cerealtx on 2009-01-12
you could try installing windows mail..not really sure why but that is all ur choice

---

### Post by zyberwoof on 2009-01-12
Before anyone is going to be able to help you, you'll need to clarify what you mean by "Windows e-mail".  

Do you currently use Outlook or Outlook Express, do you use your browser to check your email, or are you referring to something else?

---

### Post by kestrel1 on 2009-01-12
doughtful, You could try it though.
Alternitavly, use Evolution or Thunderbird.

---

### Post by ugm6hr on 2009-01-12
I'd never heard of it: [http://en.wikipedia.org/wiki/Windows_Mail](http://en.wikipedia.org/wiki/Windows_Mail)

But I suspect the answer is No.

If you want to access the same mailbox, I'd suggest using Thunderbird in Vista and Ubuntu.

---

### Post by whoop on 2009-01-12
If you just want to use the same email (address) in windows and linux check if your email provider supports IMAP. Otherwise you could also configure your emailclients to leave the email on the server and only delete it when you delete it from one of your clients.

But as the previous replies stated. We are not really sure what it is you are trying to achieve.

---

### Post by Chris Hansen on 2009-01-12
Thanks for the replies, sorry I wasn't more clear.

I'm trying to access the same e-mail from both systems and have changes on one system reflected on another. The windows e-mail I refer to is the e-mail program that came with Vista. 

I do have Thunderbird installed on both systems and it works mostly fine but my wife is more comfortable with the windows e-mail. I admit that I prefer the look and feel of the windows e-mail over Thunderbird.

Can someone explain what imap is?

I tried the setting where you leave the messages on the server but I was having to delete messages in one system and then delete them again in the other system and it got annoying.

Thanks.

---

### Post by ugm6hr on 2009-01-12
> **Chris Hansen said:**
> I tried the setting where you leave the messages on the server but I was having to delete messages in one system and then delete them again in the other system and it got annoying.

Unless you have a shared inbox, this will always be a problem.

Thunderbird is definitely your best bet.

---

### Post by kestrel1 on 2009-01-12
Imap is like using webmail, but you can do it from the comfort of an email client, such as Thunderbird.
This is only any good if your email provider supports imap though.
All messages are left on the server unless you delete them & you can access them from any machine that is setup for that particular email account using imap. Very useful.
That is all I use now.

---

### Post by samden on 2009-01-12
Normally an email program uses "pop". Basically that just downloads the messages from the server, so now they are on your computer. You can choose to leave them on the server too.

Imap is an alternative protocol to pop, you would select it instead of pop when you set up your account in your email program (thunderbird, windows mail etc). Not all email providers support it. But instead of just downloading the messages, it keeps your inbox synchronised with the server. So the messages are still on the server, although you may be storing them on your computer too. So wherever you access your emails from you will see exactly the same inbox.

If your current provider doesn't support IMAP, the simplest solution is to get a gmail account. You can set gmail to download all your messages from your current provider using pop to the gmail inbox, then access your gmail inbox with IMAP. This works really well and is what I and many other people do.

Regarding Windows Mail however, I can't see why anyone would want to use Wine just to run an email program. There are plenty of native Linux options. Any change is a change of course, and you will usually prefer your old program at first simply because you are used to it. That doesn't mean the new one is bad, just different. 

Try Evolution instead of thunderbird, that is really good and quite similar to MS Outlook (as in the full-featured MS Outlook that businesses use, not the cut-down program Windows Mail you get on most home computers). There are bound to be other options too to try - go to "Add/remove applications" and have a poke around.

---

### Post by Chris Hansen on 2009-01-12
> **samden said:**
> 

But instead of just downloading the messages, it keeps your inbox synchronised with the server. So the messages are still on the server, although you may be storing them on your computer too. So wherever you access your emails from you will see exactly the same inbox.


So if I delete a message from Vista and then check it from Ubuntu it will already be deleted there?
> **samden said:**
> 
Try Evolution instead of thunderbird, 
Evolution was the first thing I tried but I couldn't get it to send mail in Vista.

---

### Post by Chris Hansen on 2009-01-14
> **samden said:**
> You can set gmail to download all your messages from your current provider using pop to the gmail inbox, then access your gmail inbox with IMAP. This works really well and is what I and many other people do.


That sounds really slick and it might be just what I'm looking for. Can someone describe how it's done or where I can look to find out?

Thanks.

---

