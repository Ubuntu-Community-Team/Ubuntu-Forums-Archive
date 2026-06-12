---
title: "Installing games from live DVD without installing the distro along with them"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Loodmasjien on 2009-08-28
Dear sirs

Being a Linux newbie, I would like to know how to go about installing / copying games (eg. Alien Arena) and applications (eg. GnuCash) from a Live DVD to your current Ubuntu / Linux installation.

I currently have Ubuntu 9 installed. I have recently received the Ubuntu (8.xx) Ultimate Gamers Edition Live DVD and am amazed by the applications and games shipping with it.

My first action was to install Ubuntu (8.xx) Ultimate Gamers Edition to disk, thus replacing Ubuntu 9.

However, I have found that, in my case, the built-in hardware support on Ubuntu 9 is quite better than that of version 8.  

I would therefore like to keep Ubuntu 9 installed to disk, but somehow transfer the games and applications from the Ultimate Gamers Edition DVD to Ubuntu 9 on my harddrive. 

I have browsed the Live DVD for the packages which might contain the games (eg. Alien Arena), but could not find anything useful (it does not seem as if standalone packages are used).

Couldn't you somehow configure the synaptic package manager to look for setup files on the live DVD, instead of an online location?

Kind regards

Lodewyk

---

### Post by MelDJ on 2009-08-28
to add alien arena go to add/remove. its under games, just tick to install it

---

### Post by zeroseven0183 on 2009-08-28
To install GNUCash, open a Terminal and type 

```
sudo apt-get install gnucash
```

---

### Post by zeroseven0183 on 2009-08-28
You can also install **GNUCash** in Add/Remove. Just search for it, check the item and click **Apply Changes**. Be sure that **All available applications** is shown.

I also like this application.

---

### Post by Paqman on 2009-08-28
You should be able to use the LiveDVD as if it were a repo. Just put it in the drive while running Ubuntu, you should get a message acknowledging that you've inserted a disk containing packages. After that you should be able to use Synaptic to install any packages that are on the disk that aren't in the normal repos.

I'd check the repos first though, as you'll probably get a newer version from the 9.04 repos than you would from an 8.10 DVD.

---

### Post by Loodmasjien on 2009-08-31
> **Paqman said:**
> You should be able to use the LiveDVD as if it were a repo. Just put it in the drive while running Ubuntu, you should get a message acknowledging that you've inserted a disk containing packages. After that you should be able to use Synaptic to install any packages that are on the disk that aren't in the normal repos.

I'd check the repos first though, as you'll probably get a newer version from the 9.04 repos than you would from an 8.10 DVD.

Hi Paqman,

Synaptic does detect packages on the live DVD, but only standard packages (.deb, .tar, etc.).  I've browsed the live DVD again and found that most of the disc space is concentrated in a single file, "Filesystem.squashfs".

It must be the image file from where the live distro is mounted and must therefore contain all of the games and applications.

Just for interest's sake, I would like to ask the following:

If I booted from the live DVD, could the physical files of say, Alien Arena, be copied from the virtual file system to the Ubuntu 9 one on my harddrive?  I know that the executable file would be found at "/usr/games", but where would the rest of the data be (almost 600 MB) ?

I know that this sounds elaborate and that downloading the games would be far easier, but it would be very nice to know.

Regards

Lodewyk

---

### Post by mike555 on 2009-08-31
You'll find all of your .deb's in /var/cache apt/archives/

---

