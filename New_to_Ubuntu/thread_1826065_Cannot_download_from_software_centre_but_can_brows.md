---
title: "Cannot download from software centre but can browse web fine..."
date: 2011-08-16
forum: New to Ubuntu
---

### Post by jim88 on 2011-08-16
Hi all,

I'm a complete Linux/Ubuntu newbie - just installed 11.04 yesterday on my laptop and managed to successfully download all the updates etc over my home wireless connection. However, today I've brought my laptop into work, set up the wireless connection (can browse the internet using firefox with no problems) and when i've tried to use the software centre I'm unable to download anything (Error message: "failed to download package files. Check your internet connection", "failed to fetch http://gb.arch..."). 

Realise it's probably something in my connection configuration but am at a complete loss as to what it could be. Any help would be awesome as the IT people here have no clue!

Cheers!

---

### Post by grahammechanical on 2011-08-16
It may be nothing to do with you or your connection to the network. It could be that the servers you are downloading these packages from are not doing their job. This sometimes happens. Check out this thread.

[http://ubuntuforums.org/showthread.php?t=1823584]("http://ubuntuforums.org/showthread.php?t=1823584")

I had this same issue in my testing of 11.10 and could only update through the command line. But this morning I was able to use update manager without problems.

Sometimes links to packages are broken and we have to wait until it is corrected.

Regards and welcome to the forums

---

### Post by jim88 on 2011-08-16
Cheers for the quick reply Graham!

Just tried installing a couple of completely different things (gfortran and VLC media player) and also just doing a general update via command line but had no luck - so unless i've been very unlucky and the links have been broken for everything i've tried to install, I think something else might be causing the problem :(

Any ideas?!

---

### Post by realzippy on 2011-08-16
so what errors does
```
sudo apt-get update
```
give?

---

### Post by Paqman on 2011-08-16
In Software Centre got to Edit > Software Sources > Download from > Other > Select best server.

It'll find the fastest server for you.

---

### Post by Gone fishing on 2011-08-16
It could be your work blocks access to the content - for example they may block access to certain file types, certain websites etc.

Also does your work use a proxy? have you configured synaptic etc to use the proxy?

---

### Post by jim88 on 2011-08-16
Looks like the proxy was the problem! Have managed to configure Synaptic successfully to install stuff from there, however I still can't get software centre or command line installs to work. Can anyone tell me how I would go about changing the proxy settings for these too?

Cheers!

---

### Post by ofnuts on 2011-08-16
> **Gone fishing said:**
> It could be your work blocks access to the content - for example they may block access to certain file types, certain websites etc.

Also does your work use a proxy? have you configured synaptic etc to use the proxy?
Likely scenario:

- work network has a proxy
- OP set up the proxy only in his browser
- software updates use the standard routing, doesn't go through proxy and fails

Possible fix:

- setup proxy system-wide so all applications can use it

I'm not sure if Ubuntu's network managers can switch/enable the proxy automatically when switching network locations.

---

### Post by jim88 on 2011-08-16
Fixed it! Am still finding my way round Ubuntu and managed to stumble across the network connections options.

Thanks for the help guys!

---

### Post by Gone fishing on 2011-08-17
Proxy from the commandline I've had a problem with try ```
sudo -i
``` then the command ```
apt-get install whatever
```

---

