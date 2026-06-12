---
title: "how to use wubi/ubuntu"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by utinker on 2009-08-15
I'm absolutely new to ubuntu (though I've seen and read bits and pieces of it) and would like to install it using wubi as it does not require partitioning. I have already installed an iso on a cd disk as well as a usb flash drive. 

I already have an iso and the wubi file on my computer, but would like to know how to go about it because I have already tried wubi twice without any success. I would appreciate someone giving me info on using wubi to install the iso as a folder in windows xp. Thanks.

---

### Post by jrothwell97 on 2009-08-15
Welcome to the Ubuntu forums!

Wubi is pretty simple once you get the hang of it: get the latest installer from [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php), download it, and run it. Once you've answered all the questions, Ubuntu will be downloaded and installed automatically.

If you'd like to burn an Ubuntu CD, you need the ISO image. Note that simply copying the .iso file to the CD won't work - you need to use software such as [ImgBurn](http://www.imgburn.com/) to burn the image (this is because a .iso file is a raw copy of everything that has to be burned to the CD, including information telling the computer how to boot from it). If you don't want to download or burn an ISO, you can order a free CD with [ShipIt.](http://shipit.ubuntu.com)

Good luck! :)

---

### Post by jmszr on 2009-08-15
utinker,

Before you install Wubi, be sure and defrag the Windows drive you're going to install Wubi on. Twice is better.

This may be of help: [http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi) .

---

### Post by utinker on 2009-08-16
Sorry I didn't explain myself clearly. I have already burned the iso file to a cd and it works.

What I'm trying to do with wubi has nothing to do with the ubuntu cd I made. The problem I'm having is that despite having the latest wubi, it didn't work. The reason I have the iso on my desktop is that I thought it would be easier for wubi to use it rather than download it from unbuntu (saves bandwidth).

From your replies  it sounds like wubi will download ubuntu anyway, it does not make use of the iso file on my computer. Am I making sense?

Correct me if I'm wrong. Thanks

---

### Post by nhasian on 2009-08-16
it is my understanding that if you have already burned ubuntu to a CD then you can just insert the cd while windows is running and install it from there with wubi.  

I know its a bit more work, but I always like to recommend installing ubuntu on its own partition or drive instead of using wubi.  it will be faster and you will have a much better ubuntu experience.

---

### Post by jmszr on 2009-08-16
utinker, 

You stated that the CD installation attempt did not work. Can you be more specific? Here are a couple of resources that are worth a look: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) .

Having the .iso file on you desktop will not affect your installation.

If you're having a problem with CD installation then (bandwidth permitting) go ahead and install Ubuntu using the installer as jrothwell97 suggests.

---

### Post by Harper45 on 2009-08-16
its great information thanks for sharing:popcorn:

---

### Post by utinker on 2009-08-18
Sorry for the confusing message - I have no problem with the cd. I have a problem using wubi to install ubuntu within windows. What I am trying to do is to use wubi to load my iso file into windows - from your posts it looks like wubi does not work that way. It seems wubi downloads and installs ubuntu itself (so there is no need for the iso file I have). Is this right?

---

