---
title: "Thunderbirds file location"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by unknown user on 2010-01-11
I am looking to get a new Windows 7 laptop, but I will be having it as a duel boot with Ubuntu on it. I will be using Thunderbirds on both OS’s. 

Is there a way that I can direct both the Windows and Ubuntu systems to the same Thunderbirds file location’s so that I can open the same mailbox (etc) be it if I am in Windows or Ubuntu? This way I cam have the same settings, messages, contacts, that are up to date on either system I boot up in?

---

### Post by barnex on 2010-01-11
On ubuntu, mine is in .mozilla-thunderbird/. I would suggest to start thunderbird once in ubuntu. Then see if this directory gets created and if you can locate it (or perhaps a similarly named directory, depending on your thunderbird version). Then remove it again and replace it by a symbolic link to its windows counterpart.

This assumes you have your windows partition automatically mounted somewhere.

---

### Post by bug67 on 2010-01-11
This may or may not help.  I use MobileMe and Gmail for my email.  Those are both IMAP based protocols.  That way, no matter what operating system or email application on whatever system I am using, all my mailboxes are the same.  Hope some of this makes sense.

---

### Post by Excedio on 2010-01-11
> **unknown user said:**
> I am looking to get a new Windows 7 laptop, but I will be having it as a duel boot with Ubuntu on it. I will be using Thunderbirds on both OS&#8217;s. 
 
Is there a way that I can direct both the Windows and Ubuntu systems to the same Thunderbirds file location&#8217;s so that I can open the same mailbox (etc) be it if I am in Windows or Ubuntu? This way I cam have the same settings, messages, contacts, that are up to date on either system I boot up in?
 
I can't really help with this, however... I love that you said 'duel boot.' Makes it sound like Windows and Ubuntu are fighting with each other on your computer. :-D

---

### Post by barnex on 2010-01-11
> **Excedio said:**
> I love that you said 'duel boot.' Makes it sound like Windows and Ubuntu are fighting with each other on your computer. :-D

LOL, I saw this expression a few times before and always thought it was a typo. Turns out it was on purpose!

---

### Post by SecretCode on 2010-01-11
Keeping all your mail off the computer in Gmail would make this very easy.

However, that's not great for everyone.

I suggest this:
Run *thunderbird -profilemanager* (same syntax whether in win or ubuntu) and create new profile. Choose a folder location that both OSes can access - ie on a data partition.

On the other OS, do the same (create a new profile) and point to the same location. Even though the function is called 'create new' you will effectively be picking up the same profile.

I'm not sure, but you may run some risks with this. I would make sure you update thunderbird to the same level at the same time on both OSes. (Extensions aren't a problem; they are held in the profile and will automatically appear the same on both.) I would also back up the data assiduously!

---

### Post by oldfred on 2010-01-11
If you boot both windows and Ubuntu often you can have the same firefox and thunderbird data in a common partition.
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Firefox version 2 to 3 on both windows & ubuntu. 

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
More info:
    *  (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (SeaMonkey) ./seamonkey -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/shared/mozilla/thunderbird/profiles/lyu25irb.default

On the windows side the profile file is similar but uses the windows \  and f: drive(where windows sees the common partition).

---

