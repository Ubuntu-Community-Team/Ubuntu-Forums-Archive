---
title: "Tips/Best practices on where to put programs?"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by egervari on 2010-10-16
Hi, I would appreciate some advice as to where are the best places to install programs that do not have packages. For example, are a variety of programs I'd like to install.

1. Java SDK from Sun
2. Maven
3. Idea
4. RubyMine

Most of these you don't build from source, but I'm not sure where the best place to put them, and should I do it as root, or my regular user account?

Also, if I do have to build something from source, where should I put the unziped source files?

Any other tips along these lines would be greatly appreciated. Thanks!

---

### Post by SadisticCheeto on 2010-10-16
If they are prepackaged programs, I would suggest placing them in opt. For the source files, you could just make a build folder in your home folder for storing those. That's what I have done before. Easy to keep track of them. I noticed that two of the programs you listed can be installed. The SDK (sun-java6-jdk) and Maven (maven2) are both available.

---

### Post by egervari on 2010-10-16
/opt - thanks! I'll definitely do that. Should I install as root? Or give /opt permissions to my main user account?

The problem with the sun jdk package is that I never got it to work right before. Idea complained that it was really the open-jdk package. I only got it to work by installing the java sdk from the oracle website a few days ago (wubi install... I'm now running a real ext4 install now).

As for maven, they are on version 3, so the maven 2 package is out of date.

---

### Post by SadisticCheeto on 2010-10-16
Fair enough on the packages. Yes, install them as root. You might have to chown to root, too.

---

