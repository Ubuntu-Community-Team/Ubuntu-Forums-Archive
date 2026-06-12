---
title: "How do I consolidate multiple email accounts"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by NewBee2113 on 2010-03-16
Is there a program or a way to consolidate multiple email accounts into one spot.  I have email through my work (home business) that has multiple accounts that I am repsonsible for (General, Help,Contacts, Me, etc.)  then I have an old hotmail account I use for junk and ordering stuff online, or signing up for things (say fantasy baseball) so my other boxes do nto get slammed with junk.

Is there a way to get them all into one account, with one password,and maybe funnelled into different folders?

Any suggestions or how-to's.  I have evolution, and thunderbird, (but cannot figure out how to get them working.)  Not sure if my work email (it was offered through our webhosting uses SmarterMail 3.3.2543

thanks

---

### Post by lisati on 2010-03-16
A couple of options come to mind.

Some email providers let you automatically forward your email to another account. Gmail has this, and *some* Yahoo accounts can do this.

Some email providers let you automatically collect email from other accounts using "pop3" settings. I think Hotmail and some Yahoo accounts can do this.


I have most of my free Yahoo accounts forwarded to various accounts on my home server (running on my main desktop) which I then check with Thunderbird on my laptop. Using Postfix on my server lets me do some extra spam-proofing that's not so easily done with a regular email client such as Evolution or Thunderbird. (Running your own server is optional)

---

### Post by era86 on 2010-03-16
You can use Evolution to consolidate all of your email accounts.  You set up the pop3 and smtp on each one and let Evolution do the rest.  It will automatically check all your accounts and display any new messages from each.

If you're familiar with Outlook, it works pretty much the same way.

---

### Post by NewBee2113 on 2010-03-17
Cool, I will see if my email allows me to forward and then i can forward to Thunderbird or Evolution.

Do these have to be checked only on my home computer or can i check anywhere?  I sometimes travel for work

---

### Post by era86 on 2010-03-17
Well, if you forward all your accounts to Evolution, they would have to be accessed by that particular Evolution setup.  So, you wouldn't be able to access it on any other computers really.

If you forward your accounts to an existing online account like Gmail, then you will be able to check everything from that web account.

Goodluck

---

