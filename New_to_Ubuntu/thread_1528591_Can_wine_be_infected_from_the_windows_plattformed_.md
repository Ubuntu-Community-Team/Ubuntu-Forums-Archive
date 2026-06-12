---
title: "Can wine be infected from the windows plattformed virus?"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-10
HI!

I wanna know that if wine can run all those windows file, so is there any possibilities that It too can get affected from windows virus or other platform virus and all the file might get corrupted?

One more thing, like I have installed ubuntu 10.04 under windows 7 as an application, so is there any possibilities that while surfing internet when we get a virus, can that virus affect windows 7 when we run windows 7??

Thanks!!

---

### Post by HermanAB on 2010-07-11
Wine only runs a very small number of well behaved programs.  It doesn't run the vast majority of Windows programs and certainly doesn't run any malware.

Relax and enjoy your Ubuntu system.

---

### Post by bodhi.zazen on 2010-07-11
There are infrequent cases of (windows) viruses running in wine yes.

---

### Post by amityadav9314 on 2010-07-11
Thanks!!

---

### Post by k3lt01 on 2010-07-11
Yes it can happen, but having said that you are probably more likely to get a cross platform trojan in Firefox, Chromium, OpenOffice etc, than a Windows virus in WINE.

---

### Post by amityadav9314 on 2010-07-11
so what action is needed to be taken in order to make my ubuntu safe from all these trojans?

Thanks!!

---

### Post by Pizack on 2010-07-11
> **amityadav9314 said:**
> so what action is needed to be taken in order to make my ubuntu safe from all these trojans?

Thanks!!

No computer is completely safe, however Ubuntu is about as safe as it can get already.  Unless you are dealing with highly sensitive information you probably shouldn't worry about it.  That being said, never install something that you get from a source you aren't sure about.  To my knowledge there are very very few viruses and trojans that will infect Ubuntu, and the ones that can generally require an extreme negligence by the user.  

Remember, this isn't Windows, most of your big headaches are gone.  Welcome!

---

### Post by jre6 on 2010-07-11
There is little chance that Wine would get infected. And there can be no harm to your Ubuntu installation until Wine runs with priveleges with the help of  sudo.

Maybe you can conduct antivirus scans to remove all the trojans. But most antiviruses don't work with Wine.

---

### Post by k3lt01 on 2010-07-11
> **amityadav9314 said:**
> so what action is needed to be taken in order to make my ubuntu safe from all these trojans?

Thanks!!There is a wealth of information in this forum, just do a search in the search function and type security or something similar.

Be alert, not alarmed. With Ubuntu (Linux) you don't need to be a reactionary. If you are careful with what you use (as has been mentioned above know where your material is coming from) and know about the sites you visit on the net 99.999999% (just a roundabout figure not meant to be taken as an accurate figure) of the time you'll be fine.

---

### Post by Paqman on 2010-07-11
> **amityadav9314 said:**
> so what action is needed to be taken in order to make my ubuntu safe from all these trojans?


First of all, any Windows malware picked up through using Wine will be confined to the fake Windows file structure that Wine creates in your home folder. None of it will be able to break out from there and actually take control of any system resources, unless it also exploits a flaw in Linux, which is really, really unlikely. The best way to prevent yourself becoming infected is to be careful about what .exe files you run through Wine. Don't get any Windows software from an untrusted source, which means don't get it from torrents, warez sites, etc.

As for a Wubi-installed system infecting your Win7 system, it won't happen. Only one system is running at a time. When you're booted up into Windows it's not executing any code from within the Wubi virtual partition. If you want to be extra sure of this, don't have your Windows (/host) partition mounted in Ubuntu.

---

### Post by amityadav9314 on 2010-07-11
Thanks for the windows information!

---

### Post by ronnielsen1 on 2010-07-11
[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)
 
Here's someone who's tried
 
> 
**Conclusion**
Out of the five Windows viruses I ran under Wine, not a single one was able to send email and propagate itself. When I went out of my way to be part of the Windows community by doing my part to propagate Windows viruses (lots of Windows users seem to think this is important, seeing as how they run random executables *and* use Microsoft Outlook and Internet Explorer) I discovered that it couldn't easily be done with GNU/Linux tools. Oh sure, I could *manually* forward these viruses to the folks in my address book, but where's the fun in that?

---

### Post by ankspo71 on 2010-07-11
Hi,
It is also best NOT to use "sudo" to run or open windows applications or scripts or attachments, or anything else from wine folder or some other windows-like directory. Doing so can invite bad things to happen, sooner or later.

---

### Post by bodhi.zazen on 2010-07-11
> **Paqman said:**
> First of all, any Windows malware picked up through using Wine will be confined to the fake Windows file structure that Wine creates in your home folder. None of it will be able to break out from there and actually take control of any system resources, unless it also exploits a flaw in Linux, which is really, really unlikely. The best way to prevent yourself becoming infected is to be careful about what .exe files you run through Wine. Don't get any Windows software from an untrusted source, which means don't get it from torrents, warez sites, etc.

That is not exactly true.

Within ~/.wine are symbolic links outside the ~/.wine directory , so all of your $HOME directory can be affected. Typically this means viral code is added to most , if not all, files in $HOME.

If you run wine as root system files can be affected.

The viral code is executed via wine, LOL.

The article you cite is old, search in the security section, there were 2 examples of many files in $HOME affected by wine recently (last 3-4 weeks).

---

### Post by 3rdalbum on 2010-07-11
> **amityadav9314 said:**
> so what action is needed to be taken in order to make my ubuntu safe from all these trojans?

Don't run anything you don't trust, and make sure you keep your common-sense about you when using your computer. Come to think of it, that's almost all you need to do to keep Windows safe anyway.

---

