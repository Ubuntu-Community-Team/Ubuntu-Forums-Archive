---
title: "installing tar.gz"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by slant6power on 2011-08-17
Dear Friends,
 I've waded through boatloads of posts on this and tried myriads of  things for this really basic thing.

I am just trying to update flash player.  I download the tar ball and attempt to install:

sudo apt-get install---

But it can never find the tar ball.  I try:

cd

But no file or directory found or E: Couldn't find package.

What am I doing wrong?

Thanks!

---

### Post by jerrrys on 2011-08-17
i don't understand why your doing this.  flash is part of the "ubuntu-restricted-extras" package; located in the software center.  but to answer your question

your downloaded tar file should be located in your home folder in "Downloads" and the short answer is just to double click on it and then extract.  the long (and better) answer is here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=tar.gz&sa=Search&cof=FORID:9#896](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=tar.gz&sa=Search&cof=FORID:9#896)

are you sure you need to do this?

---

### Post by Enigmapond on 2011-08-17
I don't understand either. If you want to update to the new version, make it so simple on yourself and install the Flash-Aid add-on to FireFox. Run the script and it will install the new version and uninstall what you don't need or what will conflict.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

It was developed by one of our members and works just great.

PS.. Welcome to the forum!..:))

---

### Post by garvinrick4 on 2011-08-17
[COLOR=Red]#Use the previous posts to install Flashplayer: [/COLOR]
This is just for uncompressing and installing from source in tarball. Just instructions for
you, nothing to do with Flashplayer. See below for explanation of tarball.
```


# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    ./configure will configure the software to ensure your system has the necessary functionality 
     and libraries to successfully compile the package
    make will compile all the source files into executable binaries.
    Finally, make install will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

Each tarball comes with installation and build instructions. Open INSTALL or README file for more information:
```When you uncompress a flash tarball will just come up with a:
[COLOR=Red]libflashplayer.so[/COLOR]
#In Ubuntu needs to be put in /usr/lib/mozilla/plugins
  ```
sudo cp [COLOR=Red]libflashplayer.so [/COLOR]/usr/lib/mozilla/plugins/ 

```##FLASH AID as a Firefox add-on will do this for you and much more. Removes old flashplayer, tweaks for you and is latest version out.
#Downloading from repository via Ubuntu software center, Synaptics and or terminal command will also do everything for you but does not remove old attempts to install and its remnants. 
#I am just explaining what is in the Adobe tarball and where it go's for information.
 ##[COLOR=Blue]tar.gz also known as tarball, an archive format for electronic data  and software. Most Linux tarball contains a source code for software. If  you are new to Linux I recommend using 
GUI to install. Tarballs are a group of files in one file. Tarball files have the  extension .tar.gz, .tgz or .tar.bz2. Most open source software use  tarballs to distribute programs/source codes.[/COLOR]
#I hope this helped you understand a little better.

---

### Post by seawolf167 on 2011-08-18
As previously mentioned, a perhaps better approach would be to install the restricted extras package and update that

```
sudo apt-get install ubuntu-restricted-extras
```

then update/upgrade as needed to update flash (and the rest of the system)

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 3rdalbum on 2011-08-18
> **slant6power said:**
> I download the tar ball and attempt to install:

sudo apt-get install---

But it can never find the tar ball.

That's not how apt-get works. Apt-get looks for software on online sources called repositories. It doesn't look for software that you've already downloaded through a web browser. That's not its job.

If you want to install software that you've downloaded from a random website, firstly, be careful that you trust the site you got it from! And secondly, **you must follow the instructions given with that software**. There's so many different ways in which third parties can package software for Linux, there is no one standard way that always works.

EDIT: In this particular case, though, the other posters are correct. Don't download Flash from the Adobe website and then manually copy it to the place it needs to go for all of your installed browsers. Just install it from the repositories (Ubuntu Software Center) or use FlashAid to help you install it.

---

### Post by beew on 2011-08-18
Best way to install flash in Ubuntu is to install the flash-aid addon for FireFox and then run the script. It clears up conflicting flash versions, update flash and optimizes it for the system. Also, flash installed with flash-aid is system wide so it is not just for FireFox.

---

### Post by slant6power on 2011-08-18
Dear Friends,
  Thank you all for posting!

It seems like a majority vote was to go with flash add-on, unfortunately:

Flash-Aid 2.1.1 could not be installed because it is not compatible with Firefox 3.0.16.


So I went to update Firefox and I seem to be hung up there also, see below.

Any ideas on getting firefox updated so that I can get flash updated?

Thanks again!


elizchapman@elizabeth-laptop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.0-branding firefox-3.0-gnome-support firefox-branding libnspr4-0d
  libnspr4-dev libnss3-1d libnss3-dev
Suggested packages:
  latex-xft-fonts
The following packages will be REMOVED:
  firefox-3.0
The following NEW packages will be installed:
  firefox-branding
The following packages will be upgraded:
  firefox firefox-3.0-branding firefox-3.0-gnome-support libnspr4-0d
  libnspr4-dev libnss3-1d libnss3-dev
7 upgraded, 1 newly installed, 1 to remove and 127 not upgraded.
Need to get 13.3MB of archives.
After this operation, 26.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firefox-3.0-branding firefox-3.0-gnome-support firefox firefox-branding
  libnspr4-dev libnspr4-0d libnss3-dev libnss3-1d
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main firefox-3.0-branding 3.6.11+build3+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.170 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main firefox-3.0-branding 3.6.11+build3+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main firefox-3.0-gnome-support 3.6.11+build3+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main firefox 3.6.11+build3+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main firefox-branding 3.6.11+build3+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnspr4-dev 4.8.6-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnspr4-0d 4.8.6-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnss3-dev 3.12.8-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnss3-1d 3.12.8-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_all.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_all.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_i386.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-branding_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-branding_3.6.11+build3+nobinonly-0ubuntu0.9.04.1_i386.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-dev_4.8.6-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-dev_4.8.6-0ubuntu0.9.04.1_i386.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.6-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.6-0ubuntu0.9.04.1_i386.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-dev_3.12.8-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-dev_3.12.8-0ubuntu0.9.04.1_i386.deb)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.8-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.8-0ubuntu0.9.04.1_i386.deb)  404 Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
elizchapman@elizabeth-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
elizchapman@elizabeth-laptop:~$ apt-get update firefox
E: The update command takes no arguments

---

### Post by oldos2er on 2011-08-18
Jaunty is no longer supported, you should upgrade to at least 10.04 or higher.

---

### Post by raja.genupula on 2011-08-18
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```

i had experience with this problem if you stopped any installation or any apt-get operation in middle by using ctrl+z , up to completion of that operation you've stopped ,you're going to get same messages . when ever that process will be completed , then only you can able to run another apt-get process  .

---

### Post by slant6power on 2011-08-18
Thanks again, folks!

However, arrrrr....

I go to update 9.04 to 10.04.03 with update manager and it says an upgrade from jaunty to lucid is not possible with that tool.

That's not so friendly...

Should I do a fresh install of 10.04.03 at this point?

Thanks!

---

### Post by wojox on 2011-08-18
> **slant6power said:**
> Thanks again, folks!

However, arrrrr....

I go to update 9.04 to 10.04.03 with update manager and it says an upgrade from jaunty to lucid is not possible with that tool.

That's not so friendly...

Should I do a fresh install of 10.04.03 at this point?

Thanks!

I'd do a fresh install if it's an option. Then you get ext4 and grub2 by default. :P

---

