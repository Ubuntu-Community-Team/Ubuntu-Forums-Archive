---
title: "Installing pygame in python 3.. Help please."
date: 2010-12-19
forum: New to Ubuntu
---

### Post by colinmccubbin on 2010-12-19
I'm a 'new' convert to Linux and have been running Ubuntu 9.10 at home. I recently decided to try and teach myself Python, and bought the Head First Programming book. The programs/code used there use python3, but my ubuntu's standard install is python 2.6.4

I used sudo apt-get install python3 and successfully downloaded/installed python3 and also managed to download/install IDLE(using python3.1) so can now run the basic scripts in the book. Running *IDLE(using python3.1)* tells me that  Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) is running.

Including Tkinter works and as far as I can see runs fine as well, I can make boxes with buttons and sliders etc but now I need to download/install pygame as it is used in many of the more advanced examples.

It would appear from reading the book's O'Reilly site forum [(the thread can be found here)]("http://forums.oreilly.com/content/Head-First-Programming/20635/Confusion-With-Installing-Pygame-And-Python-3/#entry39094") that many folk are having trouble installing pygame for python3  on ubuntu (it isn't available as a download/install in the ubuntu repository).

Following instructions I found there, in a console I've run:
```
sudo apt-get install python3-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libsmpeg-dev python-numpy subversion libportmidi-dev

svn co svn://seul.org/svn/pygame/trunk pygame

cd pygame
python3 setup.py build
sudo python3 setup.py install
```

All of which lines seemed to work and each returns me to the command prompt, although at one point I got this error message:

[I]Warning, some of the pygame dependencies were not found. Pygame can still
compile and install, but games that depend on those missing dependencies
will not run. Would you like to continue the configuration? [Y/n]:[/I]

I answered **yes** and continued.

After finishing, I finally typed python3 and got the >>> prompt, so python 3 is running. I then typed *include pygame* and was told *No module named pygame*

So despite following the above, it seems that I'm still no nearer getting pygame to be recognised by my python3 installation..

If, however I start **IDLE (using python 2.6)** and include pygame it is included.

If at a command prompt I do:[B]apt-cache policy python-pygame
[/B]

I'm told:
[I]python-pygame:
  Installed: 1.8.1release-1ubuntu1
  Candidate: 1.8.1release-1ubuntu1
  Version table:
 *** 1.8.1release-1ubuntu1 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Packages
        100 /var/lib/dpkg/status[/I]


Any thoughts as to where my pygame installation for python 3 'went' would be welcome! 

I'm still unsure 'where' python modules are located in the file system, any advice on that would be appreciated too.

Thank you.

---

### Post by imho74 on 2011-01-02
Colin,

don't know if this works for 9.10 Karmic, too. But that's  the way  I have installed pygame for Python 3 in 10.10 Maverick:

First open the terminal and update your *sources.list*

```
sudo gedit /etc/apt/sources.list
```

with these two lines for *karmic*:

```

deb http://security.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe

```

If you don't use *karmic* replace it e.g. with *lucid* or *maverick*.

If you are from the US you can also use these two lines for your local servers:

```

deb http://security.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe

```

The **us** in the second line makes the difference. :)

After that update and upgrade your  system:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Maybe you have to reboot because it's possible that you have got a new kernel.

Than install all the packages you need to compile pygame for Python 3:

```

sudo apt-get install debhelper libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsmpeg-dev libportmidi-dev sharutils python-numpy python-central quilt libc6-dev libjpeg62-dev libpng12-dev libsdl1.2debian-all libsmpeg0 libx11-6 python3-dev python3-all-dev build-essential

```

Dowload the latest pygame, unpack it and change to the directory:

```
wget http://www.pygame.org/ftp/pygame-1.9.1release.tar.gz
tar xfz pygame-1.9.1release.tar.gz
cd pygame-1.9.1release/
```

The file *setup.py* in this directory is not ready for Python 3 yet. You have to change line 123:

```
gedit setup.py
```

Line 123 before:

```
reply = raw_input('\nNo Arguments Given, Perform Default Install? [Y/n]')
```

Line 123 after:

```
reply = input('\nNo Arguments Given, Perform Default Install? [Y/n]')
```

You know there is no *raw_input* in Python 3 anymore, only *input*.

Now you can compile and install pygame:

```
sudo python3 setup.py install

```

When this is finished you can check if it works:

```

$ python3
Python 3.1.2 (release31-maint, Sep 17 2010, 20:34:23) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
>>> pygame.ver
'1.9.1release'

```

Best Regards
Christian

---

### Post by colinmccubbin on 2011-01-02
Thanks, I got it working, here for anyone else with the same problem is how. :D

Python 2.6.4 is the version shipped with my copy of Ubuntu and pygame is installed to work with it by default.

Since my attempt to add it to python3 'seemed' to have worked, ie no error messages, I wondered 'where' pygame had been installed and found it under my home directory colin@Quiet-box:~$ ie simply below where I was when I opened a command prompt.

I took a look at python 2.6.4 and found that the pygame folder which DID import ok was in a folder with the path: /usr/lib/python2.6/dist-packages/pygame/__init__.pyc


    ```
#Running python at the prompt loads 2.6.4

    colin@Quiet-box:~$ python
    Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15)
    [GCC 4.4.1] on linux2
    Type "help", "copyright", "credits" or "license" for more information.

    >>> import pygame #this works, pygame imports fine!
    >>> pygame
    <module 'pygame' from '/usr/lib/python2.6/dist-packages/pygame/__init__.pyc'>
    >>>

```


So I looked at /usr/lib/python3.1/dist-packages/and found it was just an empty folder.. And guessed that I should have been in the dist-packages folder under the python3.1 path before running the above script.

Moved there and tried again.

The line svn co svn://seul.org/svn/pygame/trunk pygame was a 'you don't have permission to create a folder' error so I tried: sudo svn co svn://seul.org/svn/pygame/trunk pygame which worked.

cd to pygame, #yes, there's a folder there now.

Ran sudo python3 setup.py build #rather than just python3 setup.py build, all went ok.

Ran sudo python3 setup.py install #all went ok.

tried import pygame , IT WORKS!! :D

I've been happily running scripts/programmes using python3.1 and successfully importing and using module pygame. I hope the above makes sense and will help anyone else struggling with the same problem.

---

### Post by joris1977 on 2011-10-15
For anyone struggling with the install of pygame in python3.2...

I found the instructions in this thread working: 

[http://forums.oreilly.com/topic/20635-confusion-with-installing-pygame-and-python-3/page__p__35985__hl__pygame__fromsearch__1#entry35985](http://forums.oreilly.com/topic/20635-confusion-with-installing-pygame-and-python-3/page__p__35985__hl__pygame__fromsearch__1#entry35985)

---

