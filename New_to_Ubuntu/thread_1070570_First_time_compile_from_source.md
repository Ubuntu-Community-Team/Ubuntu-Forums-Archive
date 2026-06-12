---
title: "First time compile from source"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by spongemonkey on 2009-02-15
I decided I'd try compiling a few things from source, the programs I've tried so far are VLC and Rhythmbox.

I ran

```
sudo apt-get source rhythmbox
sudo apt-get build-dep rhythmbox
```

then cd to the relevant dir and

```
sudo ./compile
sudo make
sudo make install
```

for vlc I then had to do

```
sudo /sbin/ldconfig
```

for it to work, doing this for rhythmbox I get a load of *Rhythmbox-WARNING* and *Rhythmbox-CRITICAL* messages...

Is this all there is to it? It seems strange that I have to download 100s of MB of stuff for *apt-get build-dep* as well as the source code, whereas its only a few MBs via Synaptic. Is there something I should be doing to clean up my installs?

Thanks

---

### Post by cmnorton on 2009-02-15
make clean 

if the makefile was set up correctly, so it will clean up left over stuff.

---

### Post by mc4man on 2009-02-15
If you are using **8.10** then a change was made to apt where all build-dep acquired packages are now marked as automatically installed

If you run this they will be removed, (*though I'd double check the list first before choosing y*

```
sudo apt-get autoremove
```

For info's sake if you wanted build-deps not marked as such so not to clog up the autoremove list (useful when you intend to keep building apps, same or otherwise

You'd do it this way 
Ex. mplayer

```
sudo apt-get build-dep mplayer -o APT::Get::Build-Dep-Automatic=false 
```

Edit: also note that when you use "make install" then you don't usually want to delete your build folder so you can run 
```
sudo make uninstall
```

from the build folder prompt to remove the app.

Running "make clean" at the build folder prompt only sets the compile back to the way it was before you ran "make" (will also make the command "sudo make uninstall" not work.


Also keep in mind that many apps don't need to be installed to run or test before installing. At the prompt where you ran the configure, make, you can just go ./<app exec name>

Ex. mplayer

```
doug@doug-desktop:~/mplayer7/svn$ ./mplayer
MPlayer SVN-r28470-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
Usage:   mplayer [options] [url|path/]filename
```

For vlc it would be ./vlc

---

### Post by spongemonkey on 2009-02-15
So to clarify, downloading 10x more data to compile from source is usual? What's the deal with all that extra downloading over Synaptic? What happens to it all after I've create the binary? Not sure I entirely followed mc4man's post...

Was my approach more or less correct? Any idea what the errors with rhythmbox are about?

Cheers

---

