---
title: "Puzzled By the Packages:"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by manurakesh on 2009-02-13
A very inappropriate title, but the following is my difficulty.

I have been goofing around in Ubuntu for a while now, and just can't stop tinkling around with some settings in the root account.

Due to this, I have corrupted the system several times now. Whenever that happens, its time to install Ubuntu once again in a fresh installation. But the problem is that, every time I install Ubuntu once again, I have to download the packages, Media Codecs(Mp3, flash, etc) all over again.That is 1 GB of net download for each time I do that. I have got very limited access to the internet here and would thus like to know whether the packages are available as one big separate package(even several small packages would do) that I can store any where on the hard disk and install it at my perusal - rather than having to download them as updates that can't be stored as a setup or something.:confused:

---

### Post by mcduck on 2009-02-13
Every time you install something (or update) the packages downloaded from the servers are stored in /var/cache/apt/archives. They are kept as long as you don't run the "apt-get clean" command (which cleans apt's package cache).

You can simply copy the packages from there to any place you want, and then when you want to install them all run "sudo dpkg -i *.deb" in the directory where you have the package files.

---

### Post by desperado665 on 2009-02-13
Give aptoncd a try. Once you have your os configured, it will consolidate all your needed packages into an .iso for storage/burning.

---

### Post by jou770d on 2009-02-13
All packages installed via Synaptic or aptitude/apt-get are saved here:
/var/cache/apt/archives/
You can backup the content of this folder and copy it back there on a new installation. Then when you try to install this packages nothing would be downloaded.
I use this to transfer packages from desktop to laptop and vice versa. I hope it helps.

Edit: double ninja'd...

---

### Post by blazemore on 2009-02-13
What he said.

```
cp /var/cache/apt/archives/*.deb /home/**username**/debs/ -rfv
```

---

### Post by ugm6hr on 2009-02-13
Once downloaded, backup all files in /var/cache/apt/archives (except the lock file).

Then, when you next reinstall, just copy them back (using sudo) to the same directory.  The next time you install the apps, they will not be downloaded again (unless there is a newer version available in the repos).

The only thing that this won't work for is Adobe Flash and Windows fonts, which are downloaded directly from their relevant sites rather than the repos.

EDIT: Wow I'm slow.

---

### Post by redseventyseven on 2009-02-13
You could consider trying Linux Mint. It's based on Ubuntu but installs the media codecs "out-of-the-box" (i.e. you don't need to download them separately).

The other thing is to, well, learn to stop tinkering! Using the root account willy-nilly is likely to break things, and often, you can change your personal settings in your user-account and still get the same effect. Try revealing the hidden files in your home folder - there's lots of tinkering to be had using these files without risking your entire system.

---

### Post by manurakesh on 2009-02-13
Wow:cool: that was fast..
Thanks a lot. i'll try it when I get back to my lappy=D>

---

### Post by jou770d on 2009-02-13
> **redseventyseven said:**
> 
The other thing is to, well, learn to stop tinkering!

I don't know about that, for me getting used to any program or OS includes trying to trigger everything that could go wrong using it.

---

### Post by redseventyseven on 2009-02-13
> **Amarus said:**
> I don't know about that, for me getting used to any program or OS includes trying to trigger everything that could go wrong using it.

Fair point. I guess it depends on what you want your system for. If you want it to learn about how computers work, then tinker to your heart's content. If you're using your computer to help you do something productive like write reports or analyse data, then there's a point at which the tinkering becomes counter-productive.

Also, I'm suggesting that the original poster try tinkering with the user settings rather than using root all the time.

---

### Post by capnthommo on 2009-02-13
hi manurakesh, sorry to butt into your thread but this is really interesting to learn.
so amarus, if i make a dvd copy of all the files in (/var/cache/apt/archives/) all i would have to do is reinstall ubuntu from live disk and then 'restore/install' the dvd and that would effectively give me back the codecs, apps and updates to apps i had installed myself?  or am i reading this wrongly.
sorry again to butt in
thanks
nigel

---

### Post by jou770d on 2009-02-13
Unless the package is installed manually you will get everything back. But without any setting changes that you might have made, those are saved else where.
Plus you have to remember that:
> **mcduck said:**
> They are kept as long as you don't run the "apt-get clean" command (which cleans apt's package cache).
> **ugm6hr said:**
> 
The only thing that this won't work for is Adobe Flash and Windows fonts, which are downloaded directly from their relevant sites rather than the repos.

Personally I have two simple scripts to automate package transfer to and from an external hdd to keep things synchronized between different installations, the first one copies all packages to a folder created where the script is running and the second one puts the packages inside that folder where they should be:

```
#!/bin/bash

mkdir -pv packages_copy
sudo cp -vu /var/cache/apt/archives/*.deb ./packages_copy/

```

```
#!/bin/bash

sudo cp -vu ./packages_copy/*.deb /var/cache/apt/archives/

```

P.S: those script must run in a terminal because of the sudo in there.

---

### Post by capnthommo on 2009-02-13
hi, and thanks for the scripts Amarus.
so the first will create a directory called (packages_copy)
and copy (/var/cache etc) into it  and the second will copy the contents of the directory (packages_copy)  back into (/var/cache etc).  is that right? 
but what do [-pv] and [-vu] mean?  
where will the directory called (packages_copy) be created?  i can see how it works but some bits are a little unclear to me.  i am afraid i am not very familiar with this sort of procedure (working with/creating codes/scripts)
thanks very much
nigel

---

### Post by jou770d on 2009-02-13
Let's say the first script is currently located on your desktop, you double click and chose run in terminal. First thing it'll try do is the mkdir command which will create a new folder the "./" in the begining of the folder name means that the folder's location is relative to the script's location and that it's in the same folder (./ means current folder and ../ means parent folders).
The p flag in -pv means that if the folder already executes it's not a problem will just use it as it is, the v makes the command print a message on the terminal stating what it accomplished.
Second command copies all .deb files in /var/cache/apt/archives/ no matter what there names are, and puts them in the folder from the fist command.
The v in the arguments is the same as above, while u makes it only copy if the the source file is newer than the destination or if there isn't already a file by the same name.
In order for the second script to work properly it should also be in the same folder that contains packages_copy (desktop in our case). Or you could change the folder's name in the script (usually it's better to use complete address in that case, e.g. /home/amarus/Desktop/packages_copy/).

Scripts are just a list of terminal commands put together for convenience. You can understand each command in details by opening up a terminal and writing the name of the command then --help (e.g. "cp --help" or "mkdir --help")

If you're interested in learning more about terminals and ubuntu in general you should check this:
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)
There's a free pdf for download it should have some intersting info (chapter 5 is about terminals).

---

### Post by hyper_ch on 2009-02-13
just one thing: you cannot used the packages you downloaded in 8.04 for a 8.10 install. They are only for the ubuntu version which they were downloaded for.

---

### Post by capnthommo on 2009-02-13
hi again amarus
firstly thanks again, i already have the guide download, but i haven't had chance to really look at it yet.  i shall certainly give chapt 5 a read.
anyway, i copy/pasted and ran your scripts in a terminal and i now have a nice folder in my 'home folder' entitled 'packages_copy'  it has all the files from the relevent /var/archive folder.  i am quite happy to have it where it is, and i can now burn it to a data dvd as it is only about 700Mb.
of course, when i get an external hdd i shall be able to backup the whole system - settings and all, and a copy of my data and a copy of the packages to cover updates/grades and system crashes etc - i feel happier with too many safety nets than too few. as the song says 'its better to have and not need than to need and dont have'
anyway, this has helped me a lot
thanks
nigel

---

### Post by jou770d on 2009-02-13
Your welcome ;)
And it seems like this might be of interest to you: [http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

