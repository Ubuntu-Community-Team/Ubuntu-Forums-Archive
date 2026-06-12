---
title: "Gwibber Won't Add, Resizes a lot"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by powersurge360 on 2010-04-29
I can't add any profiles into Gwibber. It won't let me click the add button and whenever I click anywhere in the Gwibber box (at all) it resizes sporadically.

Terminal said:

** (gwibber:3940): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3940): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3940): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'


Suggestions?

---

### Post by Kafubie on 2010-04-29
Whenever I try and add one of my facebook accounts.  I "add" it then it says success.  Then it doesn't put it on the little sidebar.  The empathy client is working for me though.  I still wanna see status's and crap.  I NEED HALP!

---

### Post by jascayne on 2010-05-01
I'll join the parade of users having problems with gwibber... I can add my twitter account just fine, but I can't add a facebook account. If I try launching gwibber from the terminal, I see a whole mess of errors popping up:

```
** (gwibber:24203): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:24203): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:24203): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...

** (gwibber-accounts:24246): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:24246): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:24246): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Saving...
Could not identify preference: username
Could not identify preference: session_key
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/accounts.py", line 184, in on_edit_account_save
    self.get_account_data()
  File "/usr/lib/python2.6/dist-packages/gwibber/accounts.py", line 353, in get_account_data
    aId = "%s-%s" % (self.account["protocol"], self.account["username"])
KeyError: 'username'
```

---

### Post by donsmi on 2010-05-01
I am have tried on 2 different clean installs to register my wife's account, and it wouldn't work. I was stuck on the Add button. Everything else with Facebook would confirm, but then I could not Add the account.
Strangely, my account was added to both clean installs easily.

---

### Post by makushimu on 2010-05-02
I have the same issue with trying to register FB.

---

### Post by svetlisashkov on 2010-05-16
I'm in the same situation on three different systems...

---

### Post by amandakay on 2010-05-21
I was having similar problems, but today was able to fix things enough to post to Facebook and view messages, etc.

I updated Lucid using the Update Manager (rather than waiting for prompts to update). After this, I was able to successfully add my Facebook account to Gwibber.

At first I did have issues where it seemed my facebook updates weren't being registered, though I discovered afterwards these were mistakenly added to one of my Twitter accounts (though I had explicitly chosen to update with Facebook each time).

To resolve this, I disabled "post messages" for that Twitter account and made sure the settings for my FB account enabled me to post. Since then all has been working just fine.

Hope this may help others solve the issue too - I was incredibly frustrated at being unable to use this feature until now - it's one of the things which excited me most about Lucid!

---

### Post by Pepe Lebuntu on 2010-07-03
I join the heap of people sick to death of this absolutely abysmal program.

---

### Post by surja on 2010-07-09
same here.. this program was hyped quite a bit when Lucid was released.. but its never worked properly for me. I just cannot add any account even after updating.

---

### Post by maubp on 2010-09-10
> **powersurge360 said:**
> I can't add any profiles into Gwibber. It won't let me click the add button and whenever I click anywhere in the Gwibber box (at all) it resizes sporadically.

I couldn't add facebook until I first added my twitter account (which prompted to unlock my gnome keyring). See also:
[https://bugs.launchpad.net/gwibber/+bug/595265](https://bugs.launchpad.net/gwibber/+bug/595265)

I also got annoying resizes while trying to add accounts - the bottom of the window frequently was off my screen.

---

### Post by Clever_Username on 2010-09-10
Same problem here.

---

### Post by Allu2 on 2010-09-23
Another one with same problem, i solved it on my laptop by installing (lot) older release of gwibber from debian repos and then registering and all and after upgrading to ubuntus version (kept the login details )

---

### Post by 0N3 on 2010-09-26
I had the same problem first you need to remove gwibber from the start up section then log into facebook
Go to Account > Privacy Settings > Applications and Websites > Edit your settings
Remove Gwibber
Start the gwibber process again and add it to Facebook and authorise it
Quit Gwibber and redo the adding process then in the left hand pain click the add button and you should be working

---

### Post by ThrobbingBrain66 on 2010-10-06
All you guys having issues adding Facebook to Gwibber should try the following:

Install python-facebook from the repositories.  I was having issues too and as soon as I did this, everything worked just fine.

---

### Post by barretme on 2010-10-07
I had a similar problem as some others, where Facebook wasn't adding. It hardly updates also. It's a cool idea, but really frustrating and disappointing.

I'm running Maverick on a Macbook 3,1.

---

### Post by freacert on 2010-10-09
> **ThrobbingBrain66 said:**
> All you guys having issues adding Facebook to Gwibber should try the following:

Install python-facebook from the repositories.  I was having issues too and as soon as I did this, everything worked just fine.

no luck for me..

---

### Post by ThrobbingBrain66 on 2010-10-10
> **freacert said:**
> no luck for me..

Did you then close Gwibber down completely?

---

### Post by freacert on 2010-10-11
> **ThrobbingBrain66 said:**
> Did you then close Gwibber down completely?

yes, killed all the processes, and tried many other things. 
Almost sure the problem lies on the facebook side as subscirbed in various threads at launchpad. Because sundaymorning all of sudden, when starting up the computer sand gwibber starting up automatically, the add button appeared.

---

### Post by NightwishFan on 2010-10-11
I am unable to use gwibber with facebook either. It just never adds the account. :(

---

### Post by ghost46 on 2010-10-16
> **ThrobbingBrain66 said:**
> Did you then close Gwibber down completely?


this was the fix in my case.  accolades to throbbingbrain  #-o

---

