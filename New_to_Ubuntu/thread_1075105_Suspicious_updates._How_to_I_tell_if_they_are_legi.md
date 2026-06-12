---
title: "Suspicious updates. How to I tell if they are legit?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Razmear on 2009-02-19
I've got an icon telling me I have 3 updates available but when I went to install them I got a warning that they are unverified and could be used to take over my system. 2 of the updates are new files, which makes me more suspicious cuz how could it update something that I don't have installed? 

The updates are: 
libammb3 - floating point adaptive multi-rate AMP speech codec - Medibuntu package size 134kb

libamrwb3 - Adaptive multirate wideband AMR-WB speech codec - Medibuntu package size 112kb

mplayer (why is this unable to be verified???) 

There was also a sudo update that did not raise any warning flags that I did install earlier. 

So does anyone know if these particular updates are legit, and how would I verify in the future that new updates are ok to install? 

Thanks,
eb

---

### Post by Triggerhapp on 2009-02-19
Updates are only going to be from repositories that you have personally added, or the built in Ubuntu defaults. Although I dont use it personally, I imagine Medibuntu repository has newer version of mplayer and the libraries it needs, which are those packages.

If you dont trust medibuntu, remove it from your sources list

---

### Post by Ms_Angel_D on 2009-02-19
The [Medibuntu]("http://www.medibuntu.org/") updates are part of the [medibuntu ]("http://www.medibuntu.org/")repository. The reason you get the warning is because the repository can't be officially supported by Canonical because there are copyrights in some countries on the codecs they use for playing back certain media, such as DVD's and MP3's.

Based on what I'm reading in your post you have no worries and can update those just fine.

I'm unsure about the Mplayer issue you'll have to provide more information.

---

### Post by jerome1232 on 2009-02-19
> **Razmear said:**
> I've got an icon telling me I have 3 updates available but when I went to install them I got a warning that they are unverified and could be used to take over my system. 2 of the updates are new files, which makes me more suspicious cuz how could it update something that I don't have installed? 

The updates are: 
libammb3 - floating point adaptive multi-rate AMP speech codec - Medibuntu package size 134kb

libamrwb3 - Adaptive multirate wideband AMR-WB speech codec - Medibuntu package size 112kb

mplayer (why is this unable to be verified???) 

There was also a sudo update that did not raise any warning flags that I did install earlier. 

So does anyone know if these particular updates are legit, and how would I verify in the future that new updates are ok to install? 

Thanks,
eb

That means either 
a) You don't have the public key for medibuntu 
b) someone at medibuntu forgot to sign the packages before they went out, or 
c) (actually unlikely but this is what the public key thing is there for) the packages aren't actually from medibuntu's repository (man in the middle attack type of thing)

So first I would check to see if you have their public key added, if you do I'd wait to install the updates, they should be signed if they are from medibuntu's repository.

---

### Post by bodhi.zazen on 2009-02-19
See this page for how to add thee keys :twisted:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you do not know what keys are or how to use them or how they work, see

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Sorry to answer in links, but it saves a ton of typing.

If you have additional questions, please ask ;)

---

### Post by Razmear on 2009-02-19
> **jerome1232 said:**
> That means either 
a) You don't have the public key for medibuntu 
b) someone at medibuntu forgot to sign the packages before they went out, or 
c) (actually unlikely but this is what the public key thing is there for) the packages aren't actually from medibuntu's repository (man in the middle attack type of thing)

So first I would check to see if you have their public key added, if you do I'd wait to install the updates, they should be signed if they are from medibuntu's repository.

How would I check to see if I have their public key? I've never specifically requested or installed it. 
a & b seem the most likely possibilities, but being a noob and just getting things running smoothly I didn't want to hose the system now by ignoring a warning message. 

Thanks for the help,
eb

edit: thanks bodhi for answering my question faster than I could type it in :)

---

### Post by Razmear on 2009-02-19
Thanks Bodhi! 

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

grabbed the public key and removed the warning message. 

eb
:popcorn:

---

### Post by bodhi.zazen on 2009-02-19
> **Razmear said:**
> Thanks Bodhi! 

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

grabbed the public key and removed the warning message. 

eb
:popcorn:

You are most welcome and you obviously have learned more then if I had simply given you the commands. This is good ;)

---

