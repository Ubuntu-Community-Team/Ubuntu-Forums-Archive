---
title: "Use Multiple Gmail accounts at the same time.."
date: 2010-03-11
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-11
Is it possible to use multiple gmail accounts at the same time without using any firefox addons?

---

### Post by Temposs on 2010-03-11
Within one Firefox session, probably not, as Google will only allow you to be logged in as one user at a time in one browser. You would essentially have to trick Google into thinking you're using two separate browsers/computers.

---

### Post by ubudog on 2010-03-11
You could do it in evolution.  (I think)

---

### Post by Temposs on 2010-03-11
Of course, you could set up the Evolution mail client for two Gmail accounts. Then you could use both at the same time. But, you would have to be willing to use the Evolution program rather than the Gmail web-based client.

I use Evolution for my gmail and it works just fine :-)

---

### Post by ubudog on 2010-03-11
Evolution is nice, but I prefer using the web interface.  But if you need to access multiple gmail accounts, evolution is the way to go.

---

### Post by Paddy Landau on 2010-03-11
Alternatively, use two different browsers; Firefox for one account and Opera for another. Clumsy, I know, but I have no other solution.

---

### Post by Seq on 2010-03-11
Firefox profiles would solve this. `firefox -P` gets you to the profile manager. If firefox is already running it will try to start a new window in your current session, which is not what we want. To avoid that check, we need to add "-no-remote".

So run the profile manager:
```
firefox -no-remote -P
```

You can create and select profiles. Create a profile called "gmail2" or whatever name you would prefer. To run that profile directly:

```
firefox -no-remote -P gmail2
```

A good idea would be to use personas to give each profile a distinct look so you don't confuse them.

Alternatively, use thunderbird, evolution, or another mail reader. Much easier for handling multiple accounts.

---

### Post by lovinglinux on 2010-03-11
I know you don't want an extension, but I would recommend [Simple Mail](https://addons.mozilla.org/en-US/firefox/addon/5593). Simple Mail does not store each account messages on different folders, so it looks like a single account, but when you reply, it uses the correct sender for each account. It has imap support too and is very simple to configure.

---

### Post by karthick87 on 2010-03-12
What is personas?

---

### Post by karthick87 on 2010-03-12
> **Seq said:**
> Firefox profiles would solve this. `firefox -P` gets you to the profile manager. If firefox is already running it will try to start a new window in your current session, which is not what we want. To avoid that check, we need to add "-no-remote".

So run the profile manager:
```
firefox -no-remote -P
```You can create and select profiles. Create a profile called "gmail2" or whatever name you would prefer. To run that profile directly:

```
firefox -no-remote -P gmail2
```A good idea would be to use personas to give each profile a distinct look so you don't confuse them.

Alternatively, use thunderbird, evolution, or another mail reader. Much easier for handling multiple accounts.


Thanks a lot,this is what i want... :)

---

### Post by vinny@studo on 2010-03-12
you could get the gmail lab thing 'multiple inboxes.'  combine this with gmail's mail forwarding and you can have all your emails sent to one account.  there is also the option of choosing which account to send emails from.  all of this can be done within gmail very easily.

---

### Post by synicalx on 2010-03-12
I suppose another, potentially risky way of doing it would be to visit Gmail using a proxy site (as in ctunnel or something). As far as I know Google uses the IP address of your machine to give access to your account so if you were to visit Gmail with multiple IP's then you could theoretically login to multiple accounts I guess

---

### Post by Vaphell on 2010-03-12
using options by the web version of gmail you can have 1 central account and the rest attached to it, so they all forward mail to your main (in settings: add addresses to check with pop3 or something like that). To split emails up logically you can set up labels for each account and use automatic filters to apply proper label by destination address to every incoming message (all messages would be dropped into inbox otherwise).
Labels are listed on the left side with count of unread messages, so you see where the new stuff is at a glance. Filters are a cool tool and allow for easy sorting of mail. 1 message can be labeled with multiple tags so it's much more flexible than directory structure many other email clients use.
You can use any registered email address to be the origin of your new message (so you can have something other than your central address in the 'from' field), you just select proper one from dropdown list.
It's pretty straightforward once you look into it deeper.

---

### Post by Seq on 2010-03-12
> **getyourkarthick said:**
> What is personas?

Simple skins/themes for Firefox. I believe it is built-in to firefox 3.6 (which will be in 10.04), but available as an extension for the rest of us.

[http://www.getpersonas.com/]("http://www.getpersonas.com/")

My significant other uses those to keep her work firefox and home firefox separate, even though they reside in different user accounts.

---

