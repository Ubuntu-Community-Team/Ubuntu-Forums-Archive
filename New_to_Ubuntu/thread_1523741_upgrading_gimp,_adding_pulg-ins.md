---
title: "upgrading gimp, adding pulg-ins"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by furoido on 2010-07-04
Hi guys,
When I try to update my Gimp from 2.6.8, I get this:

andrew@andrew-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

How do I get round it?

Also, I downloaded a couple of Gimp plug-ins onto my desktop but don't know how to install them! 
1-focusblur-3.2.6.tar.xz
2-vignette.scm

Anyone kind enough to give me the EXACT instructions to do so?!

Thanks!

---

### Post by Perfect Storm on 2010-07-04
> andrew@andrew-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

You forgot sudo. Making changes to the system requires sudo (superuser do).

```
sudo apt-get install gimp
```
or you could just use the Ubuntu software center to get it.

> 1-focusblur-3.2.6.tar.xz
That looks like Arch Linux package or Slack linux. Normally when you install stuff in Ubuntu you use what's in Ubuntu repositories  - and you don't need to manually hunt down websites for installation files

From wiki:
> xz is a lossless data compression file format that uses the LZMA2 compression algorithm. Like gzip and bzip2, concatenation of multiple compressed files is supported, but the convention is not to bundle more than one target file into an archive. Instead, xz is typically used as a compression format for files that are archives themselves, such as those created by the tar or cpio UNIX programs. xz is used by GNU coreutils versions 7.1 and newer[1] xz is used for compressing packages by Fedora Project (starting with Fedora 12)[2], Arch Linux[3] and Slackware Linux.

---

### Post by furoido on 2010-07-04
Thanks so much Artifical Intelligence!!

---

### Post by Perfect Storm on 2010-07-04
Installing extra stuff for gimp do;
```
sudo apt-get install gimp-data-extras
```
Or you can search through synaptic Package Manager to check all gimp plugins/extra stuff.

If you want to install something to gimp that isn't available through ubuntu repositories: [http://www.techzilo.com/how-to-install-gimp-plugins-scripts-brushes-and-gradients/](http://www.techzilo.com/how-to-install-gimp-plugins-scripts-brushes-and-gradients/)

> Go to your Home folder. You have to make hidden files/folders visible, so hit Ctrl+H. Go to the directory named .gimp-2.x (where 2.x is version number of GIMP you are using). Within that folder, there are subfolders, one of which is brushes. Drop your brushes to that folder.

---

### Post by SoFl W on 2010-07-04
> **furoido said:**
> 
Also, I downloaded a couple of Gimp plug-ins onto my desktop but don't know how to install them! 
1-focusblur-3.2.6.tar.xz
2-vignette.scm 

Place the viginette.scm in the "/home/USERNAME/.gimp-2.6/scripts" directory/

I don't know what focusblur is so the only thing I can tell you is your going to extract it into one of the directories in the "/home/USERNAME/.gimp-2.6/" directorym depending on if it ends with scm (script) or some other extension.    You can extract by double clicking on the file and the archive manager should open up.  Usually the plugin instructions on the plug in page will tell you where it wants you to put it.

Then restart GIMP and it should show up.

---

### Post by furoido on 2010-07-04
Hi again guys,
Followed the above instructions and vignette is installed and working nicely on Gimp, thanks
...but can't find any sign of focusblur on Gimp (I extracted the original downloaded zip file to home/andrew/.gimp-2.6/plugins folder).Any suggestions?
By the way, why is Gimp not updating to 2.7?

---

### Post by clhsharky on 2010-07-04
> By the way, why is Gimp not updating to 2.7?
Will be at next release.

Ubuntu is not a rolling release distro.

---

### Post by 23dornot23d on 2010-07-04
This is a good way to install Gimp 2.7 and it keeps it away from overwriting 2.6

**This is more for advanced users though ...... if you wait a while it should become available for all - sometime in the near Future ........ (  )**

But if you cannot wait here is one way .... the safest way I know .........

[Gimp 2.7 Install]("http://www.gimptalk.com/tutorial/compile-latest-gimp-source-%28developer-version%29-39598-1.html") ...... follow it step by step ...... 

( I know there is a PPA - but this allows for both versions running cleanly .... side by side )

create a launcher too ...... it will look like this ...... takes a little extra effort but its worth it.

[IMG]http://sites.google.com/site/23dsources/allsorts/gimp1.jpg?attredirects=0[/IMG]


 The final command to run GIMP 2.7 is wrong though  ....

the final line should be .........

 /opt/gimp-2.7/bin/gimp-2.7

_____________________________________________________________________

Focusblur needs compiling ...... but there is a link here with more information [focusblur]("http://sudakyo.hp.infoseek.co.jp/gimp/fblur/focusblur_e.html#install")

_____________________________________________________________________

If you want to add focusblur to the above v2.7 then carry on and do this .......... in a terminal ......
(after downloading the files and extracting them ......)

cd focusblur-3.0.20 [COLOR=Red](or the version you chose here)[/COLOR]
./configure --with-gimp-prefix=/opt/gimp-2.7
make
sudo make install

It appears then under - [Filters - Blur - Focus blur]("http://5270667693938030042-a-1802744773732722657-s-sites.googlegroups.com/site/23dsources/allsorts/gimp2.jpg?attachauth=ANoY7creyycqVmaIU8nYffVFG2ejPofMPvZiRV6kGNXqfGLqJE7GNrCCdFhMdEnqk4UoQ4qPd5IUOoI7lxNNSCdD2JGGd6BB_mpl5HEFPrZAlTFCWdQZBWiWSQeg-DE3zluBEtuRaPC69Kw5HJls777Kwe8q8c_jGsyzYDq5iUaCvZQifFeWcgCGjBLQBLkV5TtAiQWIX1waMnMBX1EdZvwEu28bsF0Jug%3D%3D&attredirects=0") ......

_____________________________________________________________________

Here are 3 things that I like to add to Gimp ( [ScriptFu]("http://users.telenet.be/ev1/gimpphotoeffects_en.html") - [GMIC]("http://gmic.sourceforge.net/gimp.shtml") - [FxFoundary]("http://sourceforge.net/projects/gimpfx-foundry/files/gimpfx-foundry-scriptpack/scriptpack-20080323/gimpfx-foundry-scriptpack-20080323.zip/download") )
These do enhance the Gimp Experience - but also add a lot of extra Menu items too ...

---

