---
title: "How to compile and install driver?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by coldfinger on 2010-05-20
I just installed Ubuntu 10.04. This is my first Linux experience.
 
I'm trying to load drivers for my D-Link dwa-130 usb wireless adapter. I downloaded the linux driver files from D-Link, but haven't been able to compile and install. I have some basic questions:
 
- Do the files have to be in a specific directory when I compile?
- Which files do I compile (there are several to choose from)?
- After I compile, what do I do next?
 
I would greatly appreciate any help.
 
Thanks,
coldfinger

---

### Post by VeeDubb on 2010-05-20
1. Install all the stuff you need for building/compiling software.

```
sudo apt-get install build-essential
```

2. Unzip the files to somewhere convenient.

3. Open a terminal, and CD to the directory where you unzipped the files.

```
cd /path/to/the/files
```

4. Compile the kernel module (it's not really a "driver" in the windows sense)

```
make
```

5. Install the kernel module

```
sudo make install
```


That's really about it.

---

### Post by coldfinger on 2010-05-20
Thanks for the reply.  So I don't have to specify any filenames or parameters for the "make" command?
 
I tried something like that last night, but I think I got a permission error when I attempted the make.  Seems like there was an error when the process attempted to create a directory.  
 
I'll try again tonight.

---

### Post by VeeDubb on 2010-05-20
1. No, you absolutely do not need to specify files when using the make command, unless you're doing something unusual.

2. There's a very good chance that you got error when you ran the make command before, because you had never installed the build-essential package.  It installs a whole lot of packages and tools that are required for building software.  Also, it could be that when you ran the "sudo make install" command. you left off the sudo.

3. If you've already tried and failed, you may want to delete the files you extracted and extract them again.

---

### Post by Thelazygoose on 2010-05-20
i am having the exact same problem with kubuntu 10.04 and the dwa-130c, i have been trying for a while to get it to work with no method working, i tried ndiswrapping the windows drivers (i however have very little experience with ndiswrapper and could have messed it up), but i am very desperate at this point.

if anyone has any help or if the instructions posted above work out i would really appretiate it if someone could post the solution.

Thanks very nuch for your help

---

### Post by ryan858 on 2010-05-20
Can we get a link to the download so we can see what you're working with here?

You said something about a permission error... Try this:
```

cd *<dir of extracted files>*
chmod +x make

```You might also need to configure the build before using make, by using
```
./configure
```Also check to see if there are any INSTALL or README files, for instructions.

Most programs are compiled via
```
./configure && make && sudo make install
```but this being a kernel module, and thus *not* "most programs" (in fact not even a program), it could be different.

---

### Post by VeeDubb on 2010-05-20
good call adding ./configure

It's un-needed for a lot of stuff these days, so it's easy to forget.

As far as chmodding "make," that's not going to get your anywhere.  Make is a system command that is installed with the build-essential package, and should never be found in the directory your source is in.

---

### Post by ryan858 on 2010-05-20
> **VeeDubb said:**
> 
As far as chmodding "make," that's not going to get your anywhere.  Make is a system command that is installed with the build-essential package, and should never be found in the directory your source is in.
Hmm, I never really thought about it, lol. Thanks for the info.

I'm a n00b <.<

---

### Post by coldfinger on 2010-05-21
The link to the dwa-130c driver is:  [http://www.dlink.com/products/?tab=3&pid=DWA-130&rev=DWA-130_revC](http://www.dlink.com/products/?tab=3&pid=DWA-130&rev=DWA-130_revC) .  I downloaded the linux driver v 0.06 dated 11 November 2008.
 
Didn't get time to try the suggestions that VeeDub made, but will do so this evening.
 
So what does ./configure typically accomplish?
 
 
Thanks,
Coldfinger

---

### Post by coldfinger on 2010-05-21
When I tried running the ./configure command, got this error:  bash: ./configure:  No such file or directory.  

When I attempted to install the build-essential package, the system attempted to install several additional packages.  When I proceeded with the install, I got several error messages indicating none of the package files were found on the 10.04 CD.  
What am I doing wrong?
 

I attempted to do the make anyway, and I got some compilation errors:
 
 
> Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/jettdg/dwa_130/ieee80211/ieee80211_rx.o
  CC [M]  /home/jettdg/dwa_130/ieee80211/ieee80211_softmac.o
  CC [M]  /home/jettdg/dwa_130/ieee80211/ieee80211_tx.o
  CC [M]  /home/jettdg/dwa_130/ieee80211/ieee80211_wx.o
/home/jettdg/dwa_130/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_get_encode_ext_rsl’:
/home/jettdg/dwa_130/ieee80211/ieee80211_wx.c:846: warning: suggest parentheses around operand of ‘!’ or change 
‘&’ to ‘&&’ or ‘!’ to ‘~’
  
CC [M]  /home/jettdg/dwa_130/ieee80211/ieee80211_module.o
/home/jettdg/dwa_130/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rsl’:
/home/jettdg/dwa_130/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named 
‘hard_start_xmit’
make[2]: *** [/home/jettdg/dwa_130/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/jettdg/dwa_130/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2

Am I getting this error because of the problems installing the build-essential package, or does this imply source code errors in the IEEE80211_* files?



I'm not making much progress.  Wondering if I should abandon the linux driver and try Ndiswrapper with the XP drivers.

---

### Post by coldfinger on 2010-05-25
Tried installing the build-essential package so I could compile drivers for my d-link dwa-130c, but got 'file not found ...' errors when attempting to load the package and its dependencies.  A coworker mentioned that I might not have a repository enabled.  If this is the case, which repository do I need to enable, and how do I do it?
 
Additionally, when I tried to run ./configure, I got a bash error.  Is this because I don't have build-essential installed?
 
Thanks,
coldfinger

---

