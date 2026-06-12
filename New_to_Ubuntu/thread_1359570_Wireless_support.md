---
title: "Wireless support"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by elusiveqc on 2009-12-19
I just installed Ubuntu on one of my machines.  I am really new at this, always used Windows before and am almost ready to go back to XP.  I have been trying all day to get my machine to see my pcmcia card and I am not getting anywhere with it.  Wired worked fine right away but my pcmcia card is not even coming on anymore.  Tried another usb wireless card and this machine still is not seeing it.  It is a Toshiba Satellite with a Linksys pcmcia card.

I have read through all of the forums but, honestly, you guys are hard to follow.  I am seriously  new at this OS.  Found and installed all of my updates, no proprietary drivers are in use on this system.  I read in one of the forums that I should disable my ethernet card and see if Ubuntu will pick up the wireless card then but I cannot even work out how to do that.

Seriously frustrated.

---

### Post by Zzl1xndd on 2009-12-19
Would you be able to provided the model number of the Card you are using, as it might provided some insight into the issue.

This might be a case where there are no Linux drivers available and something Like ndiswrapper (Basically lets you use the Windows Drivers) needs to be used. 

But let us know the model number and we will do our best to help out.

---

### Post by elusiveqc on 2009-12-19
Hi, thanks for replying.  The adapter I have is a Linksys PCMCIA Wireless G Receiver WPC54GX w/SRX, seems pretty standard to me.  When I had xp on this machine it worked right away, did not 
need to install any additional drivers and it did not give any conflicts.

Any help you could offer me would be really appreciated.

Thanks again.

---

### Post by Zzl1xndd on 2009-12-19
> **elusiveqc said:**
> Linksys PCMCIA Wireless G Receiver WPC54GX w/SRX, seems pretty standard to me.  When I had xp on this machine it worked right away, did not 
need to install any additional drivers and it did not give any conflicts.


Did a quick search on it and it looks like this is one that requires ndiswrapper, as I have never configured anything with ndiswrapper, I am afraid I will not be much help, so I will defer to the others in the forum. 

However I can explain why it isn't working, in short the manufacture did does not have any Linux drivers for the card and the community has not revered engineered it.

---

### Post by elusiveqc on 2009-12-20
Hmm ok, it's looking like XP might win on this one 0_o

---

### Post by steveneddy on 2009-12-20
> **elusiveqc said:**
> Hmm ok, it's looking like XP might win on this one 0_o

No - it means that you need to install ndiswrapper to use a Windows driver for that card in Linux. That is what was stated before by tweakedenigma. It is a simple application that allows a user to use Windows wireless drivers on a Linux OS.

The other alternative is **do what most of the rest of us do, use hardware that is supported by Linux.**

Just because it is supported by XP doesn't mean it will be supported by Linux.

Linux,  and Ubuntu is NOT Windows. Everything is different here. If you can't get your head around Linux, or it's too hard at this time, then go back to XP.

Maybe try using a virtual machine to run Ubuntu while you try to figure out this new OS.

Look at the links in my sig or Google "ndiswrapper Ubuntu" and you will find your answer.

If you are going to use Ubuntu you really need to forget about doing things the Windows way. 

If you need additional help, post back here so we can help you.

---

### Post by elusiveqc on 2009-12-20
Are you always that harsh with new people, Steveneddy?  I am not new to technology, my first computer didn't even have the memory to store dos on it.  Yes, I got used to the way Windows works and there isn't an issue on a Windows machine that I can't resolve.  I rebuilt the machine that I put Linux on and just found a pcmcia card that works like a dream - on XP.  I installed Ubuntu and resolved the few errors that I've received with it but no, I can't get my head around the support I've been offered with this issue.  I spent all day yesterday googling different things that people have suggested I try and I've not been able to find an answer that is basic enough for me to start with.  Why would anyone go out and buy hardware just to make a machine 'compatible' with Linux - doesn't that just blow the whole point of Linux?

This is not a crazy, obsolete, wireless card that I'm trying to install.  It's really common and boring.  Not trying to work magic, just want my machine online.  I googled 'ndiswrapper Ubuntu' like you said and was met with a ton of forums that are loaded with terms that I have to then google. 

I get that this all seems basic to you, but to imply that it should be basic to everyone is just arrogant.  If a new PC user (yes there are still people who are just now starting with their first computers) asked me for help getting online and I knew their NIC was bad, I wouldn't just tell them to google it.  They likely wouldn't even know what a device manager was or where to find it and what to do when they did find it.  Reinstalling a NIC is a two minute deal for most of us but we all needed someone to show us how to do it the first time - surely you remember what it was like when you were new to Linux. (The part of your signiture that says 'Please help the new Ubuntu users' is either meant as a sarcastic joke or you're meaning to help them by pushing them out of your forum and back to another OS - either way, it made me laugh).

I will keep looking for clear, basic instructions so that I can get my laptop online and then go on to learn Linux.  And I will remember how crappy you've just made me feel so that when I am in a position to offer help to new users, I will not be condescending or arrogant with them.

---

### Post by swoody on 2009-12-20
Yes, it sounds like you are going to need to give ndiswrapper a try. I found a nice tutorial here:
[http://ubuntuforums.org/showthread.php?t=484359](http://ubuntuforums.org/showthread.php?t=484359)

All you need to do is open a terminal, and copy/paste the commands from that guide one at a time. You'll also need to download your specific driver before you start so ndiswrapper can find it. If you want a nice reference for ndiswrapper, check out the wiki page here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you encounter any errors, or have any questions, please let us know :)

---

### Post by steveneddy on 2009-12-20
> **elusiveqc said:**
> 
I will keep looking for clear, basic instructions so that I can get my laptop online and then go on to learn Linux.

You have already been given clear, basic answers twice and first you gave up and said that you couldn't keep up, the next time you said XP won on this one point.

> I have read through all of the forums but, honestly, you guys are hard to follow

> Hmm ok, it's looking like XP might win on this one 0_o

I went on to clarify the facts for you. Follow the directions that you were given twice now and install ndiswrapper to get your card installed and working. 

Stop giving up and making comments like "Oh, I guess XP is better than Ubuntu, they won this one".

If you have questions about the instructions you are given then ask about what you don't understand. 

I have already stated that this is different than Windows. Follow the instructions one step at a time until you achieve success.

Lastly, I wasn't being crappy. I reinforced the advice you were given earlier and offered alternatives to your issue, using a VM to run Ubuntu until you figure it out and using better supported hardware.

Now go follow swoody's advice and get your card running.

---

### Post by elusiveqc on 2009-12-20
I never said that XP was better than Linux, it's impossible to even begin to compare the two.  You have absolutely proven me right about you and I'll thank you to not comment on my questions again.  Get over yourself, you're not that clever.



> **steveneddy said:**
> You have already been given clear, basic answers twice and first you gave up and said that you couldn't keep up, the next time you said XP won on this one point.





I went on to clarify the facts for you. Follow the directions that you were given twice now and install ndiswrapper to get your card installed and working. 

Stop giving up and making comments like "Oh, I guess XP is better than Ubuntu, they won this one".

If you have questions about the instructions you are given then ask about what you don't understand. 

I have already stated that this is different than Windows. Follow the instructions one step at a time until you achieve success.

Lastly, I wasn't being crappy. I reinforced the advice you were given earlier and offered alternatives to your issue, using a VM to run Ubuntu until you figure it out and using better supported hardware.

Now go follow swoody's advice and get your card running.

---

### Post by elusiveqc on 2009-12-20
Thank-you so much swoody.  Worked out really well and the instructions were fantastic.  Thanks for taking the time to help me find the tutorials.  You're a gem.

My laptop is back online and now I'm anxious to learn all I can.

Thanks again.

> **swoody said:**
> Yes, it sounds like you are going to need to give ndiswrapper a try. I found a nice tutorial here:
[http://ubuntuforums.org/showthread.php?t=484359](http://ubuntuforums.org/showthread.php?t=484359)

All you need to do is open a terminal, and copy/paste the commands from that guide one at a time. You'll also need to download your specific driver before you start so ndiswrapper can find it. If you want a nice reference for ndiswrapper, check out the wiki page here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you encounter any errors, or have any questions, please let us know :)

---

### Post by steveneddy on 2009-12-20
You also might trying posting in the [Networking and Wireless thread]("http://ubuntuforums.org/forumdisplay.php?f=336") to get more traffic on your issue.

Also check the links in my sig, you will also find your answer there.

Oh, look, there is a link on how to get better support for your wireless card.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by elusiveqc on 2009-12-20
Fairly certain that I asked you to not reply to my questions.  And I know that I told you how sarcastic I found your signature, hoping that it reads as a warning sign to people you offer to 'help' in the future.

Oh look, there is a tree, go climb it.



> **steveneddy said:**
> You also might trying posting in the [Networking and Wireless thread]("http://ubuntuforums.org/forumdisplay.php?f=336") to get more traffic on your issue.

Also check the links in my sig, you will also find your answer there.

Oh, look, there is a link on how to get better support for your wireless card.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by steveneddy on 2009-12-20
Hey glad you got it working.

Please mark the thread as solved.

---

