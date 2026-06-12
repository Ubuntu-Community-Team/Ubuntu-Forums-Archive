---
title: "What am I doing wrong?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-05-14
Introduction for CA0106 soundcard

There are two ways of getting Linux drivers to work, you can either compile them into the kernel or build them separately as modules. Read the Kernel-HOWTO for details of how to compile a kernel.

You must turn on the sound support soundcore module. This is in the kernel. Look in the sound drivers directory and it should be the first option. Most people enable the module setting. That way you can load and unload the module manually if you have multiple soundcards/&#8203;devices or if you intend to debug or use cutting edge software which may cause your drivers to halt sometimes. Of course it also means you have more control of your system.

Most modern distros come with soundcore compiled as a module. You can check this in numerous ways. The easiest way is to type:

       modinfo soundcore

If this command returns that you have this module, then you don't need to recompile your kernel.
[edit] Quick installation

Type the following commands in the shell of your choice.
NB:  	

If you are using Hg (Mercurial) then you need to type:

        ./hgcompile "or" make build

instead of:

        ./configure


Make a directory to store the alsa source code in:

       cd /usr/src
       mkdir alsa
       cd alsa
       cp /downloads/alsa-* .

"These were the instructions I followed to install a generic driver 
The following is what I did and what I got":


??????@??????-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.28-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     73D4C7B18BCDAF17EE3F9B5
depends:        
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
??????@??????-desktop:~$ ./configure
bash: ./configure: No such file or directory
??????@??????-desktop:~$ ./hgcompile
bash: ./hgcompile: No such file or directory
??????@??????-desktop:~$ ./make build
bash: ./make: No such file or directory
??????@??????-desktop:~$ make build
make: *** No rule to make target `build'.  Stop.
??????@??????-desktop:~$ cd /usr/src
??????@??????-desktop:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': Permission denied
???????@??????-desktop:/usr/src$ sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
??????@??????-desktop:/usr/src$ sudo mkdir alsa
[sudo] password for ??????:
??????@??????-desktop:/usr/src$ cd alsa
??????@??????-desktop:/usr/src/alsa$ cp /downloads/alsa-*
cp: missing destination file operand after `/downloads/alsa-*'
Try `cp --help' for more information.
??????@???????-desktop:/usr/src/alsa$ sudo ./configure
sudo: ./configure: command not found
???????@???????-desktop:/usr/src/alsa$ sudo ./hgcompile
sudo: ./hgcompile: command not found
???????@??????-desktop:/usr/src/alsa$ 
"HELP!!!!!!!!"

---

### Post by spiderbatdad on 2009-05-14
to compile your source, you must be in the source code directory. You are in your home ditrectory. You need to open terminal and cd <source directory>
where source directory is actually the name of the directory created when you untarred the package. If this is on your desktop...cd ~/Desktop/<source directory>

---

### Post by MontelEdwards on 2009-05-14
It looks like you're trying to configure something.
You need to change directory or cd to the folder.
I am guessing that you downloaded something OR you are running it from a CD.
You need to first change the directory to that folder.
So say for example that you downloaded something and it is saved as 
montel.tar.bz2, and it is saved on your desktop.

You would have to extract that archive and then open a terminal and do ```
cd /home/<username>/Desktop/montel
```
or whatever the folder or location is.
Then you have to run your commands. And the make commands are not executables inside  the folder, so you dont do ./make
make is a program IIRC so you do sudo make or sudo make build.
I am not sure that you have to do sudo, but idk

---

