---
title: "why is postfix installed?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by occams_beard on 2010-02-17
I just had an update from the update manager, and the postfix mail server was included. which is odd because I don't ever remember installing postfix.

Anyway, during the install, a dialog box popped up and asked something about what kind of configuration I wanted.  Not having any idea, I selected "no configuration" from the combo box.

So why is postfix installed, and what should the configuration be?

---

### Post by SmileyChris on 2010-02-17
Same issue here.

Looking in aptitude, it looks like that the "lsb-core" package depends on "mailx" and "postfix".

UPDATE: which, in turn, looks like it is a dependency of "google-chrome-beta". So I'm guessing it's google chrome being updated which caused lsb-core to be added and therefore postfix.

---

### Post by SmileyChris on 2010-02-17
My suggestion is to do what I have just done: avoid setting up "postfix" by explicitly installing the "ssmtp" package.

You can do this on the command line via "sudo aptitude" or in gnome by going to System > Administration > Synaptic Package Manager.

Or uninstall chrome - but I couldn't bring myself to do that :)

---

### Post by occams_beard on 2010-02-17
> **SmileyChris said:**
> Same issue here.

Looking in aptitude, it looks like that the "lsb-core" package depends on "mailx" and "postfix".

UPDATE: which, in turn, looks like it is a dependency of "google-chrome-beta". So I'm guessing it's google chrome being updated which caused lsb-core to be added and therefore postfix.

That's strange, why would chrome have those as dependencies.  That's pretty weird.

---

### Post by mahousaru on 2010-02-18
Well that made for a nice wake up call....  Lucky most of the people I converted to Ubuntu don't use chrome, but one did...  To answer the ops question, if you want a working postfix, but not opened to the whole world then I believe you want to localhost profile.  

From what I can see the main culprits that chrome puts down are build-essential and mailx.  Whilst there is nothing wrong with a well configured mta on a system, do we really need it?  Badly configured it breaks a part of the security behind ubuntu, which is to not expose ones bottom to the world via services.  

Feels like the chrome release dev didn't do a proper ubuntu release...

If you want to remove all the additional apps (you will need to remove chrome), you can see what was newly installed from the log file:

/var/log/apt/term.log

The section will have a time stamp of when the install started, then you have to look for anything with:
Selecting previously deselected package xyz.

then you can build up a space separated list and do a 

sudo apt-get remove --purge {space separated list with no brackets}

It will ask you to confirm the number of packages that you wish to uninstall, so check carefully.  For example the libxml2 package is updated this time around and trying to uninstall it will try to uninstall your desktop :p

The one I just fixed had 42 additional packages including chrome.

---

### Post by occams_beard on 2010-02-18
> **mahousaru said:**
> 
From what I can see the main culprits that chrome puts down are build-essential and mailx.  Whilst there is nothing wrong with a well configured mta on a system, do we really need it?  Badly configured it breaks a part of the security behind ubuntu, which is to not expose ones bottom to the world via services.  



I was thinking the same thing. I realize it is a dependency of another package, but I don't think most Ubuntu users need or want postfix on their system.  I wonder if Google knows this happens on buntu.

Ah well, I guess it's labeled beta for a reason. Bummer cause I really like chrome.

---

### Post by mahousaru on 2010-02-18
> **occams_beard said:**
> 
Ah well, I guess it's labeled beta for a reason. Bummer cause I really like chrome.

They know the problem exists...

[Link to Chrome release comments]("https://www.blogger.com/comment.g?blogID=8982037438137564684&postID=6865604126599305350&isPopup=true")

"Evan said...

    The package deps were an oversight and will be fixed in the next release."

---

### Post by mikewhatever on 2010-02-18
Actually, I was slightly shaken seeing the number of dependencies the new google-chrome required. 32 altogether. I went for complete removal instead. Guess the same guys are responsible for google chrome and google buzz. ;)

---

### Post by occams_beard on 2010-02-18
So what is the best way to purge Chrome and all the unecessary dependencies it pulled in?

---

### Post by mikewhatever on 2010-02-18
You can uninstall everything from Synaptic.

---

