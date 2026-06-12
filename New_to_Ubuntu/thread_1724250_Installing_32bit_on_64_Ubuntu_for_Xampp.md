---
title: "Installing 32bit on 64 Ubuntu for Xampp"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Vallar on 2011-04-08
Greetings everyone, how are you all doing? 
 
Recently I decided to install Ubuntu and it was aa a great decision, mind you. I installed the Ubuntu 10.10 AMD64 version. It works fine and I didn't run into any problems what so ever. 
However, I was learning PHP and wanted to install Xampp. As you know, there is no 64 but verion of Xampp (or so I read around the internet). So after I installed Xampp not knowing this little information, I searcehd around; one guide adviced to install Xampp and then install the ia32-lib (I think is the name) to enable 32bit support in AMD64. 
 
I installed Xampp and it installed fine, however when I start Xampp it doesn't work. So I tried to install the ia32-lib files. Since I don't have a direct internet connection to my computer, I have to download the .deb files manually. I have downloaded these so far:
 
lib32gcc1_4.0.3-1ubuntu5_amd64.deb
lib32stdc++6_4.0.3-1ubuntu5_amd64.deb
lib32z1_1.2.3-6ubuntu4_amd64.deb
libc6_2.3.6-0ubuntu20.6_amd64.deb
libc6-i386_2.3.6-0ubuntu20.6_amd64.deb
lsb-release_3.1-5ubuntu2_all.deb
 
Some of these I try to run but a message in the update manager says that I have a newer version and when I try to install the next file, it says it requires a version of the previous one (which when I compare the version numbers I find I have a new version of the said required one -- for example if I require lib32gcc1 v.3 I have v.4 installed but when I try to install say lib32stdc it says it needs lib32gcc1 v.2+ and won't install)
 
 
 
How do I go around this? Anyway I would know what kind of files required to install a certain library and download them all from one place instead of navigating through tons of repository links to get each file alone?

---

### Post by andrewthomas on 2011-04-08
You just need to read through:

[http://packages.ubuntu.com/maverick/ia32-libs](http://packages.ubuntu.com/maverick/ia32-libs)

and satisfy all the dependencies.

You actually have some of the wrong versions.  

Put all the below files in a directory and install them all at once.  

I just would just use dpkg to install the files, but you probably could select them all and right-click on them and use gdebi to install.

[http://mirror.pnl.gov/ubuntu//pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu9_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu9_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.12.1-0ubuntu10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.12.1-0ubuntu10.1_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu10.1_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.12.1-0ubuntu10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.12.1-0ubuntu10.1_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/g/gcc-4.5/gcc-4.5-base_4.5.1-7ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/g/gcc-4.5/gcc-4.5-base_4.5.1-7ubuntu2_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/a/alsa-lib/lib32asound2_1.0.23-1ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/a/alsa-lib/lib32asound2_1.0.23-1ubuntu2_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/a/alsa-lib/libasound2_1.0.23-1ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/a/alsa-lib/libasound2_1.0.23-1ubuntu2_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/b/bzip2/lib32bz2-1.0_1.0.5-4ubuntu1_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/b/bzip2/lib32bz2-1.0_1.0.5-4ubuntu1_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/g/gcc-4.5/lib32gcc1_4.5.1-7ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/g/gcc-4.5/lib32gcc1_4.5.1-7ubuntu2_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/n/ncurses/lib32ncurses5_5.7+20100626-0ubuntu1_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/n/ncurses/lib32ncurses5_5.7+20100626-0ubuntu1_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/g/gcc-4.5/lib32stdc++6_4.5.1-7ubuntu2_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/g/gcc-4.5/lib32stdc++6_4.5.1-7ubuntu2_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/libv/libv4l/lib32v4l-0_0.6.4-1ubuntu1_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/libv/libv4l/lib32v4l-0_0.6.4-1ubuntu1_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/libv/libv4l/libv4l-0_0.6.4-1ubuntu1_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/libv/libv4l/libv4l-0_0.6.4-1ubuntu1_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/z/zlib/lib32z1_1.2.3.4.dfsg-3ubuntu1_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/z/zlib/lib32z1_1.2.3.4.dfsg-3ubuntu1_amd64.deb)
[http://mirror.pnl.gov/ubuntu//pool/main/l/lsb/lsb-release_4.0-0ubuntu8_all.deb](http://mirror.pnl.gov/ubuntu//pool/main/l/lsb/lsb-release_4.0-0ubuntu8_all.deb)

---

### Post by CharlesA on 2011-04-08
Why not just install the normal lamp stack?

```
sudo tasksel install lamp-server
```

You can always add python or perl afterwords.

---

### Post by Vallar on 2011-04-08
Hello! 

Well, I tried the command however the terminal produced this error:
sudo: tasksel: command not found.

On the other hand, I downloaded all the files, I even downloaded all  stuff for gdebi but it is not installing using the Ubuntu Software  Center. It however worked with dpkg; all of them worked with dpkg.  Though it was pretty tedious to install through the command line, one by  one typing the weird file names. 

Anyway, thank you very very very MUCH! I finally was able to get Xampp running :D. Thank you so very much!

---

### Post by CharlesA on 2011-04-08
Ah. I guess tasksel isn't installed by default in maverick.

---

### Post by andrewthomas on 2011-04-08
> **Vallar said:**
> Hello! 

Well, I tried the command however the terminal produced this error:
sudo: tasksel: command not found.

On the other hand, I downloaded all the files, I even downloaded all  stuff for gdebi but it is not installing using the Ubuntu Software  Center. It however worked with dpkg; all of them worked with dpkg.  Though it was pretty tedious to install through the command line, one by  one typing the weird file names. 

Anyway, thank you very very very MUCH! I finally was able to get Xampp running :D. Thank you so very much!
All you really have to do is go to the directory where all the files are and type in enough of the name to be unique, then use the [Tab] key to complete the entry, adding all the files to one command.  

I'm not sure but you may have been able to just use *

```
sudo dpkg -i ./*
```

---

### Post by CharlesA on 2011-04-08
Yep, you can use *.

```
sudo dpkg -i *
```

Don't need the ./

---

### Post by Vallar on 2011-04-08
Wooohaa!!! O.O I certainly didn't know "TAB" completes file names nor did i know about that command either. The little tutorial I followed on the internet mentioned only the -i and the -R. 

It said -R was to install everything in a certain folder; it turns out it removed everything. I didn't even know you can type in multiple files and it does it automatically.

Sorry for being so noob! Though to be honest, thank you so much now you are going to save me hours when I install anything with so much files :D

---

### Post by andrewthomas on 2011-04-09
> **CharlesA said:**
> Don't need the ./
Yeah, I don't know what I was thinking.  It's not like it was a script.

---

