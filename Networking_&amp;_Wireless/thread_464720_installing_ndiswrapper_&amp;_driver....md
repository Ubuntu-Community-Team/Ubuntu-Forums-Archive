---
title: "installing ndiswrapper &amp; driver..."
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by fflarex on 2007-06-05
Alright, I've looked online high and low for more than 6 hours, trying to figure out how to get my wireless working, and the only thing keeping me going is that I unintentionally got rid of my entire vista partition getting ubuntu on my computer, so I might as well keep going.

So I need a more recent version than what's in the repositories, because I have an Intel 4965AGN, which only works with versions 1.45 or 1.46 of ndiswrapper. Problem is, I have no idea how to install it. I tried reading the install file that comes with it, didn't help. Tried at least 3 or 4 other online guides, didn't help either. It seems to me so far that all of the guides I've come across assume I know how to do something that I very obvious do not. I had to improvise to get Feisty working with my video card -- significantly deviating from the instructions I found -- and that it worked is a miracle because I know absolutely nothing about the command line.

So can someone here either explain this to me very clearly, without skipping steps, or direct me somewhere which does? I don't want to rely on luck again. I need a) walthrough of installing newest version of ndiswrapper, b) walkthrough of installing driver.

Seriously, generic instructions are fine if they're specific enough and they work (like instructions on how to install anything from tarballs or how to install any ol' wifi driver), but so far I've found plenty that haven't worked.

---

### Post by kevdog on 2007-06-05
Did you install ndiswrapper from the cd initially?

What version do you have??? 
ndiswrapper -v

You could download an updated ndiswrapper package from here: [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)


Watch however that you have all dependencies met.  One method to do this would be to open the gdebi-gtk from command line, then search for the package you just downloaded.  It should then tell you if you have any unresolved dependencies. If you do not go ahead and then install ndiswrapper.

---

### Post by fflarex on 2007-06-05
Yeah but the ndiswrapper in that link is only version 1.38.

Right now I have 1.46, but it's a tar.gz and I don't know what to do with it.

---

### Post by kevdog on 2007-06-05
You need to install the package you have from source which actually is very easy.

From the cd or internet you need to install the build-essential package.

Then unzip your package of ndiswrapper.  Go into the unzipped directory, then type
make clean
make
sudo make install

The most import part is that before installation you need to remove your old ndiswrapper package.
sudo modprobe -r ndiswrapper
sudo aptitude purge ndiswrapper.

Then install your ndiswrapper package.

---

### Post by fflarex on 2007-06-05
Where should the directory be? I know it probably doesn't matter too much, but I don't want it on my desktop like it is now, and I'm unfamiliar with the filesystem. Where would be a logical place to put it?

---

### Post by scottDkoDer on 2007-06-05
```
sudo mkdir /home/mydrivers
cd /home/mydrivers
sudo do what ya gotta do
```

btw: It doesn't matter if its on the Desktop
```
cd ~Desktop
```

---

### Post by fflarex on 2007-06-05
Okay, then I don't understand this. Can I get rid of this directory after it's compiled? I guess I'm thinking of it like a program folder on windows. I know I could have it on the desktop if I really wanted, but to do so would lead to crazy unorganization eventually.

---

### Post by Maniac Matt on 2007-06-05
I believe that you can remove the directory from your desktop. But don't hold me to it bercasue I am also newer to Ubuntu.

---

### Post by kevdog on 2007-06-05
Once you compile and then install the package you can delete any of the compiled and source packages.  The desktop folder is just a folder like any other, except this is the folder that get shown by default on the background.  You could do everything in the desktop folder, however a lot of files would be produced. 

Just make a folder in your home directory:
mkdir ~/ndiswrapper

Put your tar file in ndiswrapper.

Untar the file, compile and install:

cd ~/ndiswrapper
sudo tar -xvzf ndiswrapper-1.46.tar.gz
cd ~/ndiswrapper/ndiswrapper-1.46
make distclean
make
sudo make install

After the installation (I would wait first to make sure everything is working in case you need to reinstall, just delete the ndiswrapper folder:

rm -R ~/ndiswrapper

---

### Post by fflarex on 2007-06-05
Alright, well I got everything working and deleted the clutter from my desktop. But now I'm curious as to what happened after I installed it. Why can I suddenly remove all the files it needed and have it still work?

---

### Post by kevdog on 2007-06-05
The executables are installed to a different location.

Try this:
1. sudo updatedb  
(Wait a few minutes to let it finish)
2. locate ndiswrapper

This will tell you were all the ndiswrapper files have been installed.

---

### Post by kevdog on 2007-06-05
Sorry I forgot to ask -- is everything working now??

---

### Post by fflarex on 2007-06-05
Yes, everything's working now. At least, everything that this topic was about.

I'm still trying to figure out some things with my laptop's touch pad and with a bluetooth mouse [here]("http://ubuntuforums.org/showthread.php?t=465665") if you would like to keep helping me get my hardware working 100%, otherwise thanks for all the help.

---

### Post by kevdog on 2007-06-05
Sorry I dont know anything about touchpad or bluetooth problems in Ubuntu.  My computer is much less technologically advanced.

---

### Post by fflarex on 2007-06-06
That's alright, just throwin' it out there. ;)

Thanks for the help with ndiswrapper, funny how much less stressed out I feel knowing that I didn't completely screw up my computer and can now get internet access from it again. Well, there's that and also graduating...

---

### Post by lefloresg80 on 2007-06-06
i can't satisfy the prerequisite:


  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

---

