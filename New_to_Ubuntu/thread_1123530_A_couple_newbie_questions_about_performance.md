---
title: "A couple newbie questions about performance"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by acesnyp3r on 2009-04-12
I just started using Ubuntu 8.10 a few days ago (loving everything about it so far) after using Windows XP exclusively for the last 6 years. Thanks largely to Google I've managed to get everything up and running without too much trouble. So far, everything is booting up and running roughly as fast as my bare-bones XP install I use for gaming, and I'd like to keep it that way, so I have a few questions about maintaining performance that I didn't have any luck finding answers to.

1. According to the Synaptic Package Manager right now I have 1334 packages installed, and most of them look like various lib- packages. Could I make any tangible gains in performance/boot times by weeding through and getting rid of some of the ones I don't need, or are these only loaded on demand and otherwise won't impact performance?

2. On a related subject, how safe are the default software repositories? Are there any known instances of malicious packages getting uploaded to the repository as security updates or anything like that?

3. Does Ubuntu have any rough analogue to the Windows registry in the sense that something's going to get crapped up as I install/remove various programs and drivers and hurt performance or cause problems eventually? If so, are there any good tools to help clean it up?

---

### Post by nandemonai on 2009-04-12
> **acesnyp3r said:**
> I just started using Ubuntu 8.10 a few days ago (loving everything about it so far) after using Windows XP exclusively for the last 6 years. Thanks largely to Google I've managed to get everything up and running without too much trouble. So far, everything is booting up and running roughly as fast as my bare-bones XP install I use for gaming, and I'd like to keep it that way, so I have a few questions about maintaining performance that I didn't have any luck finding answers to.

1. According to the Synaptic Package Manager right now I have 1334 packages installed, and most of them look like various lib- packages. Could I make any tangible gains in performance/boot times by weeding through and getting rid of some of the ones I don't need, or are these only loaded on demand and otherwise won't impact performance?

2. On a related subject, how safe are the default software repositories? Are there any known instances of malicious packages getting uploaded to the repository as security updates or anything like that?

3. Does Ubuntu have any rough analogue to the Windows registry in the sense that something's going to get crapped up as I install/remove various programs and drivers and hurt performance or cause problems eventually? If so, are there any good tools to help clean it up?

1. Correct, plus I'd assume all the libs you have currently installed are needed for various apps installed. You can run apt-get autoremove in terminal to clean up any packages that are installed but not needed.

```
$ sudo apt-get autoremove
```

2. I've never once heard of this happening. Bugs maybe, but that's what updates are for ;) The parent software repos are maintained by Canonical.

3. Programs are all independent, if something craps up, reinstall it.

Welcome to Ubuntu. :D

---

### Post by acesnyp3r on 2009-04-12
> **nandemonai said:**
> 
```
$ sudo apt-get autoremove
```

That's awesome, thanks a lot!

---

### Post by Sidewinder1 on 2009-04-12
First of all...WELCOME!!! I was, where you are, a little over a year ago and haven't looked back.
To give you some quick answers without explanation:
1. For the most part, NO, only loaded on demand.
2.Very safe; never had a problem.
3. I'll let others more knowledgeable and eloquent answer that one but suffice to say there's little maintenance / defragging necessary.
Good luck and enjoy... :-)
Side

---

### Post by emshains on 2009-04-12
> **acesnyp3r said:**
> I just started using Ubuntu 8.10 a few days ago (loving everything about it so far) after using Windows XP exclusively for the last 6 years. Thanks largely to Google I've managed to get everything up and running without too much trouble. So far, everything is booting up and running roughly as fast as my bare-bones XP install I use for gaming, and I'd like to keep it that way, so I have a few questions about maintaining performance that I didn't have any luck finding answers to.

1. According to the Synaptic Package Manager right now I have 1334 packages installed, and most of them look like various lib- packages. Could I make any tangible gains in performance/boot times by weeding through and getting rid of some of the ones I don't need, or are these only loaded on demand and otherwise won't impact performance?

2. On a related subject, how safe are the default software repositories? Are there any known instances of malicious packages getting uploaded to the repository as security updates or anything like that?

3. Does Ubuntu have any rough analogue to the Windows registry in the sense that something's going to get crapped up as I install/remove various programs and drivers and hurt performance or cause problems eventually? If so, are there any good tools to help clean it up?

Hello acesniper,
I understand you really are enjoying your ubuntu build. Now, onto the questions:
1. The default libs are almost vital to keep your system going, and they don't actually make your computer slower. Although, if you are running Ubuntu (not kubuntu), you should try to remove all kapplications and klibs, because they are a bit heavy and mostly unneeded in a gnome desktop environment. 
2. The content of default repositories is added by ubuntu developers, so I don't think you will ever encounter a malicious application. But be aware of what you are installing, because you wouldn't want to install different drivers, DE etc. That could leave you at the command line with a basic browser. You should better stick to Add/Remove app under the application menu, if you are a novice user. But, when you'll become more experienced and start wanting to experiment with different stuff, you'll see you'll get used to adding new repo's, using apt-get and synaptic, because to get some specific apps without compiling from source, you need to add specific repositories. 
3. Well, the gnome desktop enviroment has a registry system, but the chance of screwing up something with that is the same as finding a needle in a haystack. Linux mostly uses config files, which can be found under /etc/, I think.

Thanks for your attention and time to try to understand my bad english.

---

### Post by Sidewinder1 on 2009-04-12
Man,....you guys are quick....Guess that's what I get for never learning how to type.
:-(  :-)

---

### Post by Paqman on 2009-04-12
> **acesnyp3r said:**
> 
1. According to the Synaptic Package Manager right now I have 1334 packages installed, and most of them look like various lib- packages. Could I make any tangible gains in performance/boot times by weeding through and getting rid of some of the ones I don't need, or are these only loaded on demand and otherwise won't impact performance?


No, packages won't slow you down. You might want to have a look in System > Prefs > Sessions and have a look at what services you're running. If you know you won't be using Bluetooth or the accesibility options, for example, then just turn them off.

> 
2. On a related subject, how safe are the default software repositories? Are there any known instances of malicious packages getting uploaded to the repository as security updates or anything like that?


The official repos are absolutely 100% safe. Quality control is a big issue, so there are people being paid to worry about this for you.

You hit on a good point though: it's best not to add any additional repos from an untrusted source. If in doubt, post it here and people will be able to tell you whether it's trustworthy.

> 
3. Does Ubuntu have any rough analogue to the Windows registry in the sense that something's going to get crapped up as I install/remove various programs and drivers and hurt performance or cause problems eventually? If so, are there any good tools to help clean it up?

Nope, no registry. Some other Windows hassles that you can kiss goodbye are defragging and malware scans. Linux systems are pretty stable, and don't really need as much hands-on as Windows systems do. The most important thing is to run the updates that your system notifies you about. You can modify your update preferences in System > Admin > Software Sources.

Have fun!

---

### Post by acesnyp3r on 2009-04-12
Damn, thanks guys. If I knew the community was this active and helpful I might have installed Ubuntu sooner.

@emshains: What are kapplications and klibs and how would I know which of them I have?

---

### Post by Paqman on 2009-04-12
> **acesnyp3r said:**
> What are kapplications and klibs and how would I know which of them I have?

He means applications intended for KDE instead of Gnome. Personally I wouldn't worry about it.

Basically, if you install a KDE app on Gnome, it'll might have to download a ton of dependencies (stuff that would already be on a KDE system). The when you launch the KDE app it'll be a little slow to launch as it pulls in the extra KDE libs that would already be running on KDE desktop. 

Upshot of all this: KDE apps on Gnome can be fat downloads, and will launch slightly slower. Vice versa for Gnome apps on KDE.

Personally, that doesn't both me at all. I like Amarok for example, so I use it on Gnome. But some people are purists about it. Up to you.

---

### Post by emshains on 2009-04-12
> **acesnyp3r said:**
> Damn, thanks guys. If I knew the community was this active and helpful I might have installed Ubuntu sooner.

@emshains: What are kapplications and klibs and how would I know which of them I have?

Well, you can see, maybe, there are a lot of applications, that are named with names, that have a weird way of using the letter G, like GPic image viewer, that's because they are made for the gnome desktop environment. If you search in synaptic for gnome, you'll see what I am talking about. 
Kapps and klibs are applications made for the K desktop environment, and the main difference between those two environments, is that kde preloads everything on start-up (not everything, but you get the pic), but gnome picks up as you're going. And, if you have some kapps installed, you may suffer a performance penalty, just because there are different processes doing the same thing, just for each D.E. I run gnome, but sometimes I have some processes like  khelper, kblock running, and those are the preloads. They are of no use, if you don't run kde apps daily, so I suggest you remove any unneeded apps that are using klibs. In synaptic, if you search for libk, you'll see which are which.

EDIT: damn, I need to start typing faster!

---

### Post by clive littlewood on 2009-04-12
Hi

Kapps and Klibs are the apps and library files associated with the KDE desktop.

If you are running Gnome then MOST of these will not be used.

I say most because some cross desktop apps might be using them eg. Amarok

My advice would be to leave them as you would not notice any speed benefit by removing them.

Clive

---

### Post by tofiluk on 2009-04-12
thanks to your posts i learned a lot. hahahaha... :D

---

### Post by The Cog on 2009-04-12
I seem to remember there was a case of a mirror serving a corrupt for a few days, perhaps 2-3 years ago. It was somewhere like Taiwan, I think. And I don't remember if it was a deliberate malware plant or just a corrupt package.

And I would argue that the apt-get repository database can be a little similar to the registry. It can make things difficult if that gets corrupted, which is rare but can happen.

---

### Post by txcrackers on 2009-04-12
> **emshains said:**
> Kapps and klibs are applications made for the K desktop environment, and the main difference between those two environments, is that kde preloads everything on start-up (not everything, but you get the pic), but gnome picks up as you're going.

Your assertion is wrong - the **ONLY** "pre-load" of either KDE or Gnome is the base system and any auto-start programs. There is no difference between the two in this regard.

---

### Post by Lunx on 2009-04-12
> **acesnyp3r said:**
> I just started using Ubuntu 8.10 a few days ago (loving everything about it so far) after using Windows XP exclusively for the last 6 years

First of all I'd also like to welcome you to Ubuntu and The Community, I hope Linux is able to give you all you want and require in an OS. I'm new too it all myself, escaped the clutches of Microsoft at the beginning of the year, not regretted it for a moment.

As for your comments on getting a performance OS which also boots fast, there are heaps of ways to create what what you want ( a big strength of Linux, so d*mn configurable). You can go with the full install and then remove apps you have no need for, or as said earlier you can simply disable them. You can also choose to go with a minimal installation, then build on it to suit your needs. You can change windows managers and disable decorators if needed and you can easily install other desktop environments and run your session using them if you wish. I also find that running applications such as conky and gkrellm is very helpful in understanding your system and then letting you decide what you wish to run and what you don't, as well as using them to help pinpoint trouble when stuff goes pear shaped.

You sound like you are pretty comfortable with Linux and Ubuntu thus far, so I'll suggest you may even want to have a play with some other distros at some stage. I'll suggest Puppy Linux is worth a look, so small it fits into RAM and runs happily from there. I began using it today and am amazed how well it works, fast and functional. Out of the box everything "just worked" and I didn't even need to go in search of codecs to get my sound working as I have to with Ubuntu. CrunchBang may also be worth a look to get an idea of OpenBox, it's built on Ubuntu and so it's also simple to use.

That just about covers all my suggestions so I will finish by saying welcome again. If you remember that even 'though Ubuntu is "Linux for Humans" it was also built by humans, so occasionally it may let you down. Good thing is this community as you can always find help, support and information to get you up and running again when things decide to break. Until now I haven't had a problem that couldn't be resolved, even 'though the solution was occasionally found with gritted teeth and much muttering under breath. 

Hope you enjoy your journey with it all.

---

