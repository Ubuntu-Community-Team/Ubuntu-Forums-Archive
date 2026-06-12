---
title: "ubuntu and MAGIC/xilinx vlsi"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by bdipanjan on 2010-02-05
hi..
i just started using ubuntu.
i had installed it within windows as of now....and want to install both xilinx and magic in it.is there anyone who has used either of the two in ubuntu.if u have please provide me with any known problems that may occur.
i have got a few questions.
1.)i have got the xilinx webpack for red hat linux.have been trying to get it installed.but i cant.cant u tell me the commands to do so!!
2.)same for magic.
3.)well both magic and xilinx in there memory requirements have specified the ram size....i have installed ubuntu on 6 gb space within a drive in my windows partitions....
can neone tell me how much space these softwares require in the os for installation...like windows programme files...it should store up some data nah in linux too....can neone tell me about how much space these two softwares may take up for such purpose??

THANK YOU IN ADVANCE FOR UR RESPONSE

THIS IS WHAT I AM FACING WHILE TRYING TO INSTALL MAGIC-7.5.188......
ITS SHOWING THE FOLLOWING ERROR MESSAGES

checking for library containing strerror... none required
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for gm4... no
checking for gnum4... no
checking for m4... no
configure: error: M4 is required


I HAVE DOWNLOADED FROM [WWW.OPENCIRCUITDESIGN.COM]("http://WWW.OPENCIRCUITDESIGN.COM") THE PRESENT STABLE VERSION.EXTRACTED THE TAR ARCHIVE ONTO DESKTOP.GONE TO THE DIRECTORY THAT CONTAIN THE INSTALL FILE WHICH IN MAGIC-7.5.188 AND INSIDE IT USED THE  ./CONFIGURE
THE PROCESS IS ABRUPTINGLY ENDING IN THIS ERROR

day 3==>  I GOT M4 IN SYNAPTIC AND INSTALLED IT.
CONFIGURE IS RUNNING FINE BUT MALE IS GIVING ERROR

dell@ubuntu:~/Desktop/magic-7.5.188$ make
--- errors and warnings logged in file make.log
--- making header file database/database.h

IN THE MAKE.LOG IT SAYS

make[1]: Entering directory `/home/dell/Desktop/magic-7.5.188'
--- making header file database/database.h
./scripts/makedbh database/database.h.in database/database.h
/bin/bash: ./scripts/makedbh: /bin/csh: bad interpreter: No such file or directory
make[1]: *** [database/database.h] Error 126
make[1]: Leaving directory `/home/dell/Desktop/magic-7.5.188'
PLEASE HELP


I WAS MISSING THIS,,

Configuration Summary (principle requirements):

X11:          yes
OpenGL:       no

  OpenGL graphics are considerably better than the standard 8-bit
  and 24-bit X11 graphics, provided that you have a video card and
  driver supporting accelerated OpenGL graphics.  If you get this
  message, you may need to download OpenGL libraries and header
  files, which are usually available from the video card manufacturer.
  Magic with un-accelerated OpenGL, such as using Mesa GL without
  a supported graphics card, is usually a very bad combination.

Tcl/Tk:       no

  Without Tcl/Tk, you cannot run the enhanced version of magic
  with the toolbar and menus, and a number of other functions
  are disabled.  If you did not specifically disable Tcl/Tk on
  the configure command line, then getting this message means
  that you do not have Tcl/Tk headers and or libraries installed,
  or they are not in a standard path.  Try using configure options
  --with-tcl=<DIR> and --with-tk=<DIR>.

-----------------------------------------------------------

Use 'make' to compile and 'make install' to install.

Errors may not be printed to stdout:  see files 'make.log' 
  and 'install.log' for complete error summary.

-----------------------------------------------------------

HOW TO FIX THIS

---

### Post by thulefoth on 2010-02-05
Hi,  I'm new too, so ... 

I've been installing lots of software ... but I've been getting it all from the Ubuntu repositories.  Software Center.  Add & Remove Progams.  Synaptic Package Manager.  

I searched Synaptic (the most exhaustive source) with 'xilinx'.  There are 2 entries for this term; one looks like it might possibly be related to what you are after.  

I did not search using 'magic', because there are many uses of that word and one will have to scroll down through lots of returns looking for the right thing. 'Xilinx', tho - easy search-term!  

In general, if you find a package from another distribution, like your Xilinx stuff for Red Hat, it is possible to get the same software going on Ubuntu, but it is not as simple as it is with the repositories of software that are made for Ubuntu.  

To be able to take something from Red Hat and get a version of running on Ubuntu, might take some studying & learning.  It's a good thing to do, and I will be doing it myself, but it's an investment of reading & training.    Take a look at topics like "3rd party programs", 'compiling', 'building' and 'unsupported software'.

---

