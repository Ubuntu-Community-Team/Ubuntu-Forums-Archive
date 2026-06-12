---
title: "Why is Java outdated in the repositories?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by TruthOrDare on 2010-04-13
Hi,

I'm using Jaunty and the latest version in the repositories is Update 16 when the actual latest version is Update 19.

The repository is seven months out of date and the updates fix security issues.

I know Canonical don't officially provide updates, but surely software in the repository should be up to date, especially since people are actively encouraged to use it?

---

### Post by QIII on 2010-04-13
Canonical has decided to support OpenJDK, which is the open source version of Java.  That is in keeping with their philosophy of providing only open source applications and software when possible.

I am somewhat disappointed, personally, because many web sites (and my clients) specify Java.  My bank website, for instance, checks for the most recent update.  That's 19 right now.  It won't work with OpenJDK.

If you want to install Java, I recommend the method found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Otherwise, if OpenJDK will suit your needs you should use that.  It can be installed from the repos.

---

### Post by snowpine on 2010-04-13
Jaunty is the 9.04 release, this means all of its packages are the stable version as of April 2009 (patched for security if necessary). You can install the latest Java yourself from outside sources, or upgrade to the current Ubuntu release (9.10 with 10.04 coming soon). This has always been Ubuntu's policy and is the same for most Linux distros once they are released.

---

### Post by QIII on 2010-04-13
snowpine (if you get back to this) --

Not at my Ubuntu machine (unfortunately, I am a vassal of Redmond during the work day) so I can't check, but is the version of Java in the Partner repo maintained up through the current version?

---

### Post by snowpine on 2010-04-13
Happy to check for you, but no clue... how would I check?

---

### Post by QIII on 2010-04-13
Enable partner repo in the "Third party" tab in software sources, and do a search in Synaptic for JRE or Java and see if Update 19 is there (I hope there is some text that identifies it thus!)

---

### Post by Mighty_Joe on 2010-04-13
Sun JDK will be added to the partner repository for Lucid, according [to this]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426").
I was under the impression that Jaunty's sun-jdk package would continue to be updated.  Karmic is frozen at Update 16 for the reason QIII states, Canonical wanted to use Open JDK instead.

---

### Post by snowpine on 2010-04-13
> **QIII said:**
> Enable partner repo in the "Third party" tab in software sources, and do a search in Synaptic for JRE or Java and see if Update 19 is there (I hope there is some text that identifies it thus!)

I have sun-java6-jre at version 6-16-0ubuntu1.9.04 on Jaunty with the Partner repo enabled.

---

### Post by QIII on 2010-04-13
> **Mighty_Joe said:**
> Sun JDK will be added to the partner repository for Lucid, according [to this]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426").
I was under the impression that Jaunty's sun-jdk package would continue to be updated.  Karmic is frozen at Update 16 for the reason QIII states, Canonical wanted to use Open JDK instead.

Looks like it will still be Update 16 (I scanned it briefly).

I'm going to check Lucid when I get home and see what's up.

---

### Post by QIII on 2010-04-13
> **snowpine said:**
> I have sun-java6-jre at version  6-16-0ubuntu1.9.04 on Jaunty with the Partner repo enabled.
 
 Looks like Update 16, which is what Mighty_Joe found out.

Well.  Good bit of info to have under the hat for next time.

It seems that for now those who really need to have Sun Java Update 16+ will  need to use the method I referred to.

For the vast majority of users, OpenJDK will probably suffice.

---

### Post by philinux on 2010-04-13
You guys might be interested in this thread.

[http://ubuntuforums.org/showthread.php?t=1406969](http://ubuntuforums.org/showthread.php?t=1406969)

---

### Post by snowpine on 2010-04-13
See my post #3. Ubuntu is not a "rolling release" distro. I'm sure Lucid will have the latest version. :)

---

### Post by QIII on 2010-04-13
Thanks, Philinux.

I'm going to check when I get home.  If it is indeed in the Partners repository (as it says here:  [http://archive.canonical.com/dists/lucid/partner/binary-amd64/Packages](http://archive.canonical.com/dists/lucid/partner/binary-amd64/Packages)), then I will recommend using that or the method I mentioned -- for those who absolutely must use Sun Java rather than OpenJDK.

---

