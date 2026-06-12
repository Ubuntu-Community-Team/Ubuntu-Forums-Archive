---
title: "KDE not installed properly on ubuntu"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by vkbidve on 2011-05-18
Hi, I am new to ubuntu and installeddd it on my laptop. Then I installed KDE to it and set it as default desk environ. It is running very fine!

Then I installed ubuntu 10.04 LTS on my home PC and again installed KDE on it after updating everything to today's date. I set it as default desk environ. But seems that it didn't get installed properly. After logging in, the splash screen of KDE appears. First the hard disk icon appears and then abruptly it switches to login screen again. This keeps repeating. 

I tried re-installing KDE, but the problem persists.

Can anybody help?

---

### Post by vkbidve on 2011-05-19
No solution on planet earth????

:confused:

---

### Post by SeijiSensei on 2011-05-19
If you want a KDE desktop, you're much better off installing [Kubuntu]("http://releases.ubuntu.com/kubuntu/") rather than adding KDE on top of GNOME Ubuntu.

---

### Post by compmodder26 on 2011-05-19
> **vkbidve said:**
> Hi, I am new to ubuntu and installeddd it on my laptop. Then I installed KDE to it and set it as default desk environ. It is running very fine!

Then I installed ubuntu 10.04 LTS on my home PC and again installed KDE on it after updating everything to today's date. I set it as default desk environ. But seems that it didn't get installed properly. After logging in, the splash screen of KDE appears. First the hard disk icon appears and then abruptly it switches to login screen again. This keeps repeating. 

I tried re-installing KDE, but the problem persists.

Can anybody help?

Did you install "kubuntu-desktop"?

---

### Post by 1991sudarshan on 2011-05-19
Please read this post and you can find the solution for your problem!
[http://www.linuxquestions.org/questions/linux-newbie-8/kubuntu-gui-login-screen-reappears-875303/](http://www.linuxquestions.org/questions/linux-newbie-8/kubuntu-gui-login-screen-reappears-875303/)

---

### Post by 1991sudarshan on 2011-05-20
> **vkbidve said:**
> Hi, I am new to ubuntu and installeddd it on my laptop. Then I installed KDE to it and set it as default desk environ. It is running very fine!

Then I installed ubuntu 10.04 LTS on my home PC and again installed KDE on it after updating everything to today's date. I set it as default desk environ. But seems that it didn't get installed properly. After logging in, the splash screen of KDE appears. First the hard disk icon appears and then abruptly it switches to login screen again. This keeps repeating. 

I tried re-installing KDE, but the problem persists.

Can anybody help?


Paste this command in the terminal and post the output of it!

**cat /etc/kde4/kdm/kdmrc**

---

### Post by mastablasta on 2011-05-20
also you might want to try to install Kubuntu 10.10 and add the latest KDE (4.6.x) or 11.04 (which has the latest KDE version by default i believe). This is because plenty KDE problems and bugs were solved in later versions.

---

### Post by vkbidve on 2011-05-22
> **1991sudarshan said:**
> Please read this post and you can find the solution for your problem!
[http://www.linuxquestions.org/questions/linux-newbie-8/kubuntu-gui-login-screen-reappears-875303/](http://www.linuxquestions.org/questions/linux-newbie-8/kubuntu-gui-login-screen-reappears-875303/)
I tried the stuff given in post #38 of this discussion, but it didn't solve the problem.

---

### Post by vkbidve on 2011-05-22
Here is the output of the "cat ..../kdmrc" command. I have removed some verbose comments (like the big paragraph at the starting of it) as the attachement uploader didn't allow more than 19.5 kB to attach.

---

### Post by vkbidve on 2011-05-24
any reply ?????

---

### Post by mastablasta on 2011-05-24
10.04 has an older version of KDE which is not as stable as current ones.
 
since it's a fresh install it is better to use Kubuntu image and make a new install.

---

### Post by vkbidve on 2011-05-24
> **mastablasta said:**
> 10.04 has an older version of KDE which is not as stable as current ones.
 
since it's a fresh install it is better to use Kubuntu image and make a new install.
I updated ubuntu 10.04 kernel to latest one. Then i downloaded and installed KDE4. So that has to be latest one, isn't it? Another thing is, i installed the same version in the same way on my laptop, and that is working just fine!

I doubt strongly on my graphics accelerator of my desktop. It has on-board graphics accelerator and many application using graphics acceleration do not work on it, but they work on my laptop. This is my experience on windows. 

But again I thought that whatever the hardware is, the KDE software has to get configured automatically. So where is it failing?

Of course, kubuntu is an option, but i want to have gnome and kde both as desktop environments and i want to use any of them at will. That's why i am struggling for this.

---

### Post by mastablasta on 2011-05-24
> **vkbidve said:**
> I updated ubuntu 10.04 kernel to latest one. Then i downloaded and installed KDE4. So that has to be latest one, isn't it? Another thing is, i installed the same version in the same way on my laptop, and that is working just fine!

4.6.3 is the latest but 4.6.2 is also good. 4.5.5 no so good but still ok. it's also good to update not just kde but full kubuntu desktop.
 
> 
I doubt strongly on my graphics accelerator of my desktop. It has on-board graphics accelerator and many application using graphics acceleration do not work on it, but they work on my laptop. This is my experience on windows. 
 
But again I thought that whatever the hardware is, the KDE software has to get configured automatically. So where is it failing?

KDE Uses different programme to draw the environment. yes it could be graphics card. e.g. on my ATI card the splash screen doesn't even load unless i enter a few commands after install. what chip is it?
 
> 
Of course, kubuntu is an option, but i want to have gnome and kde both as desktop environments and i want to use any of them at will. That's why i am struggling for this.
 
Well you could try Kubuntu and then install Gnome (gnome-desktop or whatever it's called).
 
btw i see no reason in having so many desktop environments unless you are testing them out. they double all programmes (or use alternatives) but also double the various monitors (e.g network monitor) which take aditional ram. so you would have to uninstall a few of them to optimise the system.
 
EDIT: Also carefull with those kernel updates.

---

### Post by idoitprone on 2011-05-24
If you want an kde try a distro that distro that is better suited then ubuntu, vkbidve try opensuse with a kde spin. ubuntu tend to cast aside kde and cripple it. Sorry  ubuntu fans. Kubuntu sucks

---

### Post by compmodder26 on 2011-05-24
> **idoitprone said:**
> If you want an kde try a distro that distro that is better suited then ubuntu, vkbidve try opensuse with a kde spin. ubuntu tend to cast aside kde and cripple it. Sorry  ubuntu fans. Kubuntu sucks

Having not used OpenSuse before, can you explain to me how Kubuntu is crippled compared to it?

---

### Post by idoitprone on 2011-05-24
> **compmodder26 said:**
> Having not used OpenSuse before, can you explain to me how Kubuntu is crippled compared to it?

Where to start. where to start. Kde is not a simple desktop environment to integrate. It requires countless hours of work to polish it properly to ship it. The problem with Ubuntu, it seems that they dont devote enough resources to kubuntu; I heard there are only 1 full time employee and couple more part-timers. There are reports of random crashes with Kubuntu. On the other hand, distros such as Opensuse have devoted effort to release stable packages even though they did break somethings. 



[https://blueprints.launchpad.net/ubuntu/+spec/kde-borrow-more-code](https://blueprints.launchpad.net/ubuntu/+spec/kde-borrow-more-code)
[http://ubuntuforums.org/showthread.php?t=728306](http://ubuntuforums.org/showthread.php?t=728306)
Some of the reoccurring discussion about the problems with Kubuntu.

Please note: I dont hate Ubuntu, but when it comes to KDE. I will never touch Kubuntu as other distros does it better.

---

### Post by vkbidve on 2011-05-25
> **idoitprone said:**
> Where to start. where to start. Kde is not a simple desktop environment to integrate. It requires countless hours of work to polish it properly to ship it. The problem with Ubuntu, it seems that they dont devote enough resources to kubuntu; I heard there are only 1 full time employee and couple more part-timers. There are reports of random crashes with Kubuntu. On the other hand, distros such as Opensuse have devoted effort to release stable packages even though they did break somethings. 



[https://blueprints.launchpad.net/ubuntu/+spec/kde-borrow-more-code](https://blueprints.launchpad.net/ubuntu/+spec/kde-borrow-more-code)
[http://ubuntuforums.org/showthread.php?t=728306](http://ubuntuforums.org/showthread.php?t=728306)
Some of the reoccurring discussion about the problems with Kubuntu.

Please note: I dont hate Ubuntu, but when it comes to KDE. I will never touch Kubuntu as other distros does it better.

I saw the threads you suggested. They are from year 2008/2009. Since then KDE itself must have been progressed a lot. I don't think that 'one and the only' full time programmer was sitting idle through all these three years along with other part timers. And in case if KDE itself is unstable, then how come the OpenSuse people can deliver a stable package?

Anyways, it is not a 'KDE: good or bad' thread. It is a thread of a problem case, where KDE is giving problem on one PC, while on another one, it doesn't. If you can suggest ways to troubleshoot the hardware or the configuration settings, then it would be most helpful to me.

I have already posted the output of the **'****cat /etc/kde4/kdm/kdmrc'** command in post #9 which '1991sudarshan' guy suggested in post #6.

---

### Post by vkbidve on 2011-05-26
Any suggestion ????? :confused:

---

