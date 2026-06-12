---
title: "How to install apps through .TAR.GZ"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Thilo Kuhlman on 2009-01-10
OK. I am getting frustrated with earlier posts and am now creating a thread to answer a seemingly obvious question so obvious an answer hasn't been posted. If I download a program in a .tar.gz archive or similar archive how do I install the program into a running state? 
From a downloaded archive of random files.
To a application ready to run.
If I can figure this out I can get about 20+ people to install Ubuntu, they said if they didn't have some programs they weren't going to switch. I found the equivalent programs online, but they aren't .deb's, they are archives. How can i turn these worthless files into the applications?
:?::?::?::?::?::?::?::?:

---

### Post by ibizatunes on 2009-01-10
what is the fine name and the location

---

### Post by wizard10000 on 2009-01-10
Easiest way to do it is to put the archive in a temporary directory and then use Archive Manager to extract the files - or open a terminal window and type

```
tar -xvzf *filename*.tar.gz
```

then you should find a readme that tells you how to finish installing the program.  If it's already compiled there will be an installer script - if not you'll need to do something like

```
.configure
make
make install
```

to get the program installed.

Good luck -

---

### Post by taurus on 2009-01-10
> **wizard10000 said:**
> Easiest way to do it is to put the archive in a temporary directory and then use Archive Manager to extract the files - or open a terminal window and type

```
tar -xvzf *filename*.tar.gz
```

then you should find a readme that tells you how to finish installing the program.  If it's already compiled there will be an installer script - if not you'll need to do something like

```
**[COLOR="Red"].configure[/COLOR]**
make
**[COLOR="Red"]make install[/COLOR]**
```

to get the program installed.

Good luck -

It should be

```
./configure
make
sudo make install
```
However, you need to install the build-essential package first before you can compile anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by kansasnoob on 2009-01-10
It really does vary greatly depending on individual tar.gz's.

We could help much more if we had a list of individual programs that folks want to install.

It's not at all uncommon to find that someone has written a .deb or something similar, like making a program available via a ppa, etc.

Then there are certain oddities, an old version of Xnview comes to mind, where I found the rpm worked better for me using alien than the tar file did.

Or, if someone wants the official Mozilla build of Firefox, Thunderbird, or Seamonkey, Ubuntuzilla works like a dream!

---

### Post by steveneddy on 2009-01-10
What applications, specifically, are you trying to install?

We may be able to help you if you offered more info.

What have you tried so far?

Some of this can be done graphically, but some things need to be done in the terminal.

You need to learn that 

**cd** means "change directory"

When you first open the terminal, it's default location is the /home folder.

If you download something to the Desktop, you need to "go to" the Desktop in the terminal, or you need to "change directories" ( **cd** )

You accomplish this by typing in the terminal (or you can copy and paste)

```
cd ~/Desktop
```The little [COLOR=Blue]**~**[/COLOR] sign means look in the /home folder for the Desktop folder (or directory)

then

```
tar -xvzf filename.tar.gz

```

     
     ```
./configure
make
sudo make install 
```


However, you need to install the build-essential package first before you can compile anything from source.

     
```
sudo apt-get update
sudo apt-get install build-essential 
```


(thanks to taurus)

It's not that hard. You want the terminal to change to the directory where the .tar.gz file is so you can work with it.

Then you unpack it, because it is like a .zip file, by using the

```
tar -xvzf filename.tar.gz

```

command.


then you have to **configure** the software to your individual system.

then you have to **make** the software ready to install.

then use the make command to install the software

**sudo make install**

sudo means do this as an administrator.

you will need to enter your password.

That should get your software installed.

**Depending on what you install, sometimes you need to restart or even make a custom launcher to run your application.**

Also look at the first two links in my sig.

It will help.

---

### Post by kapok on 2009-01-10
i saw that you're guide is for hardy.
are the commands the same on intrepid?

---

### Post by steveneddy on 2009-01-10
> **kapok said:**
> i saw that you're guide is for hardy.
are the commands the same on intrepid?

Yes - or you could use this link for Intrepid.

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

There may be a few small differences between Hardy and Intrepid, but for the most part things are the same. It's all Linux, you know.

---

### Post by Thilo Kuhlman on 2009-01-10
[http://sourceforge.net/project/downloading.php?groupname=lbpp&filename=glbcc-0.1.1-linux-xw32.tgz&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=lbpp&filename=glbcc-0.1.1-linux-xw32.tgz&use_mirror=voxel)

And similar programs  such as Xlink Kai for Linux.

---

### Post by ajgreeny on 2009-01-10
If you have not already found this site, there are a lot of .debs for things not in the repos that can be downloaded from [http://www.getdeb.net/](http://www.getdeb.net/).  I have a few things from there and they all seem to work great, though there are occasionally dependency problems to be sorted out, but nothing too taxing so far.

---

### Post by Thilo Kuhlman on 2009-01-10
Nothing works :( 
Any archive I get from the internet sits on my desktop taking up space.
Exactly, for Hardy, do I type into terminal to get these programs working?
If possible, have all variables in [brackets] with an explanation, thanks.

---

### Post by oldos2er on 2009-01-11
Maybe this will help: [http://lbpp.sourceforge.net/documentation.html](http://lbpp.sourceforge.net/documentation.html)

---

### Post by nanotube on 2009-01-11
> **Thilo Kuhlman said:**
> Nothing works :( 
Any archive I get from the internet sits on my desktop taking up space.
Exactly, for Hardy, do I type into terminal to get these programs working?
If possible, have all variables in [brackets] with an explanation, thanks.

try the ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Handling_.28Tar.2FGZip.29_and_.28Tar.2FBzip2.29_archives](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Handling_.28Tar.2FGZip.29_and_.28Tar.2FBzip2.29_archives)

---

