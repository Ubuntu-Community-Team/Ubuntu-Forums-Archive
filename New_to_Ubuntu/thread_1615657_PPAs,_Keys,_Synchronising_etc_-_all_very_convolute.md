---
title: "PPAs, Keys, Synchronising etc - all very convoluted"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-07
I thought Ubuntu was supposed to be 'easy'. So far it's been an ok experience and the help on this forum second to none but this latest episode is just plain silly. Perhaps someone could assist or at least comment.

I have installed Ubuntu 10.10 on a Samsung N140. Some of the function keys and changing brightness of the screen etc don't work so I believe I have to install a PPA called Voria which addresses these issues.

The first problem is installing this thing. I have to use the terminal to do it, which is a pain switching backwards and forwards, cutting and pasting weird bits of code that make no sense. When I've installed it - where do I find it? Is it under applications? I can't find any documentation on PPA except [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA), which is an overview, not a step-by-step explanation.

I then find that I have to Activate it first by doing something on my profile page. But wait! Before I can do that I have to sign the code of conduct. So off I trot to the link that tells me I can only access this if I have an OpenPGP key!

To do this I have to import it by having a fingerprint...

...are you still with me? If this makes for boring reading then imagine what it's like for a noob like me going through all this. And I'm only half way through.

Next, in order to get an OpenPGP key I have to blah blah blah... eventually I'm in Launchpad but now I find my key has to be on the Ubuntu OpenKey server. This involves using Passwords and Encryption Keys where I have to sync to a server. This is where the problem begins. When I try and sync to a server it can't connect due to an internal server error and it just hangs.

Seriously, do I really have to go through all this just to add a little app that helps me change the brightness on the netbook? I really do hope I am being an idiot and that there is a very simple solution to all this.

Please, can someone help out a thickie noob?

Yours, without a key and very frustrated,

Jamie

---

### Post by QLee on 2010-11-07
[QUOTE=demonboy]I thought Ubuntu was supposed to be 'easy'. So far it's been an ok experience and the help on this forum second to none but this latest episode is just plain silly. Perhaps someone could assist or at least comment.
[/QUOTE]

Ok Jamie, because you invited comment I will.

I don't mean this as a criticism of you as a person.

It seems to me that you are impatient. You've just started with Ubuntu and seem frustrated with differences from what you are accustomed to. You want all the tweaks and changes to be easy, yet in your posts I haven't seen much indication that you have read available documentation. (some is noted in the stickies at the top of this subforum) In addition, you don't seem to using the forum search to find answers to frequently asked questions. I do understand that frustration, and the desire to have it all, and have it right now, but consider this. What other useful aspects of your life came automagically without the work of learning?

There is good stuff at the community documentation.
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

These two stickies also have some good information:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Some people from the Ubuntu community have put in quite a bit of effort to produce this manual as an easy for a beginner to understand step-by-step, with pictures, for reference to common tasks.
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

It probably will take a while for you to learn enough to get to the point where things make sense and you can see reasons for why things are done as they are. You'll probably progress quickly, you obviously have energy for it and time. I have seen this happen many times over the years, thus I expect to see it again and again. Truly, good luck!

---

### Post by demonboy on 2010-11-07
Yep, all fair comments. I admit, hands up, that I am being impatient. 

My only excuse for this is because I have a limited time to get two netbooks up and running with Ubuntu before I return to India where I exist on a 2G dongle connection. Any big downloads or exercises that require constant internet connection and page loading really need to done now. Believe me, my connection in India is so painfully slow even the most patient would be throwing their computer out the window ;)

I'll be sure to work my way through the documentation you suggest. I'd be interested to know if it covers off this specific issue with the hanging syncing of keys though. Also a lot of documentation out there is for earlier versions of Ubuntu and make references to things that either don't exist in 10.10 or have moved. The one advantage in India, however, is that printing is cheap. I'll be able to print off all manuals and documents when I am back there, and it's a place where I have more time to digest stuff too. It's all a bit rush-rush-rush here right now.

I hope that in some way explains my impatience! Thanks for the links, I'm going to them now...

---

### Post by QLee on 2010-11-07
I'm glad you took my comment in the spirit I meant it.

Just so you will know, I live on a small island, my Internet connection is by dial-up, so 2G doesn't sound so bad but I have seen user comments about poor service in India. No cable TV here or telephone broadband and, since I'm retired, I can't afford sat. broadband. So when I said I understand your frustration, I probably do understand some of it. I have to go visit friends when I need a big d/l. 

Ultimately, I think you'll get the hang of this stuff relatively quickly, as I mentioned, putting the time and energy in will pay big dividends.

---

### Post by QLee on 2010-11-07
I don't know anything about voria, I don't have a Samsung. However, there is a voria forum:
[http://www.voria.org/forum/](http://www.voria.org/forum/),
maybe they could offer more specific help on Samsung hardware issues. 
Edit:Maybe by hanging around there you could determine if you trust software from their repository.

You will always run into different versions in documentation, and will become good at translating into what you need. Remember, the documentation is produced by volunteers, there is no one paying to have people produce it in a timely (related to releases) manner.

---

### Post by oldos2er on 2010-11-07
Every PPA has instructions for enabling it on its home page, click the drop-down link 'Technical Details about this PPA'. [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

It sounds like you were following instructions to create your own PPA.

---

### Post by demonboy on 2010-11-07
Blimey, I certainly don't want to be doing that :P

---

