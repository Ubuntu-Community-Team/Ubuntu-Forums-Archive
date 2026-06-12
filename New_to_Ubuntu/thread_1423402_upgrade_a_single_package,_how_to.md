---
title: "upgrade a single package, how to?"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by arisseu on 2010-03-06
Hi,

I have Ubuntu Jaunty 9.04 installed and updated.
I don't want to upgrade the whole system, however I would like to try the latest version of pulseaudio on it, to see if some problems are solved.

Is this possible/meaningful/wise? how should I do it? Is it enough to download the latest version from pulseaudio and install it toegether with all required updated packages?

thx

---

### Post by halitech on 2010-03-06
2 ways I can think of. Open Synaptic and only mark the package you want to upgrade or open a terminal and run

sudo apt-get install <packagename>

---

### Post by arisseu on 2010-03-06
I explain better: 
the pulseaudio package is uptodate, according to the current ubuntu version of my system, so I don't see a way to upgrade it with Synaptic.
However the version of pulseaudio installed is 0.9.14 while the last version available of pulseaudio is 0.9.21. 
Is it possible to use 0.9.21 version on Jaunty just "upgrading" the pulseaudio package?

---

### Post by halitech on 2010-03-06
if its not an update then you will probably need to download and compile it yourself from their website.

---

### Post by ibuclaw on 2010-03-06
This is generally what [PPA's]("https://launchpad.net/ubuntu/+ppas") are for.

I have a PPA with recent versions of OpenAL + PulseAudio here: [https://launchpad.net/~ibuclaw/+archive/ibuclaw](https://launchpad.net/~ibuclaw/+archive/ibuclaw)

Current build is intended for Karmic, though I can package/upload one for Jaunty if you need it.

Regards
Iain

---

### Post by arisseu on 2010-03-06
oh well, if you can do it...I will appreciate it a lot!

---

### Post by ibuclaw on 2010-03-06
Err...

Looks like it won't build due to missing build dependencies. Not sure what it will do working around it, so am not to bother.

You said that you wish to try it "to see if some problems are solved". Would you mind instead saying which problems you are referring to?

Regards
Iain

---

### Post by arisseu on 2010-03-06
yes, maybe it's better since I'm a bit new on this...
The reason is that I'm trying to understand why I get the following error (from skype):

"E: pstream-util.c: Assertion 'p' failed at pulsecore/pstream-util.c:36, function pa_pstream_send_tagstruct_with_creds(). Aborting."

Since I installed everything from Synaptic and the whole system is up-to-date, I didn't understand very well the reason of this error.
I thought that maybe some new releases could have solved the problem.

thank you for your help!

---

### Post by ibuclaw on 2010-03-06
> **arisseu said:**
> yes, maybe it's better since I'm a bit new on this...
The reason is that I'm trying to understand why I get the following error (from skype):

"E: pstream-util.c: Assertion 'p' failed at pulsecore/pstream-util.c:36, function pa_pstream_send_tagstruct_with_creds(). Aborting."

Since I installed everything from Synaptic and the whole system is up-to-date, I didn't understand very well the reason of this error.
I thought that maybe some new releases could have solved the problem.

thank you for your help!

Seems that it has been fixed upstream... 
[https://bugzilla.redhat.com/show_bug.cgi?id=539500](https://bugzilla.redhat.com/show_bug.cgi?id=539500)

---

### Post by hero1900 on 2010-03-06
to upgrade to the last alsa read this thread 
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

