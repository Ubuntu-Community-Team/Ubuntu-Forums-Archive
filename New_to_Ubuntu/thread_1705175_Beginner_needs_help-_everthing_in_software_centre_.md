---
title: "Beginner needs help- everthing in software centre blocked as unauthorised ..."
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Hektik Keef on 2011-03-11
[SIZE=2]      Firstly,  I am beginner with only 72 hours experience of Linux and very limited experience with Windows, though many years ago I was pretty good with my Amiga, so am not a complete computer novice.  And a happy greetings to you all- But now to the first problem...
 I am almost completely flummoxed by the way seemingly the entire range of add ons available from the Ubuntu software center is being blocked as coming from unauthorized sources. I have managed to install the Vlc media player and Ktorrent through synaptic package manager, but I would appreciate help in finding the source of this block, as i am stuck...[/SIZE]

---

### Post by dFlyer on 2011-03-11
Have you added repositories?

---

### Post by Hedgehog1 on 2011-03-11
Hektik Keef,

I spent many happy hours editing video with my Amiga(s).

To be honest, I have not enjoyed using an OS as much until the more recent releases of Ubuntu.  Amigas were very ahead of their time...

Anyway, to help you we need a bit more information, please.

Please tell us the basics about your hardware: Mac or PC, Desktop/Laptop, Processor and RAM, size of hard disk.

Also what version of Ubuntu did you install and are you dual booting?

***The Hedge***

:KS

p.s. Were you installing using the **EASY** Ubuntu Software Center or the **HARD** Synaptic Package Manger?

---

### Post by oldos2er on 2011-03-11
Can you open a terminal (menus Applications, Accessories, Terminal), run **sudo apt-get update**, and if there are errors, please post the full terminal output here.

---

### Post by Hektik Keef on 2011-03-11
[SIZE=2]That was darn fast- Apologies for not putting the details of my system and the installation.  The thought occurred to me nanoseconds after I Clicked the post button. I was using Windows 7 for a week- but its rubbish, so i downloaded Ubuntu 10.10 64 bit on 4 gig flash drive with the last dying gasps of Windows, then installed on hard drive straight away.  The computer itself is a tower containing quad core 2.4 GHZ pentium, 4 gig DDr3 memory, and have no graphics or sound card installed yet, ones ordered, ones not.  Drives are 250Gb system drive and second 1.5 Tb storage drive, both Seagate and SATA2.  DVD drive disconnected waiting for splitter cable.  There is not a trace of microsoft to interfere from the dual booting I did for a day as that installation of Ubuntu was run on an old 6 gig IDE Atapi drive that was lying around after I gutted the case to install current bits.  And I don't know what a repository is or what it does, 99% sure i have not altered or installed any, unless they came with some codecs on the sly.[/SIZE]  

[SIZE=2]Keef[/SIZE]
[SIZE=2]   PS Do i get tarred and feathered for having an Xbox?[/SIZE]

---

### Post by Hektik Keef on 2011-03-11
sudo app line is doing something...

---

### Post by Hektik Keef on 2011-03-11
Appears sudo app... Terminal command line worked.  Certainly has now installed 7zip- suggestions welcome on anything that may be better- and the update manager has kicked in doing its thing.  Many thanks...  Could I please have an explanation of the meaning of sudo? And a nudge in the direction of education of how to get better with Terminal...

---

### Post by Frogs Hair on 2011-03-11
Here you go.[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)  
[http://linux.about.com/od/commands/l/blcmdl8_sudo.htm](http://linux.about.com/od/commands/l/blcmdl8_sudo.htm)

---

### Post by ikt on 2011-03-11
> **Hektik Keef said:**
> blocked as coming from **unauthorized** sources. 

**Unauthenticated***

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/705988](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/705988)

Slightly different words, added an extra 10 minutes to my searching haha

But that's ok, it seems like a bug, a pretty bad one I must admit, I will check to see if there has been any progress on it.

---

### Post by Hektik Keef on 2011-03-11
Sorry for the Unauthorised/ Unauthenticated mistake.  Will be more careful with me lingo. Cheers for the two links for Terminal improvement, although that is for tomorrow. Brain cant hack that at gone 2 in the morning. Yet...  And yes seems fixed and everything installing fine now and think was a bug, not my tired stumbling fingers pressing something silly yesterday.   Next, coming in a thread near you from a small provincial town very soon-  please make my Ktorrent work...

---

### Post by ikt on 2011-03-11
> **Hektik Keef said:**
> Sorry for the Unauthorised/ Unauthenticated mistake.  Will be more careful with me lingo. 

All good, it's a bug that you shouldn't be seeing anyway :(

> **Hektik Keef said:**
> 
Next, coming in a thread near you from a small provincial town very soon-  please make my Ktorrent work...

Once you get all this initial configuration issues sorted out it becomes a lot easier from here, you're on the right path :)

---

### Post by oldos2er on 2011-03-11
> **Hektik Keef said:**
>  Could I please have an explanation of the meaning of sudo? And a nudge in the direction of education of how to get better with Terminal...


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

