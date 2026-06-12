---
title: "Compiling"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by lile001 on 2011-07-18
OK, I am needing to compile something.  The specific problem I am having (a bug in a tablet driver) is probably semi-irrelevant, but I have been told I need a new version of a driver that is not included in the latest Ubuntu release. It needs to be compiled from the source.  Here is a link to the source that I need to compile:

> That was fixed fairly quickly so I think xf86-input-wacom-0.10.8 or later has the fix:  [http://sourceforge.net/projects/linu...6-input-wacom/]("http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/")

In other words you'll have to upgrade your xf86-input-wacom from 0.10.5 to 0.10.8 or later.

I have started going through the steps outlined here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Which swiftly begins to fail since I have only a vague idea of what I am doing.  

This step worked OK:  
```
 sudo apt-get install build-essential checkinstall
```

as did this one:

```
sudo apt-get install cvs subversion git-core mercurial
```

This step gives an error code when I substitute my name for $USER:

```
sudo chown $USER /usr/local/src 
chown: missing operand after `/usr/local/src'
```
So I changed the permissions in this directory using Nautilus

This step seemed to work OK:
```
sudo chmod u+rwx /usr/local/src
```

I was able to download and expand the referenced tarball into usr/local/src. 

There is a readme in the tarball that suggests I try:
```
$ ./configure && make
``` which informs me there is no such file or directory. 

The next step in the HOWTO talks about resolving dependencies, and it reads like complete gibberish to me.    I am sure it is meaningful if someone already knows what it says, but I can't get anything out of it.  

I need to get this tablet running because of a handicap that makes it painful to use a regular mouse.  We are probably just a step or two away from getting it compiled.  Can someone help me figure out what to do next?

---

### Post by lile001 on 2011-07-18
Blundering around, I finally got configure to run, with the output attached.  Apparently I need a bunch of stuff that isn't here (as expected), however I have yet to decipher what this output is telling me to do.

---

### Post by lile001 on 2011-07-18
The first two missing packages are apparently:

No package 'xorg-server' found
No package 'xproto' found

Trying to install these using apt-get results in "Unable to locate package", so apparently that isn't how to proceed.

---

### Post by oldos2er on 2011-07-18
You may need to refresh your sources.list by running ```
sudo apt-get update
``` if you haven't already done so. Which version of Ubuntu are you using?

Sometimes the package names ./configure is looking for are slightly different than the package names in the repositories, for example 'xorg-server' which doesn't exist as you noticed, but there is a package named 'xserver-xorg-dev' which I'm pretty sure is what you're needing (always look for -dev packages for the development files you need to compile code).

Using 'apt-cache search [search term]' to find the other packages you need, try installing 

x11proto-core-dev
x11proto-dmx-dev
xserver-xorg-dev
libxext-dev
x11proto-kb-dev
x11proto-input-dev

then retry ./configure

---

### Post by lile001 on 2011-07-18
Thanks!  That worked to a point.  The last few lines of teh output this time are:

```
Package xorg-macros was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-macros.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-macros' found
checking for rint in -lm... yes
checking for XORG... yes
checking if RANDR is defined... yes
checking for X11... no
configure: error: Package requirements (x11 xi xrandr) were not met:

No package 'xi' found
No package 'xrandr' found
```

I was able to identify a package that contained "xrandr", however apparently xi is used in thousands of programs, because the output is many pages long.  Somewhere in that gibberish is the package I need to install, but which one?  Output is attached, if it is any help.

---

### Post by lile001 on 2011-07-18
Attachment is too large to upload.  150K.  Anything in there I should look for, particularly?

---

### Post by lile001 on 2011-07-18
I found a list on this page

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dependencies](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dependencies)

that seems to list the packages to install.

---

### Post by decoherence on 2011-07-18
Same as what you did to fix the error prior to this -- install the development headers for the packages it complains about. in this case probably things like

libx11-dev
libxrandr-dev
xutils-dev
libxi-dev

After this, it may spit out even more dependencies. It's basically an exercise in translating between how the packages in the error messages are named and how repository packages are named.

Like old oldos2er said, look for packages ending with '-dev'. You won't always find them because they often preceded by 'lib' in the repository so that's another thing to check. libxi-dev, above, is a good example -- that will fix the "No package 'xi' found" error.

Aside from that, you can often get the answer just by pasting each package error in to google.

Good luck!

---

### Post by decoherence on 2011-07-18
> **lile001 said:**
> I found a list on this page

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dependencies](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dependencies)

that seems to list the packages to install.

Yep, that's what you need!

---

