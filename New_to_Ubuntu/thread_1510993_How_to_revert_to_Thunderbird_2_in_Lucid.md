---
title: "How to revert to Thunderbird 2 in Lucid"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by ubume2 on 2010-06-16
I have Thunderbird 3 in my install of Lucid.  I am finding IMAP very frustrating, and want to revert back to Thunderbird 2 as was in my 8.04 9.04 and 9.10 install. [I don't want Thunderbird on my desktop to affect my gmail files and folders on the web]

I've tried compiling. I've installed all the packages necessary to compile, but can't get it to compile/install.  The make, configure files are not there.  I am new to compiling from source.

I really don't want to go back to 9.10, and I think thunderbird 3 is probably the default thunderbird mail client in 9.10 by now anyway. 

I've googled and searched but can't find a satisfactory answer.
Help appreciated.

---

### Post by maizuddin35 on 2010-06-16
how bout you just remove everything related to thunderbird3 and then install thunderbird2?

---

### Post by ubume2 on 2010-06-16
> **maizuddin35 said:**
> how bout you just remove everything related to thunderbird3 and then install thunderbird2?

I did remove thunderbird 3 and attempted to install thunderbird 2

---

### Post by maizuddin35 on 2010-06-17
what exactly the problem you're facing?

---

### Post by XubuRoxMySox on 2010-06-17
Three possible solutions:

**1.** - Just [COLOR="Purple"]change your account settings in Thunderbird 3 to POP3 instead of IMAP[/COLOR] (since you said you wanted to keep locally stored stuff on your computer from affecting what's on the web).

If it's Gmail you're using, simply change the incoming server to pop.gmail.com (SSL, port 995) and the outgoing server to smtp.gmail.com (also SSL) like it was in T-Bird 2.

IMAP is the default in Thunderbird 3 (and it does have some advantages), but POP3 sounds like what you want (and it's alot faster).

**2.** - As an alternative, [COLOR="Purple"]right-click on any folder you want to keep stored locally (like INbox), select *properties*, then *Synchronization*, and check the box marked *Select this folder for offline use[/COLOR]*. This downloads stuff to the folder(s) you selected. Those messages load instantly because they're stored on your own 'puter. So you get the speed of POP3!

**3.** - Thunderbird 2 is unavailable in the Lucid repos (and even in Karmic, updates to T-Bird 2 make it very much like T-Bird 3 anyway). But an alternative that works just exactly like the good ol' T-Bird 2 that we know and love, is [COLOR="Purple"]the SeaMonkey Internet Suite[/COLOR] (available in the Lucid repos). The browser and e-mail client are integrated, but when you open the mail it looks and acts just like T-Bird 2. 

The only thing about SeaMonkey is that some (very few) web sites balk at the browser, which is kinda outdated. It's like an older version of Firefox (and most Firefox extensions work on it).

Anywayz, there are three things you can try. I've got my T-Bird 3 working great using option #2 above.

Cheerfully,
Robin

---

### Post by maizuddin35 on 2010-06-17
sorry . I dont do much in thunderbird. i myself dont find it usefull enough to get my email from there.

---

### Post by ubume2 on 2010-06-17
> **dixiedancer said:**
> Three possible solutions:

**1.** - Just [COLOR="Purple"]change your account settings in Thunderbird 3 to POP3 instead of IMAP[/COLOR] (since you said you wanted to keep locally stored stuff on your computer from affecting what's on the web).

If it's Gmail you're using, simply change the incoming server to pop.gmail.com (SSL, port 995) and the outgoing server to smtp.gmail.com (also SSL) like it was in T-Bird 2.


Cheerfully,
Robin

I was having problems with error messages when I tried to get emails.
I uninstalled thunderbird 3 and reinstalled it.  I then placed the .mozilla_thunderbird file in /home/usr from an install of thunderbird 2 on a different partition, and it appears to have solved the problems.

Settings of my several gmail accounts are all pop now.  Originally, it wouldn't let me do that without getting all sorts of errors. In my web accounts I have IMAP on. No problem.

Thanks for help

---

### Post by XubuRoxMySox on 2010-06-17
Be sure to mark the thread as [SOLVED] then. You can do that by bringing up your original message and clicking on the Edit button to change the Subject line.

Thanks,
Robin

---

### Post by wjamoore on 2010-11-15
I think that is not solved.. that is a work around.

I need a reliable procedure to get back to Thunderbird 2.

T3 has just deleted a whole stack of my e-mail history and I have no idea why..  luckily I keep a backup, but this is really unnacceptable for someone like me running a small business.  Now I need to figure out how to get the old emails merged with the new ones...

Added to the message filters not working T 3 is a disaster

Some guidance greatly appreciated

AM

---

