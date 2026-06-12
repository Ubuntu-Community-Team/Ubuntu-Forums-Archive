---
title: "Virus found after installing ubuntu"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by abnordude on 2011-04-30
I just installed ubuntu 11.04 natty.
I also installed clamtk from the software center.
Then I did a recursive scan on my file system.
It detected** 6** viruses.
When I tried to delete them, I couldn't.
Please help me.


I'd also like to know one thing.


**Will viruses really affect ubuntu??**

---

### Post by 5149.5 on 2011-04-30
That sounds like false positives to me. I would be very skeptical for several reasons. What are the filenames that were found to be infected?

---

### Post by Rubi1200 on 2011-04-30
Post the log of what was found. As already mentioned, likely false-positives which are a well-known issue with this particular AV.

---

### Post by rvchari on 2011-04-30
> **abnordude said:**
> I just installed ubuntu 11.04 natty.
I also installed clamtk from the software center.
Then I did a recursive scan on my file system.
It detected** 6** viruses.
When I tried to delete them, I couldn't.
Please help me.


I'd also like to know one thing.


**Will viruses really affect ubuntu??**
best way is to try to scan with an alternative AV, avast is a good option. if you cant download and install, try to get your disk scanned from online... (cant guarantee it will be perfect, coz all AVs may seem commercial and try to market their product by making you purchase if its non free version)

false positives may also be a reason in your case

---

### Post by abnordude on 2011-04-30
OK.
I'll Scan once more.
I had to switch off my computer due to power cut.
Scanning....

---

### Post by lisati on 2011-04-30
For the record: AVG have a free Rescue CD that you can download.
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by abnordude on 2011-04-30
Here is the scan result

---

### Post by rvchari on 2011-04-30
> **abnordude said:**
> Here is the scan result


everything seems to be related to clamtk
try to completely remove clamtk. if you are using ailurus then try to clean the apt-cach from the gui of ailurus. else you can issue terminal commands to clean all apt cache.

also remove the .clamtk or related files from your home directory.

after system is clean, then re-install. i m presently using clam in maverick (exclusively to scan the external disks and sticks and ofcourse some windows programs that i frequently run thru wine.

all said and done, you need not worry abt the sys files of ubuntu. they are rock solid and virus cant attack then unless you give them permission !

have fun

---

### Post by gandaran on 2011-04-30
> **abnordude said:**
> Here is the scan result

this only goes to show what clam antivirus really is, the best piece of junk that you can install, an antivirus that detects itself as virus!

---

### Post by samacaster on 2011-04-30
I once saw a video of an install of XP where halfway during the install, once XP connects to the net, a virus pops up and claims that your system is infected!!!!HA!!!!! Download our software to remove it now!!

rvchari has it spot on. follow the instructions and all will be well.

---

### Post by yetiman64 on 2011-04-30
> **gandaran said:**
> .... an antivirus that detects itself as virus!

The first thing I noted on seeing the log. :lol:

> **samacaster said:**
> ....rvchari has it spot on. follow the instructions and all will be well.

+1, I agree with this (and rvchari of course.) 

Most people don't install an antivirus in Ubuntu, unless they either run a mail server or share potentially suspect files with Windows users (although the responsibility for protecting a Windows install should really fall to the user of that install).  

A good link for you to check out would be [[COLOR=Blue]--Ubuntu Security--  [/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812")(it contains some good information about Ubuntu and viruses).

---

### Post by 3rdalbum on 2011-04-30
Look at the "status" column. **Those are listed as ClamAV test files**. They are files that are designed to always be picked up by ClamAV, to check whether the test process has actually run.

Every antivirus has these available, but it looks like you've downloaded this package to your system, which is why Clam is picking it up. These aren't viruses, they are just test files.

Why did you bother scanning your system with an antivirus program anyway? There are no viruses on Linux at the moment. The only thing an antivirus is good for on Linux is checking to see whether there are any Windows viruses (dormant, of course) on any connected disks, so you don't inadvertently transfer those files to a Windows system.

**Please, just remove ClamAV and stop worrying.** This isn't Windows here, this is Linux, where the system has been designed to be pretty secure.

---

### Post by abnordude on 2011-04-30
> **3rdalbum said:**
> Look at the "status" column. **Those are listed as ClamAV test files**. They are files that are designed to always be picked up by ClamAV, to check whether the test process has actually run.

Every antivirus has these available, but it looks like you've downloaded this package to your system, which is why Clam is picking it up. These aren't viruses, they are just test files.

Why did you bother scanning your system with an antivirus program anyway? There are no viruses on Linux at the moment. The only thing an antivirus is good for on Linux is checking to see whether there are any Windows viruses (dormant, of course) on any connected disks, so you don't inadvertently transfer those files to a Windows system.

**Please, just remove ClamAV and stop worrying.** This isn't Windows here, this is Linux, where the system has been designed to be pretty secure.


Well. 
I distribute CD's to people.
They mainly use windows.
Hence,  I need to have an anivirus installed.

---

### Post by 3rdalbum on 2011-04-30
> **abnordude said:**
> Well. 
I distribute CD's to people.
They mainly use windows.
Hence,  I need to have an anivirus installed.

Ahh I see, I replied to your other thread. Don't bother scanning your Ubuntu system - just a waste of time. Just scan the files that you've downloaded that you're going to put onto CD.

---

### Post by 5149.5 on 2011-04-30
Anti-virus packages look for files containing a string of characters that match a "signature" for known viruses. The signatures have to be in a file somewhere for the AV packages use. An AV package that detects it's own signature files as an actual virus is pretty lame. I can see how it could happen though with the storage of the AV files in a cache. The AV storage locations for it's files are probably excluded from scanning but the cache location isn't. Please mark this thread as solved.

---

### Post by abnordude on 2011-04-30
> **3rdalbum said:**
> Ahh I see, I replied to your other thread. Don't bother scanning your Ubuntu system - just a waste of time. Just scan the files that you've downloaded that you're going to put onto CD.

Ok.
I'll do just that.

---

