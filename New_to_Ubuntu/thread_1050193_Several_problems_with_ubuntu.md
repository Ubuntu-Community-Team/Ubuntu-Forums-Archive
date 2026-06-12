---
title: "Several problems with ubuntu"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by cjc0013 on 2009-01-25
I am not sure where I should post this. I guess here... anyways my first problem is that I can't get any new updates. I have tried using Synaptic. What happens is it will start downloading, it gets to 66/68 and then stops. 
below is the error message
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.
my second problem is i cant use my graphics card
(not sure how to post a picture on this forum)
[http://img142.imageshack.us/my.php?image=screenshotzu0.png](http://img142.imageshack.us/my.php?image=screenshotzu0.png)
my third problem is firefox. It randomly closes with no error message.


any help would be greatly appreciated. sorry if I posted in wrong spot.

---

### Post by eragon100 on 2009-01-25
> **cjc0013 said:**
> I am not sure where I should post this. I guess here... anyways my first problem is that I can't get any new updates. I have tried using Synaptic. What happens is it will start downloading, it gets to 66/68 and then stops. 
below is the error message
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.
my second problem is i cant use my graphics card
(not sure how to post a picture on this forum)
[http://img142.imageshack.us/my.php?image=screenshotzu0.png](http://img142.imageshack.us/my.php?image=screenshotzu0.png)
my third problem is firefox. It randomly closes with no error message.


any help would be greatly appreciated. sorry if I posted in wrong spot.

For the video card issue, simple put a mark in the box in front of "nvidia drivers", click apply and restart the computer. That's it.

For firefox, I had that problem too. It's simply not very stable, I recommend you switch to opera. It's free, faster, has much more functions, looks nicer, and is a 1000 times more stable. It also uses less memory.

For the first problem, I would first like to know which version of ubuntu you are using? The output you posted looks like you are (still) using dapper, 6.06, which is 2.5 years old. I recommend you switch to the latest ubuntu release, intrepid ibex 8.10. As to your problem, it looks as tough one of the update repos you have configured your system to use is down, simply wait 'till it comes back up again :wink:.

---

### Post by cjc0013 on 2009-01-25
> **eragon100 said:**
> For the video card issue, simple put a mark in the box in front of "nvidia drivers", click apply and restart the computer. That's it.

For firefox, I had that problem too. It's simply not very stable, I recommend you switch to opera. It's free, faster, has much more functions, looks nicer, and is a 1000 times more stable. It also uses less memory.

For the first problem, I would first like to know which version of ubuntu you are using? The output you posted looks like you are (still) using dapper, 6.06, which is 2.5 years old. I recommend you switch to the latest ubuntu release, intrepid ibex 8.10. As to your problem, it looks as tough one of the update repos you have configured your system to use is down, simply wait 'till it comes back up again :wink:.

I am not sure what version but I did try to check the box and It won't let me check it...

---

### Post by eragon100 on 2009-01-25
> **cjc0013 said:**
> I am not sure what version but I did try to check the box and It won't let me check it...

then go to [www.nvidia.com](www.nvidia.com) and install the driver manually following the instructions there. You might need to use one of the driver for older cards, be sure to select the right kind of video card you have in the "video drivers" menu.

---

