---
title: "Confusing Java problem on 9.10."
date: 2010-01-10
forum: New to Ubuntu
---

### Post by darkyre on 2010-01-10
I've recently come to the conclusion that my version of Java may be out of date, because certain things don't work online that other people claim to work in a similar setup.
Um, what does this mean and how do I fix it?

```
zachary@laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[sudo] password for zachary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
```

Installing flash/java/mp3 support, and the like has always been a huge hassle on Ubuntu, and the multiverse repositories have so many package options with no clear explanation between the difference, that it just baffles and confuses some of us to death.

Help?
No operating system should expect you to memorize what extras you need to install for basic compatibility with common formats, without some sort of quick-fix or well organized system of explanation.

Which reminds me of a slew of other problems relating to this. My MP3's only work in some programs, even though I've installed LAME twice?? I installed it once, and then I had to install another LAME codec (wtf?) to get Amarok to work, but Rhythymbox still won't give me sound. Also, my Flash keeps crashing when left open for long periods of time (horrible memory management) and still doesn't even make all Flash work online.

How can this all be so fail? Canonical needs to monitor their repositories better, as I have begun to notice a high rate of failure of packages claiming to do one thing and working horribly.

---

### Post by ibninja on 2010-01-11
try
sudo apt-get remove sun-java6-jre
sudo apt-get install sun-java6-jre sun-java6-bin
As for audio in Rhythmbox, is it only mp3s that don't work, or do no sound files play at all? (try an ogg file if unsure ([http://www.vorbis.com/music/](http://www.vorbis.com/music/) if you don't have any. You'll have to right click and "save link as..."))
This leaves flash. Flash has occasionally failed for me, and Adobe doesn't seem to care if it fails to function well. If you can deal with limited functionality (it will run almost all movie sites, but doesn't do well with most games), you can replace flash with gnash (uses more memory occasionally, but I've never had it crash) until flash updates again. There's often no good way to fix flash if it's broken, because it is 3rd party.

---

### Post by Mighty_Joe on 2010-01-11
> **darkyre said:**
> No operating system should expect you to memorize what extras you need to install for basic compatibility with common formats, without some sort of quick-fix or well organized system of explanation.

Complain to your local bureaucrat.  Ubuntu is in the unenviable position of trying to provide a product for free when many technologies, such as MP3, are protected in some jurisdictions by patent, license or other legal means. [See here]("https://help.ubuntu.com/community/FreeFormats") for the full story.  
As for Java, there's some growing pains as Ubuntu has decided to use [OpenJDK]("http://openjdk.java.net/") going forward, but still has many people using Sun Java who are upgrading to Karmic.  
The version of Sun Java in Karmic will not be updated, even for security flaws.  Your options are OpenJDK or install the current Java version and subsequent updates [yourself]("http://sites.google.com/site/easylinuxtipsproject/java")

---

