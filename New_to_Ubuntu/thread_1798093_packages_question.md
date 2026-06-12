---
title: "packages question"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by maximo360 on 2011-07-05
when installing needed packages for compiling using the apt-get install command, are the packages installed permanently or do i have to reinstall them everytime i need them?

---

### Post by Frogs Hair on 2011-07-05
The packages remain installed unless they are setup files of some kind .

---

### Post by jtarin on 2011-07-05
> **maximo360 said:**
> when installing needed packages for compiling using the apt-get install command, are the packages installed permanently or do i have to reinstall them everytime i need them?Using the "apt-get install command" installs them as long as you want them. Compiling is different. It is downloading the "source" package and compiling for your architecture and then installing.I would suggest you only download and install packages using "apt" or some form of it and not compiling anything until you learn more about Linux.

---

### Post by phaditama on 2011-07-05
I agree with jtarin. compiling is nasty :). believe in the repository. it is the safest place to get your software until you are comfortable enough with make and gcc. it is updated regularly and whatever in it has been rigorously tested.

---

### Post by maximo360 on 2011-07-05
> **jtarin said:**
> Using the "apt-get install command" installs them as long as you want them. Compiling is different. It is downloading the "source" package and compiling for your architecture and then installing.I would suggest you only download and install packages using "apt" or some form of it and not compiling anything until you learn more about Linux.
heres the packages they were requiring me to install;> [SIZE=+2]Developers Building Guide:[/SIZE]

The following is based off [CyanogenMod]("http://wiki.cyanogenmod.com/index.php?title=Compile_CyanogenMod_for_Dream_%26_Sapphire") wiki and explains how to build on:
Ubuntu 10.04 (Lucid) & Ubuntu 10.10a3 (Meerkat) and ideally a AMD64 compatible computer

I personally (mostly following the same instructions) use Debian squeeze and others have succeeded with 32bit systems. 

**Computer Setup** (only if you have not made an android build environment before):

1) It is not 100% needed but highly recommended to install [the Android SDK]("http://wiki.cyanogenmod.com/index.php?title=Howto:_Install_the_Android_SDK")
2) Install the packages required for the build 
[INDENT] 	 		** 			Originally Posted by [B]cmwiki** 		[/B] 	 	Install using the package manager of your choice:

For 32-bit & 64-bit systems:

    git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev  libwxgtk2.6-dev squashfs-tools build-essential zip curl libncurses5-dev  zlib1g-dev sun-java6-jdk pngcrush 

For 64-bit only systems:

    g++-multilib lib32z1-dev lib32ncurses5-dev lib32readline5-dev gcc-4.3-multilib g++-4.3-multilib 
NOTE: gcc-4.3-multilib g++-4.3-multilib is no longer available for  Ubuntu 11.04 64-bit, but should still build without issue. (with the  current version of gcc/g++ installed)

Note: On Ubuntu 10.10, and variants, you need to enable the parter repository to install sun-java6-jdk:

    add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner" 
 [/INDENT]

so i just install these packages using the sudo apt command?

---

### Post by jtarin on 2011-07-05
NO.....what is the software you are wanting to install?

---

### Post by maximo360 on 2011-07-05
> **jtarin said:**
> NO.....what is the software you are wanting to install?
this is what i am trying to do:[http://forum.xda-developers.com/showthread.php?t=882356](http://forum.xda-developers.com/showthread.php?t=882356)

---

### Post by jtarin on 2011-07-05
> For 32-bit & 64-bit systems:

git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk2.6-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev sun-java6-jdk pngcrush

For 64-bit only systems:

g++-multilib lib32z1-dev lib32ncurses5-dev lib32readline5-dev gcc-4.3-multilib g++-4.3-multilib
NOTE: gcc-4.3-multilib g++-4.3-multilib is no longer available for Ubuntu 11.04 64-bit, but should still build without issue. (with the current version of gcc/g++ installed)These you will have to install with "apt" or you can search in Synaptic Package Manager, but let me warn you you will start having problems installing some of these due to dependencies or different versions than what is available for your version if Ubuntu. However most of these are "build tools" for compiling so newer versions should not hurt. When you have problems with this do not come back to the "Beginners" forum. Post in a more appropriate forum in the "Main Support" category.

---

### Post by jtarin on 2011-07-05
You might consider setting up VirtualBox for doing this so if you hose something.....your real install stays safe.

---

### Post by maximo360 on 2011-07-05
ok gotchta, and what does the apt command do? just install them temporarily?

---

### Post by jtarin on 2011-07-06
> **maximo360 said:**
> ok gotchta, and what does the apt command do? just install them temporarily?As I said before...."Using the "apt-get install command" installs them as long as you want them". I hesitate to use the word permanently in this ever changing world of ours.:p
If you decide to use VirtualBox and install in that environment they will not be installed in your "real" environment. "What happens in Vegas stays in Vegas".:p
You want to know more about apt ....in a terminal type ```
man apt
```.

---

### Post by wildmanne39 on 2011-07-06
Hi, +1 for virtualbox, I use it to test  with if I have any doubt that I might break something.

---

