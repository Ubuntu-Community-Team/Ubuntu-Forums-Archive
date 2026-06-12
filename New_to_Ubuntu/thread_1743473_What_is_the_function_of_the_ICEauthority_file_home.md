---
title: "What is the function of the ICEauthority file /home/username/.ICEauthority"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by rocksockdoc on 2011-04-29
What is the function/purpose of the ICEauthority file?

Today, all of a sudden, KolourPaint began crashing with segmentation faults and when I rebooted, I got the cryptic message "Could not update ICEauthority file /home/username/.ICEauthority".

Googling, I see this ICEauthority file is very often corrupted. Most solve the problem by deleting the file, or changing permissions. 
- [**could not update ICEauthority**]("http://ubuntuforums.org/showthread.php?t=1021106")
- [**Could not update ICEauthority file /home/ian/.ICEauthority**]("http://ubuntuforums.org/showthread.php?t=1437213")
[- **Could not update ICEauthority file /home/carl/.ICEauthority**]("http://ubuntuforums.org/showthread.php?t=1577267")
[- **Could not update ICEauthority file /home/test/.ICEauthority**]("http://ubuntuforums.org/showthread.php?t=1081730")
[- **[SOLVED] ICEauthority error**]("http://ubuntuforums.org/showthread.php?t=949750")
-[ Could not update .ICEauthority file]("http://byrd740.wordpress.com/2009/10/01/could-not-update-iceauthority-file/")
etc.

This weakness in the ICEauthority file has been around for quite some time in Ubuntu:
- [**ICEauthority error in Ubuntu 8.10**]("http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8-10-a-681312/")

And, it's still around in Ubuntu 10.10:
- [Ubuntu 10.10:  Error:  Could Not Update ICEauthority File]("http://raywoodcockslatest.blogspot.com/2010/10/ubuntu-1010-error-could-not-update.html")

The single most relevant quote in those references is perhaps this one:
> I don't know for certain, but it's possible that running a graphical application with *sudo* (instead of *gksudo*) might have messed up your .ICEauthority file. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)But, may I ask ... What 'is' the ICEauthority file and what does it do for us (besides corrupt)?

---

### Post by eveg on 2011-07-25
do you know for certain that the 'psychocats' link is a safe one? links that seem harmless can trigger malicious code, so it's better not to post them if you aren't certain. not saying this one is necessarilly any harm, just concerned.
 
the closest to an answer that i've found is that running sudo whan you should run gksudo can leave you without gui (no graphics--only a command line).
found that on pg. 972 of the 2010 ubuntu linux bible, but the author's solution is obviously not for ametures; i tried it and kept getting the same errors plus different ones, doubtless because i didn't understand what the author was telling me to do. not entirely my fault as there were no written examples even, much less a useful screenshot--- at which point i should've had the sense to get more advice before i tried anything.

---

