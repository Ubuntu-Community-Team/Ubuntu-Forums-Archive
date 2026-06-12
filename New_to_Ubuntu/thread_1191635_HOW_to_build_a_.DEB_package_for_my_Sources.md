---
title: "HOW to build a .DEB package for my Sources?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by drkameleon on 2009-06-19
Hello everybody, :D

I've written a program for *nix, [MathMachine]("http://sourceforge.net/projects/mathmachine/#item3rd-1")

The application is written in C++ and can be compiled and installed using

```
make
sudo make install
```

I should also mention that the program DEPENDS on a library ([GMP MP BigNum Library]("http://gmplib.org/")) which must be compiled/installed from sources beforehand.

Could you please explain to me STEP-by-STEP, how I could create a package, so that I could distribute it more easily? 

Thanks in advance! ;)

Dr.Kameleon

---

### Post by dje on 2009-06-19
[http://wiki.ubuntu.com/PackagingGuide/Complete]("http://wiki.ubuntu.com/PackagingGuide/Complete") ;)

---

### Post by drkameleon on 2009-06-19
Hmmm.... It seems to me I have a lot of reading to do... LOL

Thanks anyway, DJE! ;)

---

### Post by glennric on 2009-06-19
Did you know that GMP is in the repositories?  Its package name is libgmp3c2.  Of course to compile software that depends on it you need to install libgmp3-dev.  MathMachine compiles nicely with this version of GMP in the repositories.

---

### Post by Alias1407 on 2009-06-19
Or perhaps here...


[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)


Could be useful?

---

### Post by kostkon on 2009-06-19
Or for an easier way [*GiftWrap*]("http://giftwrap.tuxfamily.org/")...

---

### Post by Cheesemill on 2009-06-19
You could set yourself up with a Launchpad PPA
[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)

---

### Post by glennric on 2009-06-19
I have created a debian package from your source and uploaded it to my ppa.  Add my ppa repository
```
deb http://ppa.launchpad.net/glennric/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/glennric/ppa/ubuntu jaunty main

```
Then run "sudo apt-get update"

Then you can download the sources with "apt-get source mathmachine"

The important thing to look at is the "debian" subdirectory of "mathmachine-0.2.1".  That is what does all the work.
To create the deb run
```
cd mathmachine-0.2.1
dpkg-buildpackage
```

I am planning on deleting this from my repository in a few days.  I just put it there temporarily so that you could download it and see what I did.  You will want to make modifications to the packaging like change the maintainer to yourself, add a "copyright" file in the debian directory, etc.

---

### Post by drkameleon on 2009-06-19
Oh my god! I couldn't even imagine I would have so many answers in so little time.

THANK YOU ALL GUYS - REALLY! :D:D

One last favour : in the meantime, I played a bit with dh_make and debuild and managed to create a .DEB package... I've uploaded it to my own server (as you may have already noticed, I'm not that familiar with repositories yet...)

[http://portfolio.drkameleon.com/mathmachine_0.2.2-1_i386.deb]("http://portfolio.drkameleon.com/mathmachine_0.2.2-1_i386.deb")

**Could you please verify that it works? (it's actually a Terminal app and is executed using "mathmachine")**

Thanks again! ;)

---

### Post by drkameleon on 2009-06-19
> **glennric said:**
> Did you know that GMP is in the repositories?  Its package name is libgmp3c2.  Of course to compile software that depends on it you need to install libgmp3-dev.  MathMachine compiles nicely with this version of GMP in the repositories.

First, THANKS A LOT for your help! ;)

I suppose this detail must go to the debian/control file under build-depends, right?

And, if yes - which one? the libgmp3c2 and libgmpxx4ldbl OR libgmp3-dev? (just to make sure...)

By the way, I tried to add your repository in /etc/apt/sources.list and after "sudo apt-get update" I'm getting the following error...

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6C843CCE8505D44B
W: You may want to run apt-get update to correct these problems
```

(Probably, it's ridiculously simple but I can't figure out why...)

---

### Post by drkameleon on 2009-06-19
Well... I fixed the previous error, using...

```
gpg --keyserver keyserver.ubuntu.com --recv 8505D44B
gpg --export --armor 8505D44B | sudo apt-key add - && sudo apt-get update
```

("8505D44B" are the last 8 digits of the... missing key)

---

### Post by drkameleon on 2009-06-19
> **glennric said:**
> I have created a debian package from your source and uploaded it to my ppa.  Add my ppa repository
```
deb http://ppa.launchpad.net/glennric/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/glennric/ppa/ubuntu jaunty main

```
Then run "sudo apt-get update"

Then you can download the sources with "apt-get source mathmachine"

The important thing to look at is the "debian" subdirectory of "mathmachine-0.2.1".  That is what does all the work.
To create the deb run
```
cd mathmachine-0.2.1
dpkg-buildpackage
```

I am planning on deleting this from my repository in a few days.  I just put it there temporarily so that you could download it and see what I did.  You will want to make modifications to the packaging like change the maintainer to yourself, add a "copyright" file in the debian directory, etc.

OK, Glennric - I finally managed to get the sources package!!

You were 100% helpful - I greatly appreciate that! ;)

One clarification... does this mean, that by "replacing" the sources with my future ones, tweaking the text files in the "debian" subdirectory and doing a "dpkg-buildpackage" in the main sources dir, I will be able to be creating deb packages for my future releases???

Thanks one more time! ):P

---

### Post by drkameleon on 2009-06-19
OK. I figured the whole thing out - GlennRic, you really made my day!

:D:D:D

---

### Post by glennric on 2009-06-19
> **drkameleon said:**
> 
One clarification... does this mean, that by "replacing" the sources with my future ones, tweaking the text files in the "debian" subdirectory and doing a "dpkg-buildpackage" in the main sources dir, I will be able to be creating deb packages for my future releases???


Yeah, change the version to the appropriate number for the new release.  There are other things you may need to do also for later releases.  For example if you add dependencies make sure you add the dev package to the control files depency list.

---

