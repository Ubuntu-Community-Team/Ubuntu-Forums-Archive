---
title: "Wine is not lauching .exe"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by RaceNChase on 2010-04-10
Hello,

I am new to Ubuntu but have a friend assisting me, I am using 10.4 beta 2 as it is an LTS and should be finalized at the end of the month.  

I am using Wine to utilize some windows applications but when I click on an .exe I get the following error

"The file '/home/Name/Downloads/Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

My friend said it should just auto launch the program but it doesn't I even right clicked it and manually clicked on open with WINE but I receive the exact same error.

Help, please and thank you.

---

### Post by WinterRain on 2010-04-10
Just right click the file and go to properties > permissions tab. There should be a box to check off to make it executable. ("allow executing file as program")

---

### Post by arnab_das on 2010-04-10
> **RaceNChase said:**
> Hello,

I am new to Ubuntu but have a friend assisting me, I am using 10.4 beta 2 as it is an LTS and should be finalized at the end of the month.  

I am using Wine to utilize some windows applications but when I click on an .exe I get the following error

"The file '/home/Name/Downloads/Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

My friend said it should just auto launch the program but it doesn't I even right clicked it and manually clicked on open with WINE but I receive the exact same error.

Help, please and thank you.

this is a problem with the latest version of wine. i would suggest that you regress/downgrade to an older version. that will solve your problem.

to install an older version check out this link in the official wine page: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

as mentioned in the link, add the repositories, and finally via synaptic downgrade to an earlier version.

(just for ur reference: current version of wine is 1.1.41 or 1.1.42 while in my opinion, the last 'proper' version was 1.1.36, the version which was default in 9.10)

---

### Post by WinterRain on 2010-04-10
> **arnab_das said:**
> this is a problem with the latest version of wine. i would suggest that you regress/downgrade to an older version. that will solve your problem.

to install an older version check out this link in the official wine page: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

as mentioned in the link, add the repositories, and finally via synaptic downgrade to an earlier version.

(just for ur reference: current version of wine is 1.1.41 or 1.1.42 while in my opinion, the last 'proper' version was 1.1.36, the version which was default in 9.10)

No need for that. See my post above.

---

### Post by _h_ on 2010-04-10
> **arnab_das said:**
> this is a problem with the latest version of wine. i would suggest that you regress/downgrade to an older version. that will solve your problem.

It's not an issue with Wine at all, it's just that what he downloaded wasn't marked as an executable first. Ubuntu side, not Wine side.

---

### Post by arnab_das on 2010-04-10
> **_h_ said:**
> It's not an issue with Wine at all, it's just that what he downloaded wasn't marked as an executable first. Ubuntu side, not Wine side.

oh my bad then, well i couldnt launch an exe file when i had 10.04 beta installed, the problem was gone when i downgraded. i also could run quite a few more games like my older NFS etc on the 9.10 version.

---

### Post by RaceNChase on 2010-04-10
thank you so much for the quick replies.  I greatly appreciate your fast assistance.

---

### Post by RaceNChase on 2010-04-14
after several days of fighting this,  I too used a regression, I could not get Runes of Magic to play with the current version even when using Play On Linux.

---

### Post by Hman242 on 2010-04-17
> **WinterRain said:**
> Just right click the file and go to properties > permissions tab. There should be a box to check off to make it executable. ("allow executing file as program")
Hate to bring up an old thread, but I need some help. When I try this, is says I don't have permission to do this.

---

### Post by Paqman on 2010-04-17
> **Hman242 said:**
> Hate to bring up an old thread, but I need some help. When I try this, is says I don't have permission to do this.

Check who owns the file. Anything that's downloaded by you into your /home should be owned by you, but if it's not the quickest way to sort it is:
```
sudo chown username /path/to/file
```

---

### Post by techno-mole on 2010-04-17
I am having the same issue on lucid beta 2 with wine - 1.1.42-0ubuntu2 I am unable to install adobe elements 6 because the executable isn't trusted, but I am unable to change the permissions as the disc is not writable.

I have tried copying the contents of the disc to my home folder, but then I have other errors that prevent installation, so I guess downgrading is my only option at this point.

---

### Post by mc4man on 2010-04-17
There are several ways around installing from a cd, ranging from using a terminal command, creating a new wine launch command to creating an fstab entry for your drive.

Some are shown here post #11 also
[http://ubuntuforums.org/showthread.php?p=9121470#post9121470](http://ubuntuforums.org/showthread.php?p=9121470#post9121470)

I'd go with either the terminal method or new right click/left click launcher over an fstab entry

(if not clear then just ask

---

### Post by Mark Phelps on 2010-04-18
Your installation is likely to be NOT worth the effort.  Take a look at the page below from the WineHQ site rating application compatibility with Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1794]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1794")

The Elements versions are mostly Bronze -- only one step up from Garbage.  You should click on the test results on the right side of the page to read the details to see if the features you want to use actually work.

---

