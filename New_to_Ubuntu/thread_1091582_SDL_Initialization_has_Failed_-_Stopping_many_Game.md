---
title: "SDL Initialization has Failed - Stopping many Games from Loading"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-03-09
I have a large number of games installed via the repositories on Ubuntu 8.10 how ever many of them throw an error similar to this upon trying to load them:

```
Error : SDL initialization failed
Reason : No available video device

```

I have a NVidia 9500M GS Graphics card and I am running the 180.xx drivers. Any one have ideas ideas how I can correct this error?

I found [this thread](http://www.linuxquestions.org/questions/debian-26/could-not-initialize-sdl-video-subsystem-572275/) which appears to be the same issue I am having... how ever I do not under stand the solution that was posted anyone mind explaining how I can apply this to Ubuntu 8.10

Thanks,
~Jeff

---

### Post by beastrace91 on 2009-03-17
Any one have even the slightest idea what I might be able to do to correct this? There does not seem to be an answer anywhere online. Searching for "SDL Configuration" yields pretty much all guides on how to write apps in SDL, I've posted on several message boards and no one has been able to help for almost a week now. Thinking formatting just to get a fresh install would be an option but I would really like to know how to correct the issues in case it happens again... Anyone?

Halp!
~Jeff

---

### Post by KIAaze on 2009-03-17
The first thing you could try is ask on the thread you linked too: [http://www.linuxquestions.org/questions/debian-26/could-not-initialize-sdl-video-subsystem-572275/](http://www.linuxquestions.org/questions/debian-26/could-not-initialize-sdl-video-subsystem-572275/)

From what I understood, there are 3 things you should try:

**1) Recompile SDL: 2 possibilities**
First install the necessary build dependencies:
```
sudo apt-get build-dep libsdl1.2debian
```

*1a) From the source tarball:*
Download SDL-1.2.13.tar.gz from here: [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)
```
tar -xzvf SDL-1.2.13.tar.gz
cd SDL-1.2.13/
./configure
make
sudo make install

```

*1b) From the source package in the repositories:*
```
apt-get source libsdl1.2debian
cd libsdl1.2-1.2.13/
debuild -us -uc
gksudo gdebi-gtk libsdl1.2debian-all_1.2.13-2ubuntu1_*.deb

```

**2) Try booting from an older kernel version (<=2.6.22 according to the thread, but try a bit more recent ones first maybe):**
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux+image](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux+image)

Install them through Synpatic when possible.
Otherwise, just download the .deb from the link above and install by double-clicking it.

Note: You can install as many kernel images as you want. It shouldn't conflict normally.
When you reboot, just choose the kernel version you want to boot.

**3) If none of the above worked, do #2 and then #1, i.e. recompile SDL while running an older kernel.**

**4) Other than that, well, you could try simply installing Ubuntu 8.04...**

_**Important:**_ I think you should report this as a bug on Launchpad too.
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

