---
title: "Problems installing ROOT"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Blatm on 2011-06-02
Hi,

Warning: I got Linux yesterday.

I'm looking to install ROOT (root.cern.ch) on Ubuntu 11.04 64-bit. I downloaded the source for version 5.28.00 (root.cern.ch/drupal/content/downloading-root), extract it, and ./configure. I get the message
```

Checking for libX11 ... no
configure: libX11 MUST be installed
```root.cern.ch/drupal/content/build-prerequisites says that I need libx11-dev. However, when I sudo apt-get install libx11-dev, I get the message
```

libx11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```I'm not sure how to proceed from here. It looks like the libx11 files are in /usr/lib32 when maybe they should be in /usr/lib, but I don't know how to move them (copy/paste doesn't work, and again, I got Linux yesterday).

Is anyone familiar enough with this stuff to help me out? Thanks.

---

### Post by iansane on 2011-06-02
I don't remember seeing lib32 before I installed 64bit OS and I"m pretty sure that's why it is there. Those files definitely don't need to move but copying them over might do the trick. See the part in the configure file that looks for them?
```
if test ! "x$enable_x11" = "xno" ; then
    check_library "libX11" "yes" "$x11libdir" \
        ${finkdir:+$finkdir/lib} \
        /usr/lib /usr/X11R6/lib /usr/lib/X11 /usr/openwin/lib \
        /usr/local/lib /usr/local/lib/X11 /usr/local/X11R6/lib \
        /usr/X11/lib /usr/lib/X11R5
```

lib32 is not in the list of directories to search so I'm pretty sure this is not made for a 64bit system.

Having said that you can do alt-f2 and type gksudo nautilus to copy/past as root. I was going to give the terminal command for copying but now I'm confused because my xll directory is in /usr/lib but then some libx11*.so files are in /usr/lib32 so yeah just use the alt-f2 way and copy what you think will make it work.

Still don't know if this will work since it looks like it wasn't made for 64bit

---

### Post by Blatm on 2011-06-02
Thanks for the quick reply.

I successfully copied libX11.so, libX11.so.6, libX11.6.3.0, libX11-xcb.so, libX11-xcb.so.1, and libX11-xcb.so.1.0.0 equivalents, but I still get the same error ("Checking for libX11 ... no  //  configure: libX11 MUST be installed")

EDIT: I tried copy/pasting everything in my usr/lib32 folder that started with libX into my usr/lib folder (skipping duplicates) and I still get the same error.

---

### Post by Blatm on 2011-06-03
This problem is still unresolved.

---

### Post by Legion81 on 2011-06-03
I was just having the same problem.

I linked libX11.so to the actual file with:
sudo ln -s /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 /usr/lib/libX11.so

When I ran ./configure again, the libX11 error was gone, but now there was a new error with libXft. I linked that file the same way and had to do it again with libXext and ./configure finally ran. I'm currently running make, so you may want to go to /usr/lib/ and search for libX11. The libX11.so file will probably be linked to something like libX11.so.something (6.3.0 in my case), so make sure you use the file that it is linked to.

Hope that helps.

---

### Post by Legion81 on 2011-06-03
Oh, I just noticed that you were looking for the files in /usr/lib32. lib32 is not the correct place. You want to get look for the file in lib. It will probably be in /usr/lib/x86_84-linux-gnu if you have 64bit installed. Make sure you are in lib and not lib32. That could be why you are having issues.

---

### Post by Blatm on 2011-06-03
It's making!

Thanks, Legion81. The ln -s didn't work (maybe because I had already copied something from lib32 there with the same name), but I copy/pasted the three files you mention (libX11, libXt, and libXext) from usr/lib/x86-64-linux-gnu and the ./configure worked.

---

### Post by Blatm on 2011-06-03
Update: the make didn't work.

I get the error
```
bin/rmkdepend -R -fproof/proof/src/TDataSetManager.d -Y -w 1000 -- -pipe -m64 -Wshadow -Wall -W -Woverloaded-virtual -fPIC -Iinclude  -pthread -D__cplusplus -- /home/blatm/Downloads/root/proof/proof/src/TDataSetManager.cxx
g++ -O2 -pipe -m64 -Wshadow -Wall -W -Woverloaded-virtual -fPIC -Iinclude  -pthread -o proof/proof/src/TDataSetManager.o -c /home/blatm/Downloads/root/proof/proof/src/TDataSetManager.cxx
/home/blatm/Downloads/root/proof/proof/src/TDataSetManager.cxx: In member function ‘virtual void TDataSetManager::MonitorUsedSpace(TVirtualMonitoringWriter*)’:
/home/blatm/Downloads/root/proof/proof/src/TDataSetManager.cxx:708:1: internal compiler error: in redirect_jump, at jump.c:1443
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.5/README.Bugs> for instructions.
make: *** [proof/proof/src/TDataSetManager.o] Error 1
```

?.

---

### Post by Legion81 on 2011-06-03
You can fix that by opening root/config/Makefile.linuxx8664gcc and a few lines down you will see:

OPTFLAGS = -O2

delete the "2" so you have OPTFLAGS = -O

You will probably want to run "make clean" before you run make again.

You can also use v5-30-00 instead of v5-28-00. It has most of these problems fixed.

---

### Post by JohnBonne on 2011-06-03
Am going to save / subscribe to this thread because I had a required output from something i was installing / updating and said such adn such information was to be in X11 but that directory is blank/

I am pretty new at this but love it.

---

### Post by Blatm on 2011-06-03
Once again, it seems like Legion81's suggestion has fixed my problem.
Once again, I have another problem:

```

Creating executable ../../bin/xrdadler32
g++ -m64  -D_ALL_SOURCE -D_REENTRANT -D_GNU_SOURCE -fPIC -rdynamic -Wall  -Wno-deprecated -D__linux__  -O2 ../../obj/Xrdadler32.o  ../../lib/libXrdPosix.a   ../../lib/libXrdClient.a -L../../lib -lXrdNet  -lXrdOuc -lXrdNetUtil -lXrdSys  -lnsl  -lrt -ldl -lc  -o  ../../bin/xrdadler32
../../obj/Xrdadler32.o: In function `main':
/home/blatm/Documents/root/net/xrootd/src/xrootd/src/XrdApps/Xrdadler32.cc:176: undefined reference to `adler32'
/home/blatm/Documents/root/net/xrootd/src/xrootd/src/XrdApps/Xrdadler32.cc:218: undefined reference to `adler32'
/home/blatm/Documents/root/net/xrootd/src/xrootd/src/XrdApps/Xrdadler32.cc:255: undefined reference to `adler32'
collect2: ld returned 1 exit status
make[5]: *** [../../bin/xrdadler32] Error 1
make[4]: *** [Linuxall] Error 2
make[3]: *** [all] Error 2
make[2]: *** [XrdApps] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/blatm/Documents/root/net/xrootd/src/xrootd'
*** Error condition reported by make (rc = 2):
make: *** [net/xrootd/src/xrootd/LastBuild.d] Error 1
```I hear that the most recent version (in this case 5.30) tends to be a bit unstable so I am somewhat reluctant to use it over 5.28. However, with all the problems I'm getting (3) it might be worth it.

---

### Post by Legion81 on 2011-06-04
It looks like v5-28-00d has a fix for that:
[http://root.cern.ch/drupal/content/root-version-v5-28-00-patch-release-notes](http://root.cern.ch/drupal/content/root-version-v5-28-00-patch-release-notes)

You can rename (or delete) your current root folder and download this one. Then run configure, make, and set the path. Hopefully that will do it.

v5-30 will be the production version in a few weeks so I wouldn't imagine it has major issues, probably just a minor bug here and there.

---

### Post by Blatm on 2011-06-04
I could make v5.30.00 without any problems. However, now the install guide tells me to


"Add bin/ to PATH and lib/ to LD_LIBRARY_PATH. For the sh shell family do: . bin[COLOR=#000000]**/**[/COLOR]thisroot.sh
 and for the csh shell family do: [COLOR=#7a0874]**source**[/COLOR] bin[COLOR=#000000]**/**[/COLOR]thisroot.csh"


I don't know what that means. Typing the command verbatim gives "permission denied", and I don't want to sudo things without knowing what they do.

---

### Post by Legion81 on 2011-06-04
Oh good, it's working. Open a terminal and type this:

nano ./.bashrc

A file will open. Scroll to the bottom and add these three lines:

cd root
. bin/thisroot.sh
cd

Notice there is a space between "." and "bin/thisroot.sh". It won't work without the space.

Close the terminal and open a new one. You should be able to type "root" to launch ROOT.

---

### Post by Blatm on 2011-06-04
That didn't work.

My terminal looks like

```

blatm@Bob:~$ nano ./.bashrc
blatm@Bob:~$ root
No command 'root' found, did you mean:
 Command 'rootv' from package 'xawtv' (universe)
 Command 'rott' from package 'rott' (multiverse)
 Command 'rbot' from package 'rbot' (universe)
root: command not found

```and the file that opes when I type nano ./.bashrc is

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend


[...]


  GNU nano 2.2.6              File: ./.bashrc                                   

# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

cd root
. bin/thisroot.sh
cd


```I also tried doing it in my root folder (/cernroot/root, where I ./configured and maked). There the file was empty. I tried just trying it and closing, but that didn't work, and when I opened the terminal again the changes were reverted. I then left with ^X, and said Y when they asked if I wanted to save.

EDIT: I also tried changing the first line to cd Documents/cernroot/root since the path to the root folder is ~/Documents/cernroot/root (i.e. guessing that the cd is the same cd I use to navigate), but that didn't work either.

---

### Post by Legion81 on 2011-06-04
Yes, you want to do ctrl+x and save. I should have mentioned that. The "cd root" was assuming you put the ROOT folder in /home/username/ so if it is somewhere else, you will want the actual path.

If you look in the root folder you should have about 35 sub-folders, including one called "bin". That is where the "thisroot.sh" file is located. If not, it didn't install correctly. If your root folder is empty, check to make sure a new folder called root wasn't created somewhere else, like /home/username or /home/username/Documents. That would be strange if make finished but there aren't any files.

After you add the line to bashrc, you will have to exit the terminal and open a new one. If you don't do that the command "root" won't do anything.

---

### Post by Legion81 on 2011-06-04
You can also do what it says in the user manual and type:

export PATH=$ROOTSYS/bin:$PATH
export LD_LIBRARY_PATH=$ROOTSYS/lib:$LD_LIBRARY_PATH

but the . bin/thisroot.sh seems to be easier and works every time you start a new session.

---

### Post by Blatm on 2011-06-04
it works!

Thank you very much Legion81.

(I tried the nano ./.bashrc thing again, changing the path ,saving, etc. and it worked this time. Maybe I didn't try every combination of saving/changing path/where to nano ./.bash,/etc. last time.)

---

### Post by ceejay724 on 2011-07-02
THANK YOU

This thread has been most helpful

---

