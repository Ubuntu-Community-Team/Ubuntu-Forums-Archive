---
title: "install musescore"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by joseielpi on 2011-02-09
Hello; I am hoping to learn how to install software from source. I wish to make use of the latest version of musescore music editor, but there haven't being any updates available for lucid lynx (the latest version available is 0.9.6, whereas the developers have already reached 1.0!) in synaptic for, at least, six months (last one I remember was July/August 2010). The musescore website lets one download a package, I just don't know how to build/install/compile it. Thanks in advance on any help!! :p

---

### Post by Luinar on 2011-02-09
Hey there.

To install software from source, the process is usually as follows:

1) Download the package. This is usually a .tar.gz file.

2) Extract the contents of the archive to your home directory.

3) Navigate to the folder containing the extracted files and in a terminal run the following commands:

```
./configure
``````
sudo make
``````
sudo make install
```This will compile the source code into makefiles, which are then used to install the software.

If you have not installed software from source before, then chances are you will need to install a compiler before doing so. This can be done by running:

```
sudo apt-get install build-essential
```from a terminal.

Hope that helps. :)

For more info, check out the relevant section in the Ubuntu Guide: [http://ubuntuguide.org/wiki/Ubuntu:Maverick#Installing_a_package_from_source](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Installing_a_package_from_source)

---

### Post by joseielpi on 2011-02-09
Thank you, Luinar. I've read the guide and followed the steps. When I type

Code:

./configure

I get (in my native spanish lenguage) a terminal output that says: 

"No such file or directory"

Since installed build-essential, I'm guessing the package I downloaded is actually missing that file.

---

### Post by Luinar on 2011-02-09
Hmm, Musescore seems to do things slightly differently to the standard build procedure. They have instructions on their site ([http://musescore.org/en/developers-handbook/compile-instructions-ubuntu-093](http://musescore.org/en/developers-handbook/compile-instructions-ubuntu-093)) but they are for an older version of Ubuntu so they may not work exactly as described any more.

I did quickly check out the downloads section though. It seems that the only source package of the Linux version I could find for download is the same as the one in the Ubuntu repositories (0.9.6.3). I think perhaps version 1.0 is the Windows version, which may have a different release schedule?

---

### Post by joseielpi on 2011-02-10
Actually they have a link to download the linux version of 1.0 (it's in the release notes for version 1.0) That's the one i've tried to install. Strange enough, i've also noticed that Maverick repositories have the 0.9.6.3 version you reffer to, but Lucid repositories are stuck with older versions, and even a beta one that i could never get to open. I'll try to follow the instructions on the link you've send me, and tell you what happened.
 Again, thanks a lot!!

---

### Post by joseielpi on 2011-02-14
Hello again. I've tried out the instructions the musescore website gives out. They don't work (at least for me). 

 They read:

[CODE]

bunzip2 mscore-1.0.tar.bz2
tar xf mscore-1.0tar
cd mscore-1.0

make

cd build
make lupdate
make lrelease
sudo make install

However, after typing make, i get the following message:

[CODE]
 make: *** [release] Error 2

Any hint on what I could be doing wrong?

---

