---
title: "This version of the clamav engine is outdated"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by ifindcomputersreallyhard on 2009-03-26
Greetings.

Trying to update clamav (using the apt-get install clamav and so on in terminal), I receive the message:

This version of the clamAV engine is outdated. DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq).

For all the good that did me, it might as well have been written in Martian.

Could anybody give instructions, in really simple English, which will enable me to install the latest antivirus engine?

One of the problems with trying to move to Linux is that most of the instructions I find seem to presuppose a reasonable knowledge of the OS. This is tricky for those of us who've barely learned to find our way round Windows.

I apologise if this topic has been covered elsewhere - to be honest, I still haven't got the hang of navigating the forum - although I did try to look for previous posts.

I'll certainly look in a little later in case any kind soul has found time to respond. Thanks in advance.

---

### Post by albandy on 2009-03-26
sudo freshclam
this will update your clamav signatures

---

### Post by ifindcomputersreallyhard on 2009-03-26
Thanks, Albandy.

The virus signatures are updating fine, fortunately.

The ClamAV GUI shows the antivirus engine to be outdated.

I tried removing Clamav and reinstalling from scratch (couldn't find any left-over Clamav folders in the Home directory, showing hidden files - doesn't mean I didn't miss something, of course!)

The GUI and virus signatures are up-to-date; it's the anti-virus engine which is still the old one. This suggests that I DIDN'T actually uninstall the old one - but I may be wrong here.

All suggestions gratefully received!

---

### Post by albandy on 2009-03-26
You have to options, use it from backports or uninstalling it and installing by hand
I recomend you enabling backports
but if you prefer:

to uninstall clamav:
sudo apt-get remove clamav clamav-base clamav-freshclam --purge
then download from official web page and install

---

### Post by lisati on 2009-03-26
From the ClamAV website:
> What does Your ClamAV installation is OUTDATED mean?

    * You’ll get this message whenever a new version of ClamAV is released. In order to detect all the latest viruses, it’s not enough to keep your database up to date. You also need to run the latest version of the scanner. You can download the sources of the latest release from our website. Upgrade instructions are on the Wiki. If you are afraid to break something while upgrading, use the precompiled packages for your operating system/distribution. Remember: running the latest stable release also improves stability.


---

### Post by gandaran on 2009-03-26
> **ifindcomputersreallyhard said:**
> Thanks, Albandy.

The virus signatures are updating fine, fortunately.

The ClamAV GUI shows the antivirus engine to be outdated.

I tried removing Clamav and reinstalling from scratch (couldn't find any left-over Clamav folders in the Home directory, showing hidden files - doesn't mean I didn't miss something, of course!)

The GUI and virus signatures are up-to-date; it's the anti-virus engine which is still the old one. This suggests that I DIDN'T actually uninstall the old one - but I may be wrong here.

All suggestions gratefully received!
do you have clamtk installed? clamtk is the clam antivirus gui for gnome users, if you want to update using the gui you have to run the gui with root permissions!

---

### Post by albandy on 2009-03-26
> **gandaran said:**
> do you have clamtk installed? clamtk is the clam antivirus gui for gnome users, if you want to update using the gui you have to run the gui with root permissions!

I don't use clamtk, only clamav from terminal, I prefer not to run visual app with sudo because you can easily delete something

---

### Post by ifindcomputersreallyhard on 2009-03-26
Thanks, everyone.

You've no idea how complicated this Ubuntu business is to beginners - "backport" sounds like some sort of a carburetter problem -I've got an awful lot of homework ahead! 

The command ending "...purge" looks promising - I'll give that a try.

Updating the GUI proved straightforward - I just reinstalled it. Hope this isn't viewed as cheating!

Thanks again for all your time. It's given me plenty to think about.

---

### Post by rzlorayes on 2009-04-13
> **albandy said:**
> sudo freshclam
this will update your clamav signatures
Hi Albandy,

Thanks very much for sudo freshclam! The command line was real cute!

Ric

---

### Post by Sir Jasper on 2009-04-13
Hi,

I am using Clamtk (not clamav) so you might try that.

I also use Avast (debian) which scans some 5 times faster than clamtk.

My regards

Addendum:

Avast downloads its full database when signatures are updated usually once a day. So it is much less effective for those on dial-up.

Sometimes, I also use Firefox and its "Dr.Web" add-on on line to check for viruses before downloading new files.

---

### Post by dr_smit on 2009-07-22
try
sudo apt-get update
sudo apt-get urgrade clamav

worked for me

---

### Post by jebradley on 2011-04-07
I have read all of these postings, and they do not help when the current version of clamav is 0.97 and the version in the repository is 0.96.5 .

I repeat, the version in the repository is 0.96.5, so doing a 'sudo apt-get update' and 'sudo apt-get upgrade' is not going to get you beyond 0.96.5, so you will continue to get the message about the engine being outdated.

I have tried installing from source, but the /etc/init.d/clamav-daemon and /etc/init.d/clamav-freshclam files did not get changes, and I continue to get the error message. Most of the /usr/bin/clam* files now have the current date, but 'clamav-check' and 'clamz' both have dates from 2009 and 2010.

So, how do you update the clamav engine to the current version?

---

### Post by uRock on 2011-04-07
Necromancy. Please open a new thread. (To update ClamTK, you will have to download from their site, though the current GUI will work fine.)

Thread Closed.

---

