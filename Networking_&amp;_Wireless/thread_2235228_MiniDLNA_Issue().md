---
title: "MiniDLNA Issue(?)"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by AnotherKevin on 2014-07-19
OK.   Can I impose on you guys again?

I got everything running on my miniDLNA near PERFECT, accept one TV says "video codec not supported" and "audio codec not supported", HOWEVER when I put the same video file on a thumb drive and plug it into the TV, it plays just fine.  This TV (Vizeo) also plays music files (mp3) with no problem off the network.  So, could this be a network issue?  Any other ideas?  

Thanks in advance...

Kevin

---

### Post by Hadaka on 2014-07-19
Hi, you may just have a codec issue not a miniDLNA problem.
hopefully you arnt running headless,,,click the left bar thing
then click Ubuntu Software Center...once there enter "restricted"
no quotes in the upper right search section. that will bring up
Ubuntu Restricted Extras...load that for missing codecs and
hopefully that will help.
good luck

P.S. ran across this looking around,,
Jun 5, 2014 - ReadyMedia (formerly known as *MiniDLNA*)
per.  sourceforge.net/projects .,,I went to the page and they
have a free download of the latest,,greatest,,,so maybe
codec issues have been addressed in the package, i have no
idea if this is so.
More info:[http://askubuntu.com/questions/199594/ubuntu-restricted-extras-after-install-ubuntu-12-04](http://askubuntu.com/questions/199594/ubuntu-restricted-extras-after-install-ubuntu-12-04)
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by AnotherKevin on 2014-07-21
Hi [COLOR=#000000]Hadaka,  sorry for the delay in my response - grand kids are here visiting from downstate...[/COLOR]

[COLOR=#000000]I already had Ubuntu extras installed, but re-installed just to be sure.  [/COLOR]

[COLOR=#000000]I downloaded the newest version of miniDLNA from sourceforge.  I wasn't able to compile it, though.  There's poor instructions on doing so.

Kevin[/COLOR]

---

### Post by AnotherKevin on 2014-07-21
Well, I give...  Unable to compile the newest from source code.  Followed 3 different sets of instructions, none of which was successful.

However, I seriously doubt the issues I posted about are a result of the version I'm using (our other TV does just fine playing music and videos).  

Does anyone else have a suggestion?

Thanks

Kevin

---

### Post by AnotherKevin on 2014-08-02
Well, I finally figured out the issue.  This particular TV, Vizio Model E320i-A0, is not DLNA compliant (they tell me).  While it is intended to be able to run .mov, .avi, .mp4, near as I can tell, it only will play .avi files.  But, it plays them great!

So that's the fix:  using avi files...

Thanks!

Kevin

---

