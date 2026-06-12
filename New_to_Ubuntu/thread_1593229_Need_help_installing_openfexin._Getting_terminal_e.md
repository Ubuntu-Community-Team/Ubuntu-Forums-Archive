---
title: "Need help installing openfexin. Getting terminal errors following instal instructions"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by tbhoff on 2010-10-11
Im currently trying to install openfexin 1.9 (a program based on china mobile's fetion program to send and receive free text messages to chinese cell phones) on my computer. I beleive im using version 9.04 (Jolicloud). 


 Being a recent convert from windows, im having a bit of difficulty. Ive read quite a few tutorials on installation, basic commands, as well as searched the forums, but I can't find anything specific enough to help me.



I tried to download it using the instructions from the official website:
[http://basiccoder.com/openfetion](http://basiccoder.com/openfetion)

I downloaded the tar.gz, extracted the files to a new folder.

Then after checking the read me file, I saw these instructions:
"
WEB SITE

Visit the openfetion web site for the latest news and downloads:

[http://basiccoder.com/openfetion](http://basiccoder.com/openfetion)

INSTALLATION

It requires these library : openssl , libxml2 , gtk+2.0

If there are no such libraries in your system You can install these library like this:

sudo apt-get install libgtk2-dev

sudo apt-get install libssl-dev

apt-get install libxml2-dev

sudo apt-get install pkg-config

Then you can start installing openfetion like this:

autoreconf -fiv
./configure --prefix=/usr
or your can enable debug mode to trace the runing information with --enable-debug

make

sudo make install 

"

As I was not sure if i had these libraries. i used the first command:
"sudo apt-get install libgtk2-dev"
and i get this result:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk2-dev
brenden@bh-netbook:~$ "



I get the same result when trying to add any of the other libraries

I tried to run the last command : "autoreconf -fiv
./configure --prefix=/usr"

and i get this result:
brenden@bh-netbook:~$ autoreconf -fiv
The program 'autoreconf' can be found in the following packages:
 * autoconf
 * autoconf2.13
Try: sudo apt-get install <selected package>
bash: autoreconf: command not found
brenden@bh-netbook:~$ ./configure --prefix=/usr


Im incredibly confused and im sure that this is a problem with me doing something wrong. If someone could explain to me what i am doing wrong, or guide me through this installation i would be eternally grateful.

I would ask for help directly from the developers or try and find a solution on google or the ubuntu forums (which i did of course), but as this is chinese software for use in the PRC, all the websites and users seem to be communicating in Chinese- and have almost no useful Chinese computer vocabulary.

I was hoping that someone here would be generous enough to walk me through this process (as mind numbingly basic as it may be for any slightly-advanced linux user). 


I also found this information on the website:

9.04: Code: Deb [http://ppa.launchpad.net/happyaron/ppa/ubuntu](http://ppa.launchpad.net/happyaron/ppa/ubuntu) jaunty Main

But inputing this code does nothing for me (more command not found errors)

Thanks


PS- I definitely tried finding deb files, etc... but couldnt find anything.  If someone else knows of/can find an easier way install this other than a tar file, im definitely fine with that too :)

---

### Post by tbhoff on 2010-10-16
never mind- all fixed. i looked over it again and reallized I was just making some REALLY stupid mistakes.

---

