---
title: "libsdl... and more libs"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by nime1 on 2010-02-07
Hello.
I am beginner in linux so please help regarding problem.
I want to install libsdl-sound through synaptic and there says "libsdl-sound1.2-dev:
 Depends: libvorbis-dev but it is not going to be installed". Same is happend when I want to install liballog.dev". I downloaded required *.deb package (libvorbis-dev) but they dont want to install. Says: Error: Dependency is not satisfiable: libvorbis0a (= 1.2.3-3) through package installer. This messing me whole day! 
Anybody can help?

---

### Post by thulefoth on 2010-02-07
Hello nime1,

I looked in my Synaptic (Ubuntu 9.10), using the search-term 'libsdl-sound', and there is a libsdl-sound1.2  (I had all the dependencies, but not libsdl-sound1.2 itself.)

All the dependencies for libsdl-sound1.2 are 'greyed', for me, meaning they are already installed on my box.  I then hit Apply in the Menu, installed libsdl-sound1.2, and there were no problems.

You should not try to install dependencies yourself.  Select the package; it looks for dependencies, shows a list of what it needs:  the dependencies that are already on your box are greyed-out, and you just ignore them.  If it needs to install dependencies, it shows these **in bold** ... but you don't do it yourself - you just click the Mark button, and Synaptic gets them for you.

Let me know how it goes ... or any other issues?  :)

Ted

---

### Post by nime1 on 2010-02-07
Hello thulefoth,
I'm trying to install manually just because some libraryes dont want to install through synaptic. Actually - all of them which have dependency on libvorbis-dev. Thats why I want to install libvorbis-dev manually to get a chance that synaptic install further needed libraryes (SDL and Allegro) by itself because they "depend" on them. But my understanding of linux filesystem is not yet so "strong". I fight with them for a month, not longer. So, any help would be appreciated...

---

### Post by thulefoth on 2010-02-07
True - sometimes what the 'system' thinks, isn't what we want!  ;)

I don't see a libvorbis-dev in the libsdl-sound1.2 package.  There is other Orbis stuff there, but no -dev.  It's 3rd party?

Do you need the -dev for some kind of development work?  If you are just trying to run something, and not trying to program or create something, then the -dev library is usually not what we go for.

Your not confusing *.deb and -dev, are you?  They're totally different...

If you want this one particular library, and it is evidently not compatible with Ubuntu libsdl-sound1.2 (etc), then maybe you can get where you want to be by finding a version of SDL/Sound which does incorporate the -dev library you want.  Have you looked down this path? 

Is the -dev proprietary?  They might be blocking this use, on purpose?

---

### Post by nime1 on 2010-02-07
I find until now that deb files can install themselves alone with some included script together with dependencyes so I like them most! :)
Dev, as I assume is material for developement purposes, yes I understand that, partially.
What I am trying to do is to "play" some example programs included with "FreeBasic" programming language. They need SDL libraryes for run. They are for sound and some graphic, events and so... Most of them are installed but when I try to install through synaptic missed files I get: libsdl-sound1.2-dev:
 Depends: libvorbis-dev but it is not going to be installed, also libsdl-mixer. I think Freebasic need dev versions as they are tool for programming. Thats it... Please dont tell me that I should compile something from scratch because I'm unfamilliar with that stuff.

---

### Post by thulefoth on 2010-02-07
Yes, FreeBasic will need the -dev support.  That explains it.  For SDL support, the FreeBasic site sends us to the [SDL Simple Directmedia Layer]("http://www.libsdl.org/") site, and there I see [Frequently Asked Questions: Linux]("http://www.libsdl.org/faq.php?action=listentries&category=3").  Hmm!

Has other advise been to "compile"?

As can be seen at a glance, I don't have enough Beans to make a cup of soup.  :D

But I do know a couple things.  ;)

One is, you can get things to work right on Linux, by compiling them (this allows to make a unique version of the package that matches both your software & hardware environments).

Another is, compiling on Linux is not voodoo.  It may be, that by putting FreeBasic on Linux, you have already done tougher things than a straight-forward compile.

You're going to compile, with FreeBasic ... right?   You can do it with Linux & SDL, if that's what others are saying to do.

I have not done any compiling yet myself, either ... but I'm only one week old.  :-$

But 'compiling stuff' is a normal/expected operation, on Linux.  If a package of interest is offered in source code form, and the developers say, 'Yeah, just compile it ...', then I believe this is a straight-forward undertaking that a non-expert can succeed at.

Very soon, I will 'learn myself' how to install 3rd party stuff (I've played with FreeBasic before, on Windows), and how to compile stuff that should be compiled.   I am sure this is "practical".

Lastly, I have installed the Ubuntu Bambas2 environment (Visual Basic like), and it seems promising.  I know FreeBasic is cool ... but it's possible Gambus is, too.  

If this is what the issue you are grappling with boils down to - compiling - then I will shift my goals & schedule, and describe how a noob (me) learns to compile successfully.  

Mmm?

---

### Post by nime1 on 2010-02-07
Thank you very much for your willing to help anyway. I tryed Gambas and I must admit that it is cool. But I am also used to windows style of Basic (QB45, VB6) so FreeBasic looks to me most likely. I tryed few more Basics for linux (SDL, kBasic, RB, Small Basic etc.) and no one seems so good (QB45 (VB) like and so fast and open) like Freebasic so I decided to dig deeper in them. Unfortunately, I dont know much about linux so I expeted problems... I am not surprising but with time things will become simpler and simpler (I hope). Additionally, here is no IDE for FreeBasic and in Windows they have one (FBEdit) which is fully based on windows-system components. After all I decided to leave from anything related to microsoft so I investigate now to move - where? To cross-system language, similar with QB45 but with all possible modern extensions. IDE is not cruccial here. GTK is (or maybe QT or IUP)!
Those compiling stuff, I thing must go through some C or C++ program (compiler & linker) where i am totally unexpirienced so seem that I would leave this thing few days to sleep :)
Anyway, for now linux seems to me wery promissing platform where everybody can find something for them and look more human-like system than windows. Maybe because it is maded from people to people...

---

