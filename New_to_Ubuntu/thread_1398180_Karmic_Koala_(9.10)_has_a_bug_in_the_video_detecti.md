---
title: "Karmic Koala (9.10) has a bug in the video detection setup"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by DaveInPhx on 2010-02-04
Yep, this is old news to those who are already up and running, but to someone that just downloaded the package and was expecting a "stable" release to be - ummmm - stable?  It comes as quite a shock.  It's a pity that nobody thought to post any of this on the download site so others wouldn't be slamming these forums with "help me" messages!  The short answer is that the video detection just plain doesn't work!

I have spent (wasted) the past 5 hours hunting for information on how to get the video to display in something higher that 800x600, to no avail. I've followed tips on creating the non-existent xorg.conf, some of which resulted in me going back to the CD in order to recover the system. Unfortunately, I'm still no closer to getting it working, and I have some problems which complicate the whole issue even further.

The machine I'm setting up is for a friend whose XP box was totally wiped out recently by a virus and I've finally talked him into trying an alternative. I have all his data backed up on my own network, and happily blew away his entire hard drive to install Karmic.  Everything works great, but the video resolution is so low that some applications (GIMP for example) have their windows overlapping or parts of them are off the screen.  The system isn't usable in this state.

My questions, therefore, are as follows:

[LIST]
[*]Is there an older distro I can use to put him on that has similar capabilities but where the detection actually works?
[*]Has anyone come up with a generic guide to creating the xorg.conf file, explaining exactly how to get the information needed for each point?
[/LIST]
To elucidate on the last question, I believe it should be along the lines of:

[LIST=1]
[*]Create the file through sudo
[*]Edit the file and paste in a template, pre-filled with identified fillable fields (suitably sized to be readable in a browser in 800x600 mode!)
[*]Each variable in the template should then be referenced by instructions on the commands to run in order to obtain the data to be placed into that position.
[*]Follow up should include where to get the additional data (for example, monitor synch modes.
[*]Conclusion should include methods to recover (in laymans terms) if the method doesn't work, including disaster recovery, or just using ctrl-alt-F1 to avoid blowing out the monitor!
[/LIST]
I think a well referenced tutorial of this type would reduce both the questions posted here, as well as the frustration levels of new users. I know I'm worn out by the whole process, and more than a little disappointed with it.  

I ran on linux many years ago, and even completed LFS (linux from scratch), but I've forgotten most of that stuff. What would most help me now is an answer to the first question posed above (older distro?), just so I can get my friend back online quickly!

Your help would be most appreciated!

---

### Post by dubref on 2010-02-04
Sorry to hear you are having such a bad time.

I think, what would be most helpful, if you posted what video card your friend's computer has. Video card dedtection problems are still around, although personally I have been lucky to never encounter them thus never having had the pleasure of editing a xorg.conf file ;).


What you should try is an earlier Ubuntu LiveCD(8.04LTS(Long Term Support) or,8.10,9.04), if it boots in a nice big resolution on your friends computer, then you might start with installing that particular version and upgrade later.

Alternatively you might try Mint (till recently a customized version of Ubuntu,which may have extra drivers already preloaded, someone correct me).

---

### Post by Grenage on 2010-02-04
Bad EDID detection is actually an issue with the monitor or monitor cable 99% of the time, but I agree that there should be a GUI option to force a res of your choice.  I have a rough guide [here]("http://www.grenage.com/xorg.html") on the issue, with workarounds.

---

