---
title: "Build Essential install  from only cd-rom."
date: 2009-08-25
forum: New to Ubuntu
---

### Post by newport_j on 2009-08-25
Since we must add 

apt-get install buld-essential
 
After Ubuntu 8.04.2 installation. Because build-essential is not installed automatically in Ubuntu 8.04. How do we install from the cd-rom only - no internet used at all? 

It seems that this can be done because the cd-rom that is the installation disk must have build-essential on it.

So install build-essential with only cd-rom. How do I do it.

Newport-j

---

### Post by mgranet on 2009-08-25
In Synaptic, go to Settings-->Repositories. Now, click the tab that says 'Third Party Software'. Select the checkbox next to the bit that says CDROM:[Ubuntu......] Click close, then click the Reload button.

I noticed a typo in your code. It should read ```
sudo apt-get install build-essential
```.

---

### Post by newport_j on 2009-08-25
Okay, but how I install build-essential only from the cd-rom. If I am somewhere with no internet connection. I have my original Ubunu 8.0.4.2 LTS install disk and nothing more. I assume that build-essential is on that disk.

Newport_j

---

### Post by mgranet on 2009-08-25
If you followed the steps I showed you, you will simply have to enter a terminal and paste the code I provided. Ubuntu can use a CD-rom as a repository, so you will just be 'downloading' the package from the CD instead of the internet. If you typed in that code and got some sort of error, please post it here so we can help you track down the problem.

You should also be able to download the .debs that make up the build-essential metapackage and burn them to a cd. These can then be transferred to your Linux install and installed manually by clicking on them. You can find the metapackage and all dependencies at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by mcduck on 2009-08-25
> **newport_j said:**
> Okay, but how I install build-essential only from the cd-rom. If I am somewhere with no internet connection. I have my original Ubunu 8.0.4.2 LTS install disk and nothing more. I assume that build-essential is on that disk.

Newport_j

Please, if you want people to help you stick to one thread instead of discussing the same things in multiple threads.

People helping here are all using their own free time to do so, and helping a person in one thread while somebody else gives the same answers in another one is simply wasting those people's time while they could be using it to help somebody else.. :)

(besides, the form rules forbid double posting..)

---

