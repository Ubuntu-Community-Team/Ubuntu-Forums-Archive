---
title: "errors with libc6 2.9-25"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by VideoAddicted on 2009-09-11
i am frantically attempting to successfully install wine.  when i attempt to install from synaptic package manager, i am told that i need libc6 2.9-25, and i only have libc6 2.7.  So, i attempted to download libc6 2.9-25 and was told i needed libc-bin, which when downloaded and installed said 'Installation Finished' and 'Failed to Install libc6 2.9-25.  No matter which mirror i attempt to download the file from, i get the same error.  also, when i check the terminal information, no text appears.  does someone know what i need to do to get this to work?

---

### Post by j7%&lt;RmUg on 2009-09-11
What version of ubuntu are you running, because i just checked my ubuntu 9.04 machine and i have libc6-2.9-4.

to install wine just type this in a terminal:

sudo apt-get install wine

Should install, all i ask is that you dont panic and try to download 20 different code libs off the net, everything you need should be in synaptic package manager.

---

### Post by mc4man on 2009-09-11
If you are running hardy, (which it appears so) then you should probably stick with hardy repo's.
If this is the case, (on hardy) then you added a jaunty repo (for wine..? 

You could have just added the hardy wine repo or downloaded a wine version from here. (for hardy
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Otherwise, if you're determined to use jaunty system libs then save yourself some grief and upgrade to or do a fresh install of jaunty

edit:
 or have you added a debian repo for wine ..?(squeeze uses libc6 2.9-25

OR are you running debian in the first place (lenny

---

### Post by VideoAddicted on 2009-09-12
i tried getting wine from the webpage you suggested mc4man, however, now i cannot access synaptic, add/remove applications, or update manager, introducing a whole new problem.  Do you know why this happened and how i can fix it?

---

### Post by mhgsys on 2009-09-12
what happens when you try ;
```

sudo apt-get update

```

in a terminal?

---

### Post by mc4man on 2009-09-12
You really should post what are you running, ubuntu (hardy..?) or debian.

The 2 packages you've mentioned are debian packages, i don't believe there is a libc-bin in ubuntu

Maybe post your sources list
```
cat /etc/apt/sources.list
```

Edit
if you are on ubuntu, then installing libc-bin from debian (if that's what you did), would have been a very poor idea

---

### Post by VideoAddicted on 2009-09-12
i am using 8.04. i'm not sure about libc-bin, but in synaptic, i was told that i had libc6 2.7 and that i needed 2.9, so i think that i still need libc6 update.

---

### Post by mc4man on 2009-09-12
> but in synaptic, i was told that i had libc6 2.7 and that i needed 2.9, so i think that i still need libc6 update. 

Well one is free to do as they please. Your best bet for salvaging this install, (if still possible), is to remove any debian or debian/wine repo sources, try to remove libc-bin, if successful do an ldconfig  and then do an apt-get update.
Installing a higher libc6 version than the release version is problematic, installing a higher version from another distro is even more so. 

You've already installed a glib utils package that's causing issues.

As mentioned post your sources.list if unsure of what to disable/remove

---

### Post by VideoAddicted on 2009-09-12
i ran sources.list and got the following, i dont know if it means anything, it sure doesn't mean anything to me.




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by mc4man on 2009-09-12
The contents of your sources.list and this statement aren't making a whole lotta sense
> i am frantically attempting to successfully install wine. when i attempt to install **from synaptic package manager**, i am told that i need libc6 2.9-25

Did you at any point add a repo for wine in some manner?

If you can open System -> Admin.. -> Software Sources -> Third Party is anything listed?

What does this show, if anything?
```
ls /etc/apt/sources.list.d/*.list
```

Or did/were you simply trying to install a wine .deb that you downloaded

---

### Post by VideoAddicted on 2009-09-12
firstly, could you clarify what a 'repo' is, i am truly just a noob seeking guidance.

secondly, when i entered the suggested code, the followed emerged


/etc/apt/sources.list.d/winehq.list

---

### Post by mc4man on 2009-09-12
> firstly, could you clarify what a 'repo' is
A repo is short for repository , which is a 'pool' of packages that you can install, have installed from.
Refer back to your sources.list and you'll see all the standard ones you're using for hardy.
(( you'll also notice 2 from fiesty that are commented out (#), meaning they are no longer used, and should stay that way.

You can also add 'outside sources' (aka repo's) to draw upon a larger pool of packages, sometimes newer, sometimes not available in the standard repo's for the release you're using.
Typically these are known as 3rd Party sources.

Where you can get into trouble is if you add a repo or repo's from a release other than the one you've installed, for instance, in your case of using hardy, adding an intrepid or jaunty repo.

Where you will most definitly get into trouble is when you add a repo from another distro, in this case debian. While ubuntu is debian based it uses different package versions, names, and in some cases, libraries.

It appears that you went to winehq or copied a command from somewhere that added the wine debian repo and the resultant package dependencies ( probably debian squeeze) to your lists of available packages.

That's why you were prompted to install a package that doesn't exist in ubuntu.
At that point nothing was really wrong (borked), wine just would'nt install, no big deal. You could have just removed the wine/debian source listing, added the proper ubuntu/hardy one and installed the latest wine for hardy.

It appears though that you went ahead and found and installed a debian package that doesn't belong on your install and could cause some real issues. (libc-bin

What exactly is your current state? (you mentioned no synaptic, ect.

Could you go to System -> Administration -> Software Sources -> third Party and see if there is a winehq listing. If so disable it, click close, reload and see what happens.

you'll need to remove that libc-bin in some manner, what I'm not sure quite yet 

( possibly 
sudo apt-get remove libc-bin

---

### Post by VideoAddicted on 2009-09-12
i removed the jaunty version of wine and can now successfully access synaptic, etc.  

two questions,

1. do i still need to remove libc-bin?

and2. do you know where i can get a hardy version of wine that i can use successfully?

---

### Post by mc4man on 2009-09-12
> w where i can get a hardy version of wine that i can use successfully?
from the link in post 3, scroll down the page a few inches

> do i still need to remove libc-bin

I'd vote no, if it was even actually installed. Personally not really sure what you did or didn't do so I'd leave well or not well enough alone/

From your prior posts if seemed likely you were trying to install this libc6 which does have a depend of libc-bin

[http://packages.debian.org/squeeze/libc6](http://packages.debian.org/squeeze/libc6)

Now your mentioning jaunty or whatever

---

### Post by VideoAddicted on 2009-09-13
thanks alot, that has fixed all of my errors

---

