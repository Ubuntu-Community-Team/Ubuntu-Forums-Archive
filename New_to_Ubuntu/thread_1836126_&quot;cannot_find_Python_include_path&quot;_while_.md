---
title: "&quot;cannot find Python include path&quot; while installing moviefly"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by chris722 on 2011-08-30
Hello, I'm trying to install moviefly which is the Ant Movie Catalog counterpart for linux.

The installation process is well described on the application site:
[http://savannah.nongnu.org/projects/lmc/](http://savannah.nongnu.org/projects/lmc/)

I'm not quite sure how to install this way:

> If you are using Debian you can add the following two lines to your /etc/apt/sources.conf: 
deb [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/testing]("http://www.master-ai.uni-karlsruhe.de/%7Emerkosh/lmc/debian/testing") ./
deb-src [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/testing]("http://www.master-ai.uni-karlsruhe.de/%7Emerkosh/lmc/debian/testing") ./

And run the following as root to update your package list and install moviefly: 
$ apt-get update
$ apt-get install lmcNot because I'm scared of using terminal but I don't know how to safely edit the sources.conf file (in my case it's sources.list). It can't be edited when I open it.

So I decided to try installation "from sources"
Everything seems pretty straightforward as there are only five lines to type into the terminal

```

$ tar xvzf lmc-X.Y.Z.tar.gz
$ cd lmc-X.Y.Z
$ ./configure
$ make
$ make install

```After typing ./configure I get the message at the bottom:
"checking for Python include path... find: `/usr/include/python/': No such file or directory
configure: error: cannot find Python include path"

So I decided to search a little bit and found one interesting thread on this forum:
[http://ubuntuforums.org/showthread.php?t=59842](http://ubuntuforums.org/showthread.php?t=59842)

I followed those advices and:
1. My version of python: **$ python -V**
Python 2.7.1+

2. I don't know what this command does but after typing: **$ ls /usr/include/ | grep python**
I got two results hightlighted in red colour:
python2.6
python2.7

Is it OK or I messed something up?

[FONT=monospace][FONT=Verdana]I also installed (as the author of mentioned thread did):
$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev[/FONT]

[FONT=Verdana]but it didn't help.[/FONT]

[FONT=Verdana]I know it is very basic question as it refers to installing software, but can anyone help with this python error displaying?[/FONT]

[/FONT]

---

### Post by cgroza on 2011-08-30
Does installing "python-dev" solve this problem? It appears that the program you are trying to install requires some python headers.

---

### Post by beew on 2011-08-30
> **chris722 said:**
> 
I'm not quite sure how to install this way:
[FONT=monospace]...[/FONT]> If you are using Debian you can add the following two lines to your /etc/apt/sources.conf: 
deb [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/testing]("http://www.master-ai.uni-karlsruhe.de/%7Emerkosh/lmc/debian/testing") ./
deb-src [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/testing]("http://www.master-ai.uni-karlsruhe.de/%7Emerkosh/lmc/debian/testing") ./

And run the following as root to update your package list and install moviefly: 
$ apt-get update
$ apt-get install lmc                      

I think you can add debian repos to Ubuntu.
To add the repo to your sources list, in the terminal type

```
sudo apt-add-repository deb [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/testing]("http://www.master-ai.uni-karlsruhe.de/%7Emerkosh/lmc/debian/testing") ./
```Then update and install

```
sudo apt-get update
sudo apt-get install lmc
```Alternatively you can use a GUI, open Synaptic package manager, go to Settings > Repository > Other Software and click add and in the dialogue box type
> deb [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/testing]("http://www.master-ai.uni-karlsruhe.de/%7Emerkosh/lmc/debian/testing") ./Then close the dialogue box and reload Synaptic and then you will find lmc in your software list (you can search for it from Synaptic's search box) Right click and install.


Seems you have a python conflict. Which version of Ubuntu are you using?

---

### Post by rosencrantz on 2011-08-30
I don't think it's a python conflict, more likely the packagers didn't write the sources correctly to match your directory structure.
The package installer searches for python include files in /usr/include/python, whereas your system has the include dir /usr/include/python2.7
You could try 
cd /usr/include
sudo ln -s python2.7 python
to create a symlink but you might run into more problems later. Also, a package installed from sources is not maintained by the package manager and might be difficult to update/uninstall.
It's really much easier to edit /etc/apt/sources.list -  you just have to give your editor admin privileges by starting it with sudo from a terminal:
sudo nano /etc/apt/sources.list
sudo gedit /etc/apt/sources.list

sudo apt-add-repository, as mentioned by beew, should work too.

---

### Post by chris722 on 2011-09-02
I am unable to install MovieFly by adding repositories to sources.list due to connection problem. Probably the link doesn't work anymore.


I installed python-dev and another error occured (after ./configure command):
```

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for perl... perl
checking for perl version greater than or equal to 5.8.4... ok
checking for perl module LWP::UserAgent... ok
checking for perl module URI::Escape... ok
checking for perl module POSIX... ok
checking for a Python interpreter with version >= 2.3.4... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/site-packages
checking for Python include path... /usr/include/python2.7
checking for Python library path... /usr/lib/python2.7/config
checking python extra libraries... 
checking python module: qt... no
configure: error: failed to find required module qt

```
Can anyone help?

---

### Post by chris722 on 2011-09-04
refresh

---

### Post by jards on 2012-10-16
Hello,

facing exactly the same sequence of problems.

Anyone?

I don't want to solve this problem by using the windows version with WinE!

Can you help?

Thanks

---

