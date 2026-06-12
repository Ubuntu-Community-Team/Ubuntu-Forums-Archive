---
title: "why Ubuntu is acting weird?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by akohan on 2008-12-28
Hello group,

I just installed Ubuntu 6.06 I had the CD from past and now things look OK as far as veryh simple desktop but I'm not happy with it since there is no GCC, there is no MAKE command and ....

why is that? what is the beneifit of limiting Linux here?

what can I do to have gcc?


Thanks,
ak

---

### Post by pirattrev on 2008-12-28
> **akohan said:**
> Hello group,

I just installed Ubuntu 6.06 I had the CD from past and now things look OK as far as very simple desktop but I'm not happy with it since there is no GCC, there is no MAKE command and ....

why is that? what is the benefit of limiting Linux here?

what can I do to have gcc?


Thanks,
ak

Not exactly sure what your question is. Why did you install 6.06? And there is make and gcc in 6.06, so you can see why I might be a little confused...

---

### Post by jrusso2 on 2008-12-28
You have to install the build essential package to get those applications.  But I would get rid of 6.06 as its no longer supported and if the repository is still available it will not always be.

If you want the Ubuntu LTS download 8.04 or if LTS does not matter get 8.10.

---

### Post by pirattrev on 2008-12-28
ditto to the above dude

---

### Post by akohan on 2008-12-28
OK, thanks to everybody for your help. As soon as I did post the question I found it and added the packages I needed.


One question: when I installed Ubuntu 6.06 after reboot I got a message that there about 300 updates which I updated it. wasn't that enough? if not then how can I get the new version without messing with my current setting?

Regards,
amit

---

### Post by Michael.Godawski on 2008-12-28
hi akohan,

I guess it is not possible to upgrade from 6.06 dapper drake to the 8.+versions.

I would just download the newest version and burn a new cd/dvd and install fresh.

See here:

[LIST]
[*][http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)
[/LIST]
 > if not then how can I get the new version without messing with my current setting?

You can install a new version of Ubuntu without overwriting your personal data only if you have created a separate /home partition; did you ?

If not just grab all the files you might probably have on the drive on a cd or usb stick and install the 8.04 LTS or 8.10 version.

---

### Post by akohan on 2008-12-28
Hello Michael,

Thanks! so it seems you mean I have to download the new version and burn a CD and install from scratch. Right?

if not, the what is wrong with 6.06? is too old, missing some features?

Thanks.
ak

---

### Post by Michael.Godawski on 2008-12-28
> Thanks! so it seems you mean I have to download the new version and burn a CD and install from scratch. Right?

if not, the what is wrong with 6.06? is too old, missing some features?

Every new release is (should :P) much better than the last one, concerning the compatibility, usability and stability. Perhaps something went wrong during your installation, because the applications mentioned by you are essential to a working and successful installation.

What went wrong exactly, I cannot tell. But moving to the newer release, with more than 2 years of development between them, should make a difference.

---

### Post by akohan on 2008-12-28
That's right! now I'm downloading version 8.10 on current version. Can I burn CD in Ubuntu and replace it now?

Thanks.

---

### Post by arpanaut on 2008-12-28
6.06 is the previous LTS release, therefore it should have a direct upgrade path to Hardy aka 8.04. From a completely updated  6.06 system in update manager it should offer the upgrade to the new LTS.

Some prefer upgrade, some prefer fresh install.  From a fairly fresh 6.06 it "should" be pretty seamless.

I do believe that build-essentials has always bee a post install addition.  You can't put everything on the cd that one might expect to be using, or needing.

---

### Post by RomeReactor on 2008-12-28
Hi. As arpanaut says, you can [upgrade from 6.06 to 8.04]("https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS"). If you're having problems with Dapper, or if there isn't anything keeping you from a clean install, this would be a better option.

As for GCC and MAKE, they're not installed by default.

EDIT: Didn't see you're now downloading 8.10; just burn it and do a clean install.

---

