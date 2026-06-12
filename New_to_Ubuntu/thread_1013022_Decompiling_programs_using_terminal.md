---
title: "Decompiling programs using terminal"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by beeping_rugs on 2008-12-16
Hi everyone, I am an absolutely new beginner. Running dual boot Windows XP and Ubuntu 8.10 although I have not been in to Windows for a month or so now. Absolutely loving Ubuntu.
Problem:  Although I've made use of Synaptic Package Manager for a variety of software downloads, I am trying to extract and compile a program using the terminal. I have attempted to open a package called klog-0.4.5 and, after entering  

tar -zxvf klog-0.4.5.tar.gz the package has decompiled so far and then I get this:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
will@ubuntu:~/Desktop/klog-0.4.5$ 

Can someone explain this to me as I am struggling.

Similarly, tried to TAR,  ./configure and MAKE the following open src package and have been getting the following:

will@ubuntu:~/Desktop/LinLog$ make
make: *** No targets specified and no makefile found. Stop.
will@ubuntu:~/Desktop/LinLog$ 

Not sure what to make (excuse the pun) of this

I apologise in advance for my ignorance as I think you probably need more information.  I guess I need to spend a lot of time doing background reading on installation of these open source  packages rather than rely on Synaptic Package Manager and what it has to offer.  I want to use and master the terminal method as its much more interesting than having Synaptic do it for me.  

Any assistance would be appreciated...............:confused:

---

### Post by Ericthegreat on 2008-12-16
Have you tryed installing the kde headers?

---

### Post by Tatty on 2008-12-16
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) have a read of this.

---

### Post by oldos2er on 2008-12-16
You first need to install the package "build-essential". Then look for a README and/or INSTALL file that tells you the dependencies needed to compile the source.

---

### Post by donkyhotay on 2008-12-16
For this specific error make certain you have build-essential and kde headers. Usually most errors similar to this are a missing library. If you get a problem like this go into synaptic and do a search for the -dev version of whatever is reported missing and then install that.

---

### Post by snova on 2008-12-16
When I first found this thread, I wondered *what on earth* you were doing! ;) Decompiling is an entirely different process than what this is.

You're well on your way to a successful compilation, but you have to install a few other packages first: 'build-essential' and 'kdelibs4-dev'. If it still fails, try installing 'kdelibs5-dev' instead, but it doesn't appear so.

> 
will@ubuntu:~/Desktop/LinLog$ make
make: *** No targets specified and no makefile found. Stop.
will@ubuntu:~/Desktop/LinLog$


You will get that until configure manages to finish successfully. It didn't.

---

### Post by Paqman on 2008-12-16
Klog 0.4.3 is available from the universe repo. Unless there's a really, really good reason you need the 0.4.5 release, i'd advise sticking to the one in the repos.

---

### Post by snova on 2008-12-16
> **Paqman said:**
> Klog 0.4.3 is available from the universe repo. Unless there's a really, really good reason you need the 0.4.5 release, i'd advise sticking to the one in the repos.

Ah. I searched for to make sure it wasn't already, but I missed it.

Agreed, it's much easier to stick with the repos. Such a minor change in version number won't be a big difference, either.

---

### Post by beeping_rugs on 2008-12-16
"fan jammy dozey" ......excellent responses. Thank you so much. I will, come sun up, look to install the various packages that each of you have kindly referred me to. Let you know how I get on. Good evening/morning from sunless Glasgow !! :lolflag:

---

### Post by beeping_rugs on 2008-12-17
Hi everyone,
I did as suggested and downloaded the outstanding items.
Tried the same process again TAR -ZXVF <PROGRAM), CD .....<program file name>,  ./configure, MAKE; even tried SUDO MAKE INSTALL and.....same issues. Interestingly, What I then did was to carry out the same process and downloaded GFTP and that program installed without a problem ?? So, I wonder if it is an issue with the open src programmes that I've downloaded ??  Seems a little strange that two of these packages, <LinLog-0.4.tar.gz> & klog-0.4.5$ are producing the same sort of responses ??  Any thoughts as I now know that GFTP has gone through the process okay and the onboard packages I now have installed for my ver. of Ubuntu 8.10 is good

---

### Post by beeping_rugs on 2008-12-17
Hi everyone,
well this is really odd.  I went to Universe repo and downloaded Klog 0.4.3 and it compiled perfectly. No issues whatsoever. This reinforces my thinking that there may be something in the src code for later versions which causes conflict ?  Another anomaly;  the reason I wanted to download Klog 0.4.3 was to give myself the amateur radio logging system however; what I appear to have ended up with is anything but that and there are number of new features in my application folder such as Kalarm, Kcalc, K this n K that so I am just wondering what happened to the Amateur Radio logging program Klog ????

---

### Post by snova on 2008-12-17
Ah, yes... oh dear.

Klog is a KDE program, meaning its part of the KDE project, similar in intent to Gnome. Unfortunately by installing it you also pulled in a lot of KDE, which explains these new programs.

Secondly, when you install from the repos, it doesn't compile anything- it's already been done.

---

### Post by beeping_rugs on 2008-12-20
Thanks to everyone for their kind endeavours............see you around the linux corridors from time to time  I hope......kind regards  Will

---

