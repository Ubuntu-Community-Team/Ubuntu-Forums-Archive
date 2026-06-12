---
title: "ndiswrapper installation failures"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by acidandspatter on 2007-05-04
Hi there,

I'm a complete newbie. I've just installed Fiesty. I have a Belkin F5D7000 wireless card and I've done so research and all of the install articles say I've got to use ndiswrapper. However it keeps stumbling over the install.

I've followed this help guide [http://ubuntuforums.org/showthread.php?t=432179]("http://ubuntuforums.org/showthread.php?t=432179") after mucking it up the first time. However when it gets to  installing it I get error messages.

I've attached the console output from when I run the install command.

Can I have some help please?

Many thanks

---

### Post by cluster1 on 2007-05-04
i think i am actually currently having the same problem on my dell laptop when trying to get my wireless card to work... have yet to figure out how to fix the ndiswrapper installation

---

### Post by Sloddy Shipper on 2007-05-07
Hi, I notice the version of ndiswrapper you are using is 1.43. The version I used before writing the post you tried to follow was 1.42. The instructions I followed as to which directory you should be in when running 

~$ sudo make install

may not apply. (In fact I think install intructions on the sourceforge pages have changed on this point)

try running this command in the directory

/home/alexander/Desktop/ndiswrapper-1.43/driver

instead. Getting this card to work was my first encounter with linux too and the being in the correct directory for install issue was confusing. Check the sourceforge ndiswrapper install guide. 

Also use synaptic to make sure you have installed the build-essential package.

I definitely encountered a bunch of similar warnings and errors on at least one attempt before i got this going.  Hope this helps.

---

