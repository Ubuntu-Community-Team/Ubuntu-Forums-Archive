---
title: "Help java??"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Superman1744 on 2009-02-15
I have installed icedtea java and Tryed to load pogo.com under firefox It will load then go grayish where the game and chat is soppose to be?.also i have no clue where to access the terminal or anything like that complete noob.

---

### Post by kavon89 on 2009-02-15
You should probably use the standard Sun Java instead of IcedTea.

Head for the Synaptic Package Manager (System -> Administration) and Update/Refresh it. Then search for sun-java6 and install the JRE. Also remember to pick up sun-java6-plugin for Firefox support.

---

### Post by Superman1744 on 2009-02-15
Im away from the ubuntu pc ..i had my sis do it and it didnt work but she is also new to ubuntu and i was wondering if i could remote and do it my self?.im using vista thoe??

---

### Post by SunnyRabbiera on 2009-02-15
hmm, make sure the browser is shut off before doing anything.
Also make sure to have the restricted extras package installed too.
Try to get on your Ubuntu machine though.

---

### Post by Miljet on 2009-02-15
Glad to find another Pogo player here and welcome to Ubuntu.

First, what version of Ubuntu are you using and what version of Firefox?

There are three Sun java files that you need. They are sun-java6-fonts, sun-java6-jre, and sun-java6-plugin.Then you will need to remove Iced-tea. There is a config file somewhere that I don't recall at the moment that if it has Iced-tea listed first, it will be the one to load instead of Sun-java. You can do all that with Synaptic Package Manager.

I have been fighting this problem for months and have not yet reached a resolution. Pogo runs fine under Ubuntu 7.10 (Gutsy) using Firefox 2. However, it simply refuses to run under Ubuntu 8.04 (Hardy) and Firefox 3. After weeks of trying to get it to work, I finally created a new partition and re-installed Gutsy on it just so I can play Pogo. I have not tried Ubuntu 8.10 yet, so have no idea about whether or not it works there.

I still haven't isolated the problem to the newer version of Firefox, or the later version of Ubuntu. I kept up a running dialog with the support team at Pogo for several weeks, but they are just as stumped as I am. I have tried several different web browsers, but none of them worked either. I could list two pages of different things that I have tried, but the important point is that I haven't yet found a fix.

The best suggestion I have at this point is install Gutsy and see if it works for you. The problem with that is that Gutsy is nearing the end of its life cycle and will no longer be supported in a couple more months. Hopefully, we can figure something out before then. BTW, I kept Ubuntu 8.04 installed so I could continue to work on it too.

---

### Post by Superman1744 on 2009-02-16
I had her go to java.com and do the test, it worked!!! i agree i think java and pogo on ubuntu dont work and also i had my sis go to firefox and look for options under tools to allow pogo use its own fonts and stuff Found a site that suggested that.but she has no options thought that was weird also

---

### Post by Miljet on 2009-02-16
You can see which plugin Firefox is using by going to the URL input line in Firefox and typing in
```
about:plugins
```

I am about to sign off for tonight, but will keep monitoring this thread from time to time. And will let you know about any breakthroughs I might find.

---

### Post by hobo on 2009-02-17
I am running 8.10 and POGO would not work for me either, even though Synaptic shows Java 6 to be installed. What I did was, from the cmd line:
[I]
sudo aptitude install sun-java6-jre sun-java6-plugin [/I]

All kinds of stuff happened. But the end result was that POGO now works and the Wife is again a happy camper.

---

### Post by Koraq on 2009-02-17
So. This forum is filled with old crap and suggestions to install packages that don't exists.

That being said, it looks like the postings in this thread is from Feb 2009 so it should be up to date, right?

I have no java plugin and search synaptic don't give any results at all.

Are there a package called sun-java6-plugin ?? What repository serves it? I can't install it.

---

### Post by Miljet on 2009-02-18
Before Synaptic can find the sun-java6 packages, you need to go into System -> Administration -> Software Sources and enable all repositories. (Main, Universe, Restricted and Multiverse)  Also click on the Third-Party Software tab and enable the Partner repository. You should then be able to find the Sun packages. As stated previously, you will need sun-java6-jre, sun-java6-fonts, and sun-java6-plugin. It will install several other packages as well, but just make sure that you get these three.

Superman, if you are still monitoring this thread, I just installed 8.10 and it cured all my pogo.com problems. All games run great now. As a side benefit, it also cured the problem with my Atheros wireless card. I am a happy camper now.

---

### Post by Koraq on 2009-02-19
Partner repository enabled, and I can find all those packages, except the plugin. BTW my synaptic don't have a System menu item, and no button for "third party" that I can find. 

I do think I have the newest version of synaptic (what do that little ubuntu symbol by the package name mean anyway?)

---

### Post by Miljet on 2009-02-21
The system menu isn't under Synaptic - it is the other way around. The System menu is located at the top of your screen. You have to click on it to get to Synaptic. The partner repository is set from Software Sources, not from Synaptic.

Why don't you just open a terminal and type (or copy and paste)

```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

---

### Post by Koraq on 2009-02-23
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

So I'm missing something...

---

### Post by kelean on 2009-02-23
I have pogo working fine on my 8,10 install.  What has worked the best for me is to go to Applications>Add/Remove... Make sure to show all available applications is slected.  Type java in the search window then install Ubuntu restricted extras.

That is the best way for me to install java.  I play on pogo most everyday.  I had to move away from ubuntu because I could not run pogo on 7.10 and 8.04,  I had some other issues with those two versions, but that's another story.

---

