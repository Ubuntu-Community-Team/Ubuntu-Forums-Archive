---
title: "Firefox does not save cookies even though it's checked in preferences"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by psam3 on 2009-03-23
This seems to be a problem I have with Ubuntu and Firefox. When I had Ubuntu installed in my machine last year I remember having the same problem and now today I'm having problems with websites because they require them to be enabled. I checked in Firefox and it says they are enabled. Is this some kind of glitch or am I just missing something? I do not have this problem with Firefox in Windows.

---

### Post by Chemical Imbalance on 2009-03-23
Look under "Keep until"...what does it say in your preferences?

It should say (in your circumstance) until "they expire".

---

### Post by psam3 on 2009-03-23
Until they Expire

---

### Post by Chemical Imbalance on 2009-03-23
What about your private data section?  Do you have it set to wipe your history on close?  (Check settings and make sure cookies is unchecked in this section)

---

### Post by psam3 on 2009-03-23
Everything checks out good. I'm not sure why it does this but this may be related, last night I temporarily turned off the pop up blocker but it apparently would not save. I had to go into preferences and turn it off for all websites and restart Firefox to get it to work, also, while on a certain site, after entering my username I have to verify my computer by entering a secret question and it's supposed to save my computer, but it never does.

---

### Post by Chemical Imbalance on 2009-03-23
Hmmm, I'm puzzled also then.  Do you have any add-ons that have anything to do with Cookies/History or anything related?

---

### Post by psam3 on 2009-03-23
Nope, just themes. I appreciate you trying to help though.

---

### Post by kerry_s on 2009-03-23
check your hidden ~/.mozilla folder make sure you own it and have read & write permission.
open the file manager, press ctrl+h to see hidden, right click the folder> properties

and never ever run your firefox as root.

---

### Post by psam3 on 2009-03-23
> **kerry_s said:**
> check your hidden ~/.mozilla folder make sure you own it and have read & write permission.
open the file manager, press ctrl+h to see hidden, right click the folder> properties

and never ever run your firefox as root.

Could you please explain what you mean by running Firefox as root? How would you even do that? Not that I'm trying to, just curious.

---

### Post by Chemical Imbalance on 2009-03-23
(dont run this command please)
> gksudo firefox
(dont run this command please)

in terminal will run it as root, but since you had to ask I'm assuming you are not doing that. ;)

---

### Post by kanikilu on 2009-03-23
> **kerry_s said:**
> check your hidden ~/.mozilla folder make sure you own it and have read & write permission.
open the file manager, press ctrl+h to see hidden, right click the folder> properties

and never ever run your firefox as root.Agreed, this sounds like a possible permissions problem to me. If you don't already know how to check, go to Places > Home Folder, then go to the View menu and make sure Show Hidden Files is checked. Then right click on the .mozilla folder and select Properties. The permissions tab should tell you what you need to know. Just see if it's owned by you and if you have read and write access.

If it is owned by root, you'll probably need to use the command line to fix it. Go to Applications > Accessories > Terminal. The steps are:

1) Make sure you are in your home directory
2) Change ownership of your .mozilla folder
3) Change permissions of your .mozilla folder

```
cd ~
sudo chown -R username:groupname .mozilla
chmod -R 700 .mozilla
```

Obviously put in your username, and your primary group is generally the same as your username unless you specifically changed it. Enter your password when prompted to, nothing will be echoed to the screen, so just type it and press enter.

---

### Post by psam3 on 2009-03-23
> **Chemical Imbalance said:**
> (dont run this command please)

(dont run this command please)

in terminal will run it as root, but since you had to ask I'm assuming you are not doing that. ;)

Of course not :p

---

### Post by psam3 on 2009-03-23
I have my username as the owner, and they were all blank so I changed them to create and delete files, did I do the right thing?

---

### Post by psam3 on 2009-03-23
It seems to be working now, thanks everyone.

---

### Post by Chemical Imbalance on 2009-03-23
> **psam3 said:**
> It seems to be working now, thanks everyone.

I wonder how your permissions got changed...

Did you install firefox from the repos or from mozilla.org?

---

### Post by psam3 on 2009-03-23
> **Chemical Imbalance said:**
> I wonder how your permissions got changed...

Did you install firefox from the repos or from mozilla.org?

It was pre-installed and I think it might have updated once, but I never touched it.

---

