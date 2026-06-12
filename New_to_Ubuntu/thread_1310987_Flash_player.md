---
title: "Flash player"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by daniell59 on 2009-11-02
After finally solving a hardware issue I downloaded Ubuntu 9.10 64 bit.
Would someone direct me to the proper flash player and how to install it.

Thanks in advance.

---

### Post by philinux on 2009-11-02
> **daniell59 said:**
> After finally solving a hardware issue I downloaded Ubuntu 9.10 64 bit.
Would someone direct me to the proper flash player and how to install it.

Thanks in advance.

Hope this helps.
1. get the plug in from adobe. [http://get.adobe.com/flashplayer/tha...Linux_(.tar.gz](http://get.adobe.com/flashplayer/tha...Linux_(.tar.gz)) and save to Desktop.

2. Right click the archive and choose extract here.

3. copy the file libflashplayer.so to ~/.mozilla/plugins
You will have to first create the plugins folder.

4. restart firefox

---

### Post by karimruan on 2009-11-02
Make sure you have all of the updates. Last I knew, the 64 bit flash player was not completely finished, so it may work, may not.

---

### Post by philinux on 2009-11-02
> **karimruan said:**
> Make sure you have all of the updates. Last I knew, the 64 bit flash player was not completely finished, so it may work, may not.

It's the 32 bit version thats borked on a 64 bit install.

The 64 bit plugin is rock solid even though it is still an alpha refresh.

---

### Post by daniell59 on 2009-11-02
> **philinux said:**
> Hope this helps.
1. get the plug in from adobe. [http://get.adobe.com/flashplayer/tha...Linux_(.tar.gz](http://get.adobe.com/flashplayer/tha...Linux_(.tar.gz)) and save to Desktop.

2. Right click the archive and choose extract here.

3. copy the file libflashplayer.so to ~/.mozilla/plugins
You will have to first create the plugins folder.

4. restart firefox

I was able to get to step 2, then got lost.

---

### Post by philinux on 2009-11-02
Looks like the link was down or I got the cut and paste wrong.

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

---

### Post by daniell59 on 2009-11-02
> **daniell59 said:**
> I was able to get to step 2, then got lost.

I was able to extract files, but then got lost.

---

### Post by philinux on 2009-11-02
Ok no worries.

There's only one file, libflashplayer.so

Places>home folder
Press ctrl h to show hidden file. Browse into the .mozilla folder. Right click create folder plugins.

Copy the file into this new directory.
Copy and paste or drag and drop.

---

### Post by daniell59 on 2009-11-02
> **philinux said:**
> Ok no worries.

There's only one file, libflashplayer.so

Places>home folder
Press ctrl h to show hidden file. Browse into the .mozilla folder. Right click create folder plugins.

Copy the file into this new directory.
Copy and paste or drag and drop.

I do appreciate your effort but I am still lost.
I need a step by step breakdown. How do I get to plug in etc?

Thanks

---

### Post by philinux on 2009-11-02
If you browse to .mozilla and double click it you will be browsing inside that folder. Then right click in empty space or Click File create new folder and name it plugins.

---

### Post by sdpiowa on 2009-11-02
Look at this:
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

---

### Post by daniell59 on 2009-11-02
Could someone kindly explain to me how I can use the terminal to install the flashplayer. 

Thanks

---

