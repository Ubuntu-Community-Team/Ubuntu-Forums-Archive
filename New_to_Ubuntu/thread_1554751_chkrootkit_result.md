---
title: "chkrootkit result"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Rover75 on 2010-08-17
Hi Folks. Perhaps someone can help me to understand if the following is something malicious.

I ran ChkRootKit, which reported a suspicious file, namely:

/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path /usr/lib/firefox-3.6.8/.autoreg /usr/lib/xulrunner-1.9.2.8/.autoreg


Should I be worried? If so, what can I do about it? Any help would be greatly appreciated.

---

### Post by Paul820 on 2010-08-17
[http://ubuntuforums.org/showthread.php?t=1544017]("http://ubuntuforums.org/showthread.php?t=1544017")

---

### Post by Rubi1200 on 2010-08-17
Read this:

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)

And, as above, the likelihood is that these are false positives; so, nothing to worry about.

I just would like to point out, no disrespect intended, that as bodhi.zazen, the author of the Ubuntu security stickies, has mentioned in numerous posts if you are unwilling to do the legwork and find out what these reports mean then running a program like this is fairly pointless.

---

### Post by Rover75 on 2010-08-17
Thank you Paul820 and Rubi1200 for your reassurance about a false positive, it was very gratifying. The research I did before asking the forum for assistance was inadequate, something else I've learned.

---

### Post by john newbuntu on 2010-08-17
In general if you only have a few files, run it through [http://www.virustotal.com](http://www.virustotal.com) to check for viruses by putting it through 40+ different antivirus products.

---

### Post by Rover75 on 2010-08-18
Thank you john newbuntu, another interesting facility noted.

---

