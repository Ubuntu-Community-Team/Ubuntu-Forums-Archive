---
title: "Howto install wine in 9.10"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Petu on 2009-11-23
I installed Ubuntu 9.10 from CD. Now I'm trying to get wine installed. In Software Sources I have
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main
and it's ticked.
I can find wine from the Synaptic Package Manager. I mark it for installation and it gives me an error:
"Could not mark all packages for installation or upgrade"
"The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences"
Then it has only following in the list
wine:
That's it "wine:"!

Any suggestions how to proceed?

---

### Post by lhb1142 on 2009-11-23
The first thing I would try would be to follow all the instructions contained in the "Comprehensive Multimedia & Video Howto" here

< [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) >

ESPECIALLY the Medibuntu installation instruction but also enabling the Multiverse and Universe sources.

Make certain that you follow the instructions for 'Karmic' - they will be labeled 9.10 or 9.04 and above. Use only the instructions so labeled.

Once you have all of that done, I think that when you go into the Synaptic Package Manager and search for Wine, you will find it and the installation should proceed smoothly.

Should there be some problem (highly doubtful), try installing Ubuntu Tweak < [https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2) >. (Actually you ought to install it anyway, even if the above instructions work perfectly - Ubuntu Tweak is a great and VERY useful program).

Once Ubuntu Tweak is installed (you'll find it under Applications -> System Tools), go to its Applications section and click on Add/Remove. (You may have to enter your password.) Scroll down until you see "Wine Microsoft Windows Compatibility Layer" and check mark it. This should install Wine.

I hope the above is of some help to you. ):P

---

### Post by Petu on 2009-11-23
I did all of the above. Everything went fine. Then I tried to install Wine from Synaptic Package Manager, same result as earlier.
Then I went to Ubuntu Tweak, selected Wine, and pressed Apply... and it tells me:
"Could not apply changes! Fix broken packages first."
So I have broken packages?! Suggestions?

---

### Post by MelDJ on 2009-11-23
go to synaptic, click edit and press fix broken packages

---

### Post by Petu on 2009-11-24
Went to Synaptic, selected "Fix Broken Packages", it says "Successfully fixed dependency problems"

Still same problem. Any other thoughts?

---

### Post by MelDJ on 2009-11-24
do you mean the broken package problem is solved?

if it is, try installing wine through the steps here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
remove the wine ppa you have in your sources first

---

### Post by 3rdalbum on 2009-11-24
Have you enabled the Multiverse repository from the Software Sources program?

---

### Post by mc4man on 2009-11-24
Go to System -> Admin. -> Software Sources and make sure the 1st 4 boxes are checked (enabled) under Ubuntu software. Also make sure the 1st. 2 are enabled under the Updates tab.

If you had to ck. any of them then click close and reload.
( if you didn't then after closing, in a terminal go
```
sudo apt-get update
```

Then in a terminal
```
sudo apt-get install wine1.2
```

If it doesn't install post complete terminal output

---

### Post by Petu on 2009-11-24
No, the broken package issue was still there. But now I took the Wine ppa away from Synaptic as suggested, then used Ubuntu Tweak to install Wine, and it worked!
So for a reason or another I guess there was something wrong with the "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main"?

Thanks to you all, issues solved.

---

### Post by XCan on 2009-11-24
Perhaps, but I don't see the reason to use the ppa, WINEHQ has their own repository which I've been using for ages flawlessly.

---

### Post by mc4man on 2009-11-24
> something wrong with the "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main"?

No, that ppa is fine, maintained by Scott Richie who does most of the ubuntu wine builds.

> Perhaps, but I don't see the reason to use the ppa, WINEHQ has their own repository

The link for the ppa in post 1 is the repo for **karmic** from winehq
> 
For Ubuntu Karmic (9.10):
ppa:ubuntu-wine/ppa

---

### Post by joshzam on 2009-12-11
How to install wine in 9.10: don't.

Install wine1.2 instead.

---

### Post by Brownting on 2009-12-17
Ok same problem here broken packages wont install.  I tried fixing all broken packages same message tried using terminal here is my output.

code:
[FONT=monospace]sudo apt-get update

[sudo]password for mike:

its blank and will not let me input any info, the next cmd my password or anything its just blank and untypeable.  any help?  also tried installing the tweak but am having an issue not really worried about that I would just like to get wine working!
[/FONT]

---

### Post by Brownting on 2009-12-17
ok so apparently i could enter my password it just wasnt showing up after entering password output i got was:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


so having no idea what that meant, I decided to take above advice and install wine1.2 ill try this out untill i hear further what to do.

---

