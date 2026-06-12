---
title: "command line installation ongoing nightmare!!"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by gfunkera on 2011-06-19
as i develop into a more and more normal computer user (i.e. using Linux and NOT EVER USING WINDOZE AS MUCH AS POSSIBLE because it is a waste of time and was set up by greedy people to hinder our world progress and is used by people in the working world because A) they have no clue about anything that is going on in life and B) they dont wanna be blamed for something when they mess up) i find that i become a better person.. but there is ONE linux concept that for some odd reason continues to baffle me...

i know how to install stuff using synaptic but when it comes to command line installation of programs, what the heck is the process? i read the installation documentation and it usually always has the same "run make command as root and then run make install" but that stuff never actually works for me! i always get an Error 1 or Error 2 or something!!!!! its really annoying...

also like what the heck do i do if i wanna manually install a program, say, Audacity.. when i go to this site for Natty: [http://packages.ubuntu.com/natty/audacity](http://packages.ubuntu.com/natty/audacity) , what the heck do i download and how do i install it??????? what is the process? is there a website that will explain all the various ways to manually install stuff from the command line?

somebody please point me in the right direction!!

:popcorn::popcorn::popcorn:

---

### Post by jtarin on 2011-06-19
To get you started while I look at Audacity link.
[http://tldp.org/LDP/LG/current/smith.html](http://tldp.org/LDP/LG/current/smith.html)
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by whatthefunk on 2011-06-19
To install most programs via the command line, you first need to find the program in the cache.

```
apt-cache search program_name
```

This will give you a list of programs that match the search term you entered.  Find the program you want and then do

```
sudo apt-get install program_name
```

Also, try to find Debian files, files with a .deb file extension.  These are easily downloaded and act like .exe files in windows.  They will usually install themselves automatically.

---

### Post by Shippou on 2011-06-19
Hello. Glad you're having fun. :)

First of all, synaptic downloads precompiled binaries, not source code (unless you told it to). Thus, you can run sudo apt-get <progname> in order to install applications without compiling from source.

On the other hand, make and make install are commands for compiling from binaries. make compiles the source into binary, and make install installs the binary/ies based from the contents of the application's accompanying Makefile.

In sum: you cannot issue make and make install commands from binaries downloaded by synaptic, because the former commands deal with source codes, not binaries. In the same tune, synaptic cannot install applications directly from source.

(NOTE: In case of interpreted programs, such as Python, they can be run from source, provided you have the proper interpreter already installed.)

Hope that I understood your question well, and also provide you information regarding the matter.

BTW, I am not anymore familiar with synaptic, so please feel free to correct/augment my post.

---

### Post by jtarin on 2011-06-19
For Audacity from that page...scroll all the way to the bottom.
```
Download audacity
Architecture 	Package Size 	Installed Size 	Files
**amd64** 	2,535.8 kB	6944 kB 	[list of files]
**i386** 	2,421.7 kB	6364 kB 	[list of files] 
```Click on your architecture to download, then choose mirror......no configuring...nothing else to do but after download right click on the file and choose "Open with Software Center" or "Debinstaller".
Ignore my earlier post...that is for installing software "not" in the repositories.

---

### Post by gfunkera on 2011-06-19
awesome, ill look into it... just to give you a better idea of the situation that im in: i have this laptop (that im on now and it is running linux Mint) then i have a desktop at my place of residence that runs ubuntu natty... the problem is that i dont have internet access when i return to my natty machine!!!!

so i have to download everything on my laptop and then transfer the files to the desktop and then try to install, if it doesnt work or there is a question, google is not available for me because i do not have internet there... then what i have to do is take the laptop a mile away and do research and download stuff then walk all the way home to see if what i searched for was correct.... 

very painful process...

---

### Post by jtarin on 2011-06-19
> **gfunkera said:**
> awesome, ill look into it... just to give you a better idea of the situation that im in: i have this laptop (that im on now and it is running linux Mint) then i have a desktop at my place of residence that runs ubuntu natty... the problem is that i dont have internet access when i return to my natty machine!!!!

so i have to download everything on my laptop and then transfer the files to the desktop and then try to install, if it doesnt work or there is a question, google is not available for me because i do not have internet there... then what i have to do is take the laptop a mile away and do research and download stuff then walk all the way home to see if what i searched for was correct.... 

very painful process...

Get a Netbook....less painful. Walking is good for you.:P

---

### Post by dFlyer on 2011-06-19
First apt-get.

sudo apt-get install "package name" without quotes.
sudo apt-get update  will update archive information
sudo apt-get upgrade  will update your OS 
sudo apt-get dist-upgrade   will do a distro upgrade
sudo apt-get -f install  will install missing lib.
sudo apt-get autoremove  will remove files no longer needed
sudo apt-get autoclean   will clean /var/cache/apt/archive of old duplicate files

in a terminal type man apt-get for more options concerning apt-get.

Now dpkg which is used for program with the .deb extension that you downloaded

sudo dpkg -i "package name" without quotes

in a terminal type man dpkg for more options

---

### Post by whatthefunk on 2011-06-20
> **gfunkera said:**
> awesome, ill look into it... just to give you a better idea of the situation that im in: i have this laptop (that im on now and it is running linux Mint) then i have a desktop at my place of residence that runs ubuntu natty... the problem is that i dont have internet access when i return to my natty machine!!!!

so i have to download everything on my laptop and then transfer the files to the desktop and then try to install, if it doesnt work or there is a question, google is not available for me because i do not have internet there... then what i have to do is take the laptop a mile away and do research and download stuff then walk all the way home to see if what i searched for was correct.... 

very painful process...

.deb files would be the best for you.  You still may have problems dependencies though.

---

### Post by Christmas on 2011-06-20
There are quite a lot of ways of installing from command-line. The first one, and recommended is to use the **apt-get** command. For example, to install the music player Rhythmbox you would type:
```
sudo apt-get install rhythmbox
```
This is the same as you would search for it in Synaptic and install it from there. Programs that you install this way are located inside the official Ubuntu repositories, and all their dependencies (libraries needed by the program to function) are also installed.

Regarding the second way, the one with **./configure && make && sudo make install**. This one is used to compile a program from source (you'll hardly need to use it though). This means all the development packages needed to compile that program have to be installed on the system first. Usually this is done via **sudo apt-get build-dep program_name**. So for example if you would like to compile from source the latest Rhythmbox you would first type:
```
sudo apt-get build-dep rhythmbox
```
Then uncompress the .tar.bz2 or .tar.gz archive which has the Rhythmbox source code, get inside that directory, and issue something like:
```
./configure
make
sudo make install
```
Again, this is not a preferred way of doing things, plus it is not guaranteed to work if the development libraries in your repositories are older than what the program requires.

And finally, there are the so-called PPAs (Personal Package Archives), which include newest versions for various applications, and they will install properly without much hassle. These PPAs can be found at Launchpad.net. For example, to install the latest Firefox beta version from [the official Firefox Beta PPA]("https://launchpad.net/~mozillateam/+archive/firefox-next"), you would give something like the following commands in your terminal:
```
sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```
This code adds that repository to your repositories list, it updates the packages list and installs Firefox.

Packages like [http://packages.ubuntu.com/natty/audacity](http://packages.ubuntu.com/natty/audacity) are actually packages that are included in the Ubuntu repositories, so to install audacity you'd use the Ubuntu Software Center or just type **sudo apt-get install audacity** in a terminal.

Finally, packages that end up in **.deb** are Debian archives (which Ubuntu uses), and they get installed with:
```
sudo dpkg -i package_name.deb
```
And removed with:
```
sudo dpkg -r package_name
```
However, problems may arrive because for installing like this you'll also need to install the dependencies for that package manually with **apt-get**.

---

### Post by gfunkera on 2011-06-26
> **christmas said:**
> there are quite a lot of ways of installing from command-line. The first one, and recommended is to use the **apt-get** command...
...
...
However, problems may arrive because for installing like this you'll also need to install the dependencies for that package manually with **apt-get**.

dude you are awesome! Thanks a bunch!

---

