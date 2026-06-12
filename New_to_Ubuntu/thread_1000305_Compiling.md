---
title: "Compiling?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by cartisdm on 2008-12-02
I've been using linux for over 2 years now, but I'll admit I'm a really lazy ubuntu user.  Whenever I install stuff I either use Add/remove, synaptic, apt-get, or find the .deb version and have it go through the installer.

Why do some things need to be compiled etc?  I've compiled some stuff before but only when I had an idiot proof walkthrough to help me do it.  In Windows everything that you need to install comes as a .exe and you just extract it, and the installer wizard kicks in.

What's different about the way programs are installed and what exactly happens when you compile?

---

### Post by bruce89 on 2008-12-02
> **cartisdm said:**
> Why do some things need to be compiled etc?  I've compiled some stuff before but only when I had an idiot proof walkthrough to help me do it.  In Windows everything that you need to install comes as a .exe and you just extract it, and the installer wizard kicks in.

What's different about the way programs are installed and what exactly happens when you compile?

Compiling source code is turning high level code into binary instructions for the CPU to use.

Linux distributions all have different versions of compilers and libraries, so one executable might work on Debian Etch, but not on other distros. Also, there are so many CPU architectures, so a binary compiled on one won't run on another (i386 and HPPA for example).

The thing with Windows is that the toolchain has been much the same for a long time.

---

### Post by cartisdm on 2008-12-02
Got it, so everything that I install that doesn't require compiling has basically already been "prepped" for Ubuntu.  And things I grab that need to be compiled are just generic  linux programs?

---

### Post by Captain_tux on 2008-12-02
Here's an article on the **Linux Format Wiki** that helps explain the why and how of compiling: 

[http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy]("http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy")

Hope this helps to answer your questions!

---

### Post by bruce89 on 2008-12-02
> **cartisdm said:**
> Got it, so everything that I install that doesn't require compiling has basically already been "prepped" for Ubuntu.  And things I grab that need to be compiled are just generic  linux programs?

All packages will be compiled (or just built) by a buildbot maintained by Canonical. It is then packaged up into a Debian package by the buildbot and sent to repository mirrors all around the world.

Just because you don't have to build it doesn't mean it doesn't have to be built somewhere along the line.

---

### Post by loomsen on 2008-12-02
Compiling, hmm, one could say is the process of translating a high-level programming language to a low-level-language as understood by machines.
High-Lvl languages have many advantages, if you're a human being, such as much better readable than low-lvl language, thus easier to trace bugs, easier to write and so on. All in all, it easens a developers life if he writes his app in a high-lvl language a lot.
Now, while compiling, the code is parsed, all dependencies (sth like dictionaries) are fetched, and finally the code is translated back into machine-capable language.

Now there are basically 2 different types of architectures, 32bit and 64bit.

Windows usually ships with 32bit by default (only very few 64bit versions around, due to the need of providing 2 different versions very few 64bit apps for win as well)


This is the one hand side, the other, imho even more important side is the difference between commercial and opensource software in general.

If Microsoft announces a new Windows Version, this Version will have it's final state as soon as it's shipped, except updates and patches of course.

Now the major difference is that OpenSource Software will never reach it's final status. It's more like an ever ongoing development, aiming towards a certain goal, tho never actually achieving this goal. The closer you get to your goal, the further you'll push your goals.

Thus, a patch provided by MS is intended to provide the status Win had when it was released. If you install a WinXP today, it won't defer in its hardware capabilities compared to a 3 year old install if WinXP.

While, a kernelupdate in linux usually provides better support, new features and so on. 


So, in total this means:

A Win developer has his base and his intents are to secure, maintain and harden this base.
A UNIX developer has a goal, which is hard to define itself, and provides upgrades towards this imaginary goal.

So it's very easy to provide an application for windows, which will be able to run on nearly any installation of windows, independent of the hardware specifications.
But, as Linux not only has to handle different archs, but as well different features of each kernel (many user configure their own kernel for instance). So, applications provided have to be translated for each system, which is done by compiling, so that a 32bit CPU can handle an application just as a 64bit CPU can. The source often is the same, but afterwards, translated into different languages. Configurations could be compared to different dialects throughout the same country, here in Germany we have a whole lot of different dialects, but still every german from Hamburg will understand what someone from Bavaria or so tells him. But maybe he has to ask back here and there.
A compilation would be as if the bavarian and the hamburger wouldn't talk to each other, but talk to each other by writing it down. This way it's clear and dialects are obsolete. 

Got it?
A generic pkg will always work, just not as smooth as a custom compiled one.

---

### Post by bruce89 on 2008-12-02
> **loomsen said:**
> 
A generic pkg will always work, just not as smooth as a custom compiled one.

That's not quite the case. If you compile a package with ancient versions of all the libraries it uses, it's more likely it will work on more distributions. That is what the LSB people hope anyway.

Also, the kernel is not the main issue here, it's all the libraries the programs links with.

---

### Post by loomsen on 2008-12-03
> **bruce89 said:**
> That's not quite the case. If you compile a package with ancient versions of all the libraries it uses, it's more likely it will work on more distributions. That is what the LSB people hope anyway.


Well, probably it will, tho, still, if you compare a pkg you compiled on your machine, and the same pkg compiled on another, similar but not equal machine, bot will work, for sure. But assuming high loads, otherwise comparing would be useless, the custom compiled will probably perform a little better. 

This, however, is an economic and logical rule. Optimization (in this case, in other cases customization equals the sense) and (mass-)compatibility are negatively correlated. This is trivial.

However, I was actually answering to the threadstarters initial question, and tried to use simple words and allegories, so that you don't need to know what an octet is for instance, but still get the meaning.

And the initial question was:
> what exactly happens when you compile?

I don't think I have to explain to you what happens during a compile, and if cartisdm knew what LSB is he prlly wouldn't have posted this question in the Absolute Beginner forum...

> Also, the kernel is not the main issue here, it's all the libraries the programs links with.

Does it make a difference bearing the question in mind?

Compiling still means translating high level programming language into low level machine code.

---

### Post by Sealbhach on 2008-12-03
It's fascinating to watch the terminal while compiling is going on. I tried my hand at compiling a few things, first I followed that example in Linux Format magazine (see link earlier in thread. That worked fine. 

Then I attempted to compile Firefox about three times, but every time, the compiled application woudln't run, I got segementation fault, buffer overflow etc.

Finally, I compiled Banshee, just to see if I could. It installed and worked fine for about two days, then it began to crash on startup, so I deleted it and got the one from the repos.

The trickiest thing I think is making sure you have all the dependencies before you start. Then it's simply a matter of downloading the source, extracting the tarball and executing these commands in the source folder:

```
./configure
sudo make
sudo make install
```

I think you always have to do it as root.


.

---

### Post by Paqman on 2008-12-03
> **cartisdm said:**
> I'm a really lazy ubuntu user.  Whenever I install stuff I either use Add/remove, synaptic, apt-get, or find the .deb version and have it go through the installer.


That's not lazy at all, that's best practice. It's how the system is supposed to be used.

---

### Post by oldos2er on 2008-12-03
./configure 
 sudo make
 sudo make install

 You usually don't need to run make with sudo--not in my experience, at least.

---

