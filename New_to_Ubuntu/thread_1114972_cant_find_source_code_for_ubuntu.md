---
title: "cant find source code for ubuntu"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by cooltarlee on 2009-04-03
plz tell me where i can find source code for diffrent packages of ubuntu

---

### Post by unoodles on 2009-04-03
> **cooltarlee said:**
> plz tell me where i can find source code for diffrent packages of ubuntu

apt-get source <package>

You may want to be sure that you have the libraries required to build that package.
To do this type (as root):

apt-get build-dep <package>

Edit: Also, for future reference, try not to revive old threads (check the dates). Its better just to start a new thread.

---

### Post by cooltarlee on 2009-04-03
plz tell me where i can find source code for ubuntu packages

---

### Post by UltraMathMan on 2009-04-03
Have a look kere [http://ubuntuforums.org/archive/index.php/t-14756.html]("http://ubuntuforums.org/archive/index.php/t-14756.html").

-Hope this helps :)

---

### Post by CatKiller on 2009-04-03
Enable the source repositories, and then use ```
sudo apt-get source *package*
``` to download the source of the package you're interested in.

---

### Post by cooltarlee on 2009-04-04
how do i get source code for packages in ubuntu

---

### Post by hyper_ch on 2009-04-04
(1) enable the sources repositories (by default you have the binary only)

(2) use "apt-get source PACKAGE"

that will download the source of that package to your current directory.

---

### Post by cooltarlee on 2009-04-04
Plz tell me where can i find source code for ubuntu . Coz i wanna edit the packages . Plz also tell me where can i find source code for all the desktop tasks like applications places and system wots d source code for dese packages

---

### Post by cooltarlee on 2009-04-04
Plz tell me where can i find source code for ubuntu . Coz i wanna edit the packages . Plz also tell me where can i find source code for all the desktop tasks like applications places and system wots d source code for dese packages

---

### Post by meierfra. on 2009-04-04
Please do not start multiple threads on the same subject.

---

### Post by hyper_ch on 2009-04-04
did you actually read what I wrote?

---

### Post by cooltarlee on 2009-04-04
Ya i hv read dat but its saying dat unable to find d packages

---

### Post by hyper_ch on 2009-04-04
what command did you type? what's the exact output of it?

---

### Post by zvacet on 2009-04-04
Sys>admin>software sources>check sources and refresh.

```
sudo apt-get source packagename
```

If still no luck post here output of 

```
cat /etc/apt/sources.list
```

---

### Post by hyper_ch on 2009-04-04
(1) you did not post the complete output...

(2) you need to replace PACKAGENAME  by a real existing package name.

---

### Post by k3lt01 on 2009-04-04
> **cooltarlee said:**
> Plz tell me where can i find source code for ubuntu . Coz i wanna edit the packages . Plz also tell me where can i find source code for all the desktop tasks like applications places and system wots d source code for dese packagesPlease use correct spelling, txt msg typos are aggravating.

---

### Post by cooltarlee on 2009-04-04
sudo apt-get source abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.dsc'
Skipping already downloaded file 'abiword_2.6.4.orig.tar.gz'
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in abiword-2.6.4

---

### Post by cooltarlee on 2009-04-04
the above code is shown . wot shud i do now

---

### Post by occams_beard on 2009-04-04
> **cooltarlee said:**
> sudo apt-get source abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.dsc'
Skipping already downloaded file 'abiword_2.6.4.orig.tar.gz'
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in abiword-2.6.4


Um... :rolleyes:


How are you going to edit the source code when you don't even seem to understand the concept of downloading src packages?

---

### Post by cooltarlee on 2009-04-04
if u know wot that meants plz tell me . And if you dont know about that then plz keep your mouthshut

---

### Post by occams_beard on 2009-04-04
> **cooltarlee said:**
> if u know wot that meants plz tell me . And if you dont know about that then plz keep your mouthshut

No need to get snippy.

> 
the above code is shown . wot shud i do now


Perhaps you should buy a book? You don't really expect anyone to guide you through learning how to program and/or modify abiword on this thread do you?

[This book might be helpful]("http://www.amazon.com/C-Dummies-2nd-Dan-Gookin/dp/0764570684/ref=sr_1_1?ie=UTF8&s=books&qid=1238831871&sr=1-1")

---

### Post by hyper_ch on 2009-04-04
> **k3lt01 said:**
> Please use correct spelling, txt msg typos are aggravating.
Not everyone is of english speaking origin. Assuming that everybody must know english perfectly well is even a lot worse than making typos.

> **cooltarlee said:**
> sudo apt-get source abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.dsc'
Skipping already downloaded file 'abiword_2.6.4.orig.tar.gz'
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in abiword-2.6.4
Well, what does that actually say?

---

### Post by cooltarlee on 2009-04-04
> **hyper_ch said:**
> Not everyone is of english speaking origin. Assuming that everybody must know english perfectly well is even a lot worse than making typos.


Well, what does that actually say?

plz tell me wots d meaning

---

### Post by k3lt01 on 2009-04-04
> **hyper_ch said:**
> Not everyone is of english speaking origin. Assuming that everybody must know english perfectly well is even a lot worse than making typos.hyper, we will have to agree to disagree here. I don't know if you or cooltarlee have noticed but this is an English speaking forum, there are language forums for other languages within the Ubuntu community. Lso it ain't bout aktule spellin, if't wuz i'd b chippin evry Merican ere, bt mor bout txt lingo bein noying.

---

### Post by hyper_ch on 2009-04-04
> **k3lt01 said:**
> I don't know if you or cooltarlee have noticed but this is an English speaking forum
No, I didn't notice.

> **k3lt01 said:**
> there are language forums for other languages within the Ubuntu community.
Show one that is as big as this here? Btw, if english wasn't the most common language of the internet but something else, how would you feel if you get scolded for your "inadequacy" in that other language?

Btw, please have a look at the CoC Section I.1:
> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.

---

### Post by hyper_ch on 2009-04-04
> **cooltarlee said:**
> plz tell me wots d meaning

What could they mean?

---

### Post by pg-13(prostitute) on 2009-04-04
i was hangin out in the valley and john gotti jr had ubuntu on his laptop.

we swapped some laughs.

---

### Post by k3lt01 on 2009-04-04
> **hyper_ch said:**
> No, I didn't notice.


Show one that is as big as this here? Btw, if english wasn't the most common language of the internet but something else, how would you feel if you get scolded for your "inadequacy" in that other language?

Btw, please have a look at the CoC Section I.1:I'm taking this private

---

### Post by overdrank on 2009-04-04
Please keep the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") in mind when posting.

---

### Post by pg-13(prostitute) on 2009-04-04
woa, those 6 demerits i gotted yesterday clued me in sissssir

---

### Post by 3rdalbum on 2009-04-04
Considering that nobody has answered the latest question, I'll do this.

cooltarlee, the error message is telling you all that you need to know:

```
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.dsc'
Skipping already downloaded file 'abiword_2.6.4.orig.tar.gz'
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.diff.gz'
```

It's telling you that it has already downloaded the source code files, probably from the first time you ran the command. The source code archive is in the current directory, that is, your home directory.

```
Skipping unpack of already unpacked source in abiword-2.6.4
```

And it has already unpacked the archive for you.

You can have a look at the source code; it's in the "abiword-2.6.4" directory inside your home directory.

---

### Post by cooltarlee on 2009-04-04
> **3rdalbum said:**
> Considering that nobody has answered the latest question, I'll do this.

cooltarlee, the error message is telling you all that you need to know:

```
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.dsc'
Skipping already downloaded file 'abiword_2.6.4.orig.tar.gz'
Skipping already downloaded file 'abiword_2.6.4-4ubuntu4.diff.gz'
```

It's telling you that it has already downloaded the source code files, probably from the first time you ran the command. The source code archive is in the current directory, that is, your home directory.

```
Skipping unpack of already unpacked source in abiword-2.6.4
```

And it has already unpacked the archive for you.

You can have a look at the source code; it's in the "abiword-2.6.4" directory inside your home directory.

thank you very much for solving my problem
could you please do me 1 more favour . Could you please tell me which is the exact code is it makefile text or anything else

---

### Post by bapoumba on 2009-04-04
Several threads merged in here.

---

