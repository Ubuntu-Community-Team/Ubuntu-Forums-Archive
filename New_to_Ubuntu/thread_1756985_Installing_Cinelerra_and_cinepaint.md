---
title: "Installing Cinelerra and cinepaint"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by abnordude on 2011-05-12
I downloaded these tar files from the internet.

cinepaint-0.22-1.tar.gz

cinelerra-4.2-src.tar.bz2

I don't know how to install it.

Please help me.

---

### Post by yetiman64 on 2011-05-12
I don't know about those 2 packages generally, however here are a couple of links to Community Documentation for compiling software that may help you, good luck.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by abnordude on 2011-06-20
Could you tell me how to apply that in these two files here?

---

### Post by wep940 on 2011-06-20
> **abnordude said:**
> I downloaded these tar files from the internet.

cinepaint-0.22-1.tar.gz

cinelerra-4.2-src.tar.bz2

I don't know how to install it.

Please help me.

First, these are compressed files - like a zip file.   If you click on one to open it, it should open in the archive manager where you can tell it to extract.  I'm not sure about cinepaint, but the "src" in the cinelerra file name means it is source code - hence why you have to compile it.  There should be some form of readme when you decompress that file.

You will need to go to synaptic package manager and install the build-essential package before you can compile.  It's also quite possible that these two packages will have other dependencies that you'll have to fight one by one until they are all in.  That's why the package manager is preferred - it takes care of dependencies for you.

If you can't figure it out from each of the readme's post back, I'll download the packages, and see if I can walk you through it.

---

### Post by wep940 on 2011-06-20
I had more time here tonight to look at some stuff - the cinelerra website, on the download link, has instructions for setting up a ppa for ubuntu - if I remember correctly this will involve it showing you how to add a repository, if needed, and then you should be able to get/install it with the package manager.
**Ubuntu**

  [INDENT] Latest Cinelerra CV 2.1.5 for 10.10 Maverick Meerkat, 10.04 Lucid  Lynx, 9.10 Karmic Koala, 8.04 Hardy Heron, are available from a  Launchpad repo maintained by Nicola Ferralis
 [INDENT] [https://launchpad.net/~cinelerra-ppa](https://launchpad.net/~cinelerra-ppa) [/INDENT] To add the Cinelerra PPA to your source list follow the instructions on the [Launchpad page]("https://launchpad.net/%7Ecinelerra-ppa/+archive/ppa").
 Older packages are available too. See the [old packages]("http://cinelerra.org/old-distro.php") page.
  If you want to compile CinelerraCV from source you can find detailed instructions on the [Cinelerra for Grandma]("http://www.g-raffa.eu/Cinelerra/HOWTO/compilation.html") tutorial.
 [/INDENT]

I haven't check cinepaint yet.

---

### Post by abnordude on 2011-06-21
> **wep940 said:**
> I had more time here tonight to look at some stuff - the cinelerra website, on the download link, has instructions for setting up a ppa for ubuntu - if I remember correctly this will involve it showing you how to add a repository, if needed, and then you should be able to get/install it with the package manager.
**Ubuntu**
[INDENT] Latest Cinelerra CV 2.1.5 for 10.10 Maverick Meerkat, 10.04 Lucid  Lynx, 9.10 Karmic Koala, 8.04 Hardy Heron, are available from a  Launchpad repo maintained by Nicola Ferralis[INDENT] [https://launchpad.net/~cinelerra-ppa]("https://launchpad.net/%7Ecinelerra-ppa") [/INDENT]To add the Cinelerra PPA to your source list follow the instructions on the [Launchpad page]("https://launchpad.net/%7Ecinelerra-ppa/+archive/ppa").
 Older packages are available too. See the [old packages]("http://cinelerra.org/old-distro.php") page.
  If you want to compile CinelerraCV from source you can find detailed instructions on the [Cinelerra for Grandma]("http://www.g-raffa.eu/Cinelerra/HOWTO/compilation.html") tutorial.
 [/INDENT]I haven't check cinepaint yet.


Well. I got cinelerra. Thanks.
Now I only need to find cinepaint.

---

### Post by wep940 on 2011-06-24
I haven't forgotten you - I'm still looking for something for cinepaint.

---

### Post by wep940 on 2011-06-24
After much searching, it appears there is no release of cinepaint for ubuntu.  The threads in the forum, as well as threads on the net, indicate this is currently not installable.  The last supported package I saw mention of was for Ubuntu Dapper, an old old release of Ubuntu that isn't available or supported anymore.

---

### Post by abnordude on 2011-06-25
> **wep940 said:**
> After much searching, it appears there is no release of cinepaint for ubuntu.  The threads in the forum, as well as threads on the net, indicate this is currently not installable.  The last supported package I saw mention of was for Ubuntu Dapper, an old old release of Ubuntu that isn't available or supported anymore.

Well then its okay.
Cinerella is okay for me now.

Thanks for helping me.

---

