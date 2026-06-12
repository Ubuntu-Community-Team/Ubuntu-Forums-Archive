---
title: "Newbie Guide for installing/upgrading Calibre?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Eve23 on 2009-09-19
[FONT=Arial, Helvetica, sans-serif][SIZE=2]Hi Everyone!
 
 I am new and excited to be using Ubuntu and signed up on this forum! :)
 
 I wanted to know if there is a Step-by-Step user Guide for Newbies on installing and upgrading Calibre.

I tried it on my own.  I first installed it from the Synaptic Package Manager but it was an older version. I tried to upgrade. After doing web and forum searches, I managed to make half my files disappear causing me to reinstall Ubuntu and the older version of Calibre. :(

After seeing many problems newbies seem to have are similar to my own, I though if there was a simple list of instructions, it might help us in this and also to learn a bit more about working with Ubuntu.

One problem for me is installing the dependencies. I tried but a sudo aptitude search (filename) or using the Package Manager but often it comes up with a long list of similar names but not exactly the name listed on the Calibre site, so I am unsure which item I really need to install. :confused:

Another problem was trying to install podofo and finding I had to install cmake to compile it. Again the problem with figuring out the dependencies and I was also unsure if I needed some of the optional ones, such as LUA.:confused:

I would appreciate any help and I am sure others would too.:)

Thanks so much in advance!! [/SIZE][/FONT]

---

### Post by tomBorgia on 2009-09-30
Hiya,

Are you talking about 
[this???]("http://calibre.kovidgoyal.net/download_linux") 

Maybe a silly question but is it absolutely necessary to have the latest version - The version from the package manager will update when a later version is released to the channel and it'll probably be better tested (with ubuntu)!

So I'm assuming you've tried the installer from the Calibre website and it's running into dependency problems? They can either be quite trivial to fix (i.e. you just need to install one or two other things) or a nightmare of needing one thing to install another and then another thing to install that and then that needs to be a different version...  

So if you can, install from the package manager / aptitude if not then post some details of what happens when you try and install and someone may know how to help!

---

### Post by gspawn69 on 2010-03-13
I would like to know how to update this program as well. The version in the repos for jaunty is 0.4.143 and the latest version is 0.6.17, according to Calibre. 

It appears newer versions are in the repos for karmic and lucid, so apparently no one has felt the need to update the repos for jaunty. However, according to the oswatershed link ([http://oswatershed.org/pkg/calibre]("http://oswatershed.org/pkg/calibre")) on the Calibre download page, there's a newer version (0.6.47) available in the future branch, but I don't know how to access that. Any help would be greatly appreciated. Thanks!

---

### Post by radu_radu on 2010-03-16
I've used the binary install command listed [_[COLOR="Navy"]here[/COLOR]_]("http://calibre-ebook.com/download_linux"), but it gave me version 0.6.41. Then I got from [_[COLOR="Navy"]sourceforge[/COLOR]_ ]("http://sourceforge.net/projects/calibre/files/0.6.45/calibre-0.6.45-x86_64.tar.bz2/download") version 0.6.45 and overwrite my calibre install in /opt
It still shows 0.6.41!:p

---

### Post by dckirba on 2010-12-04
Hi guys, did anyone find out how to do this yet. I am using Ubuntu 10.10 and the version of Calibre is 0.7.18. Unfortunately, the driver for my reader is in a later version so I really do need to upgrade. So if anyone has figured out how to, please let me know.

Cheers, 
David

---

### Post by gspawn69 on 2010-12-04
Yeah, I use the binary install command on the website, but you need to have a few things installed for it to work. Taken from the Calibre website:

> 
    * You need GLIBC 2.10 or higher to run versions greater than 0.6.29. If you receive an error about GLIBC you can downgrade to an older version by getting the .tar.bz2 file for your architecture (32bit or 64bit) from sourceforge. Then delete the contents of /opt/calibre and extract the downloaded .tar.bz2 file into /opt/calibre.
    * When running the command line utilities, they will segfault after completion. This can be ignored.
    * You must have xdg-utils installed on your system before running the installer.
    * There is no uninstaller. Simply deleting the installation directory wil remove 99% of all installed files.


If you meet those requirements, just copy/paste the following into a terminal and it should work:

```

sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"

```

Calibre will also prompt you when there are new updates available and take you to the download page where you can just copy/paste this command again whenever you need to.

---

### Post by uriel1998 on 2010-12-04
> **gspawn69 said:**
> 
```

sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"

```Calibre will also prompt you when there are new updates available and take you to the download page where you can just copy/paste this command again whenever you need to.

Confirmed with 10.04.  It's worth the effort - the updates like this are (almost) as easy as when it's in the repositories.  It's definitely easier than updating under Windows was. One note - he updates OFTEN.  :)

---

### Post by dckirba on 2010-12-05
Thanks! Just another quick question - I have a pretty slow internet connection here, so does it take a long time to download and install? I have all the dependencies, but when I ran the command, nothing happened in the terminal for five minutes so I closed it. If you let me know roughly how long it took to update, I'll go find a faster connection before trying it out.

Thanks and have a good weekend,
David K

---

### Post by uriel1998 on 2010-12-05
> **dckirba said:**
> Thanks! Just another quick question - I have a pretty slow internet connection here, so does it take a long time to download and install? I have all the dependencies, but when I ran the command, nothing happened in the terminal for five minutes so I closed it. If you let me know roughly how long it took to update, I'll go find a faster connection before trying it out.


Er... the download maxes out at 30KiB (nowhere near my limit), so 10% has taken about 3.5 min.  So yeah, if you're on a modem or something, you might want to give it a while. 

It also seems to go slower right as he releases an update (duh, right?), so that might be part of it.

---

### Post by olgis on 2011-02-22
In Synaptic Package Manger is available Calibre 0.7.18 
Enjoy.

---

### Post by Woodcat on 2012-03-07
Hi, I too am having difficulty upgrading Calibre. I pasted the code into terminal as instructed on the Calibre download page, it ran for a while then came up the error: "IOError: [Errno socket error] [Errno -2] Name or service not known". Not got a clue what to do now. Any help would be much appreciated.

---

### Post by overdrank on 2012-03-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

