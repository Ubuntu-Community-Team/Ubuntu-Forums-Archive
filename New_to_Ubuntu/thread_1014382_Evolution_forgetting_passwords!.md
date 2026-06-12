---
title: "Evolution forgetting passwords!"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by geo316 on 2008-12-17
It seems almost random, the dialog to enter pop3 passwords keeps popping up. I re-enter the password and sooner or later the same dialog pops up again prompting for the password. It sometimes happens again within minutes, sometimes hours.

I have about 5 email accounts, all of them at one time or another need the password re-entered.

its driving me nuts! I recently upgraded to intrepid, I currently have evolution 2.24.2.

I've been googling for a day now trying to find the answer - or at least someone with the same problem. I found a few posts but they either had no solution or one that didnt work for me. Most folks are griping about webcal passwords being forgotten but not pop3 passwords...

HELP! :confused:

---

### Post by Hospadar on 2008-12-17
Well, I know it's not the solution you're looking for, but you might just try using thunderbird instead of evolution.  If you install the thunderbird addon "lightning" it gives you calendar support as well.  The only thing I think you really loose is new email notification in the tray when you have yet to open up your mail client (once thunderbird is open it gives you alarms)

---

### Post by GrouchoMarx on 2009-01-28
Yeah, I'm experiencing the same annoying problem. If you (or anyone) figure(d) out why it's happening, please let us know!

---

### Post by geo316 on 2009-02-05
Not long after posting this (and receiving an underwhelming amount of replies!) I decided to switch to Thunderbird. I love the filters, and it seems to be exceptional at filtering spam - everything else is either a yawn or not as ergonomic (read: comfortable for an ex-outlook lover). I've been happily living with it though.

I wanted to report that it too forgets passwords. Every now and again I randomly get a dialog asking for the password of 1 or more my email accounts, it also asks if I want password manager to remember it. 

Regardless of how many times I answer yes the dialog randomly comes back.

Could the forgetting of passwords not be an evolution or a t-bird thing but an Ubuntu 8.10 thing?

---

### Post by geo316 on 2009-02-21
not that anyone seems to be relating... but after using thunderbird for a while, then switching to claws, I am now convinced that Evolution is best suited for me - except that the problem mentioned originally persists...

I tried re-installing Evolution and so far that hasn't fixed anything... guess I have to live with it until elves come in to my office at night and fix it for me...

Please, if anyone has had a similar problem and found a fix please share!

---

### Post by chamber on 2009-02-21
What are the e mail accounts?  Evolution has no problems with my gmail account.

---

### Post by geo316 on 2009-02-21
> **chamber said:**
> What are the e mail accounts?  Evolution has no problems with my gmail account.

All 5 are pop3...

---

### Post by gandaran on 2009-02-21
> **geo316 said:**
> It seems almost random, the dialog to enter pop3 passwords keeps popping up. I re-enter the password and sooner or later the same dialog pops up again prompting for the password. It sometimes happens again within minutes, sometimes hours.

I have about 5 email accounts, all of them at one time or another need the password re-entered.

its driving me nuts! I recently upgraded to intrepid, I currently have evolution 2.24.2.

I've been googling for a day now trying to find the answer - or at least someone with the same problem. I found a few posts but they either had no solution or one that didnt work for me. Most folks are griping about webcal passwords being forgotten but not pop3 passwords...

HELP! :confused:
are you talking about the keyring password or email passwords?
have you checked on the emails pop3 setup if the remember password box is ticked?

---

### Post by geo316 on 2009-02-21
> **gandaran said:**
> are you talking about the keyring password or email passwords?
have you checked on the emails pop3 setup if the remember password box is ticked?

Email password dialog, Password box is definitely ticked... I first started using Ubuntu last summer... up until December Evo worked fine...

---

### Post by gandaran on 2009-02-21
well, why not backup your emails then delete all evolution configuration folders (home/user/.evolution and home/user/.gconf/apps/evolution) then start all over again with a fresh setup?

---

### Post by geo316 on 2009-02-21
> **gandaran said:**
> well, why not backup your emails then delete all evolution configuration folders (home/user/.evolution and home/user/.gconf/apps/evolution) then start all over again with a fresh setup?

I did an uninstall from synaptic... I did not delete the directories you mentioned however...

will try and report back when I get a few minutes...

thanks

---

### Post by gandaran on 2009-02-22
geo316
I now have the same problem! I changed all my email passwords and now it won't remember the typed new passwords, well the fix was easy, go to applications>accessories>keyrings>password tab and delete all email entries, close the application and start evolution, type the password, it will remember them now!

---

### Post by geo316 on 2009-02-24
Gandaran,

Thanks so much for the two suggestions but neither worked for me. In fact, since I've completely re-installed evolution and re-set up my email accounts I find that in addition to the password forgetting issue evolution randomly crashes every now and then.

Oh well... guess I have to live with it until someone creates a comparable outlook like email app... or maybe it will fix itself in the next release of ubuntu...

Again, thanks!

---

### Post by blueridgedog on 2009-02-24
You may not get many replies in the absolute beginner talk forum, as your issue has no simple fix.  I suggest you start a bug report for evolution in Ubuntu:

[https://bugs.launchpad.net/ubuntu/+source/evolution/](https://bugs.launchpad.net/ubuntu/+source/evolution/)

---

### Post by ChrisNZ on 2012-08-29
Please consider this post closed and fine newer ones. I've had the same problem although I actually like Evo, it has its moments like all others...;-)

---

