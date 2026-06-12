---
title: "Please help with tarballs! I'm totally trying, REALLY!"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by garpt on 2009-01-03
Hi, all,
  Can someone tell me what I am doing wrong in the below tarball install try? I can get to the directory (folder) which contains the files. You can see i did the cd command. Then I try to configure it and get the error below. I am a real newbie and trying to learn all the terminal command stuff on my own. But with tarballs, I always get stuck here. By the way, the install text file in the program instructions says the shell commands ":o:o./configure, make, and make install" should work to configure, build, and install. The first thing I did was to open the containing folder from the package manager and put it in the usr folder in the home directory, then changed the directory in terminal to point to that very same folder. I hope this makes sense, I have no idea what I'm talking about:confused::o
Please talk in beginner-ease. I'm having a lot of fun, but these tarballs have me totally frustrated!:(  Terminal text follows::

garwyn@garwyn-laptop:~/src/gnome-color-chooser-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libgnome-2.0 >= 2.16.0  libgnomeui-2.0 >= 2.14.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

garwyn@garwyn-laptop:~/src/gnome-color-chooser-0.2.4$

---

### Post by evilkastel on 2009-01-03
See the "no package found" ? you need that packages in order the program to work. Find them and install them. At least that is what i would do.

---

### Post by zenmatrix on 2009-01-03
your missing dependencies(programs need by the program your installing) from what I can see. most of those your should be able to do apt-get install <package>

---

### Post by caljohnsmith on 2009-01-03
Have you tried installing gnome-color-chooser through the repositories? I believe it is available, so is there any special reason why you want to compile it yourself? In other words, have you tried:
```
sudo apt-get install gnome-color-chooser
```

---

### Post by jerome1232 on 2009-01-03
You will probably need the development verisions of those packages, they just have a -dev at the end of the name, search synaptic for those and look for their development verssions. Isn't there a readme or install file that tells you what the programs dependencies are.

---

### Post by Coder543 on 2009-01-03
> **zenmatrix said:**
> your missing dependencies(programs need by the program your installing) from what I can see. most of those your should be able to do apt-get install <package>
**sudo** apt-get install <package>

---

### Post by steveneddy on 2009-01-03
> **caljohnsmith said:**
> Have you tried installing gnome-color-chooser through the repositories? I believe it is available, so is there any special reason why you want to compile it yourself? In other words, have you tried:
```
sudo apt-get install gnome-color-chooser
```

Totally agreed.

Always check Synaptic before trying to compile it yourself.

---

### Post by garpt on 2009-01-04
Thank you all,
 And caljohnsmith, you definitely solved the immediate problem. I thought I had already tried that, I read others who said the program "mysteriously" disappeared from that function. But i must have typed it wrong; I did a copy and paste from your command and it worked. Thank You. I still need to figure out tarballs for the future, and I thank everyone else for the probable need for additional dependicies. I will work on that in the AM. But immediate prob solved. Thanks to everyone!.
GT:o

---

### Post by sadaruwan12 on 2009-01-04
> **garpt said:**
> Thank you all,
 And caljohnsmith, you definitely solved the immediate problem. I thought I had already tried that, I read others who said the program "mysteriously" disappeared from that function. But i must have typed it wrong; I did a copy and paste from your command and it worked. Thank You. I still need to figure out tarballs for the future, and I thank everyone else for the probable need for additional dependicies. I will work on that in the AM. But immediate prob solved. Thanks to everyone!.
GT:o
Yo Bro befor trying tarballs check with the repos first then if it's ther then try to install it from that using

sudo apt-get install <package_name>

If it's not there then go for the tarball but the problem is that when you try to install with the tarball you need to get all the dependencies maunally so try to check with the repos first.

---

### Post by bonzini on 2009-01-04
> **garpt said:**
> Hi, all,
  Can someone tell me what I am doing wrong in the below tarball install try?

One really useful thing in general is the "build-dep" option to apt-get.  It instructs apt-get to go look for all the dependencies related to the package you are trying to build.

Get a terminal window.  Type "man apt-get".  Then read the doc looking for "build-dep".

---

### Post by garpt on 2009-01-04
Thanks, sadaruwan12, I think I'm getting the idea- so those needed dependencies will vary from package to package, and if I need to use the tarball, I will probably have to do that each time, correct? So those aren't files that are just "missing" from my computer and universal to installing tarballs. So, I need to hope that I can find the app in a repository to avoid the extra work. thanks. gt

---

### Post by oldos2er on 2009-01-04
> **garpt said:**
> Thanks, sadaruwan12, I think I'm getting the idea- so those needed dependencies will vary from package to package, and if I need to use the tarball, I will probably have to do that each time, correct? So those aren't files that are just "missing" from my computer and universal to installing tarballs. So, I need to hope that I can find the app in a repository to avoid the extra work. thanks. gt

 Nine times out of ten there is documentation either bundled in the tarball (README and/or INSTALL, or 'docs' directory) that lists any dependencies needed. Sometimes this info is on the website you downloaded the tarball from. Rarely you need to go googling for it.

---

### Post by steveneddy on 2009-01-04
> **oldos2er said:**
> Nine times out of ten there is documentation either bundled in the tarball (README and/or INSTALL, or 'docs' directory) that lists any dependencies needed. Sometimes this info is on the website you downloaded the tarball from. Rarely you need to go googling for it.

Very true. Most of the time there is a version of the dependency file in the repos that will work for you easily.

---

