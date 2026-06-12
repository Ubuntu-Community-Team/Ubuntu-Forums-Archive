---
title: "Downloading Corrupt Files"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by alexis44 on 2011-03-19
If I happen to download a media file, whether it's an image, video or audio file that may possibly be corrupt.  Will the system alert me to this, and if not, and I cannot find it, will it cause any problems with the OS?  Can it possibly install something malicious like a rootkit or trojan?  If I find a file that could be corrupt and delete it, will that simple act solve any possible problems?

---

### Post by alexis44 on 2011-03-19
This seems like a rather basic question, maybe too basic.  Would it help if it were moved to the Security section or I started one there? :)

---

### Post by fabricator4 on 2011-03-19
> **alexis44 said:**
> This seems like a rather basic question, maybe too basic.  Would it help if it were moved to the Security section or I started one there? :)

ABT, probably _is_ the best place.  I was hoping someone more knowledgeable would answer.

Because of layered nature of the Linux OS, very little that happens in user space can affect the kernal.  You have to actually give permission for the kernel and other system files to be modified.  Therefore, while a program could theoretically damage something in your home directory, the kernel and system should be quite safe.  This why you have to type in your password to update the system, or to install programs.

You still need to make sure you are using trusted sources (like the official repositories) and so on.  My understanding is that the .deb installation packages are checked for integrity at the time they unpacked for installation so that a bad download is not installed into the system.

As far as bad downloads in videos, sound files etc, the programs using them can and should be written in such a way as to trap any unexpected problems.

Similarly, to test the integrity of a downloaded ISO (like the LiveCD) you should check the MD5SUM against the published result for that release.  I had a corrupted ISO download only a few days ago, which was picked up by checking the MD5SUM.

With a little bit of care (like not giving permission to an unknown program) then you should experience no problems at all.

Chris

---

### Post by mike555 on 2011-03-20
If you wonder about a download you could scan it first in Firefox with this add-on; 
[https://addons.mozilla.org/en-US/firefox/addon/drweb-anti-virus-link-checker/](https://addons.mozilla.org/en-US/firefox/addon/drweb-anti-virus-link-checker/)

---

