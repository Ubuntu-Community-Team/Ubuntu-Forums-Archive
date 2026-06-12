---
title: "Intel pro/wireless 2915 problems"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by kohlerbn on 2006-08-29
I followed this post 

[http://ubuntuforums.org/showthread.php?t=45048&highlight=intel+pro%2Fwireless+2915](http://ubuntuforums.org/showthread.php?t=45048&highlight=intel+pro%2Fwireless+2915)

and got all the way down to the make part of the ieee80211-1.0.3 before it gave me this error: 

make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-10-386/build M=/home/brenton/downloads/ieee80211-1.0.3 MODVERDIR=/home/brenton/downloads/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/brenton/downloads/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/brenton/downloads/ieee80211-1.0.3/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/brenton/downloads/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2


can anyone help?

---

### Post by funchords on 2006-08-29
I'm not sure this is it, but ...

**sudo make**

---

### Post by kendals on 2006-08-29
EDIT: Found a solution via [http://ubuntuforums.org/showpost.php?p=1081852&postcount=6](http://ubuntuforums.org/showpost.php?p=1081852&postcount=6) :)

That thread actually, will solve the problem. I also did a fresh install. Yay! So happy now :)

---

### Post by kohlerbn on 2006-08-30
I tried 
  sudo make


and it still gave me the same error. any other ideas?

---

### Post by kendals on 2006-08-30
I just grabbed the network manager app from Synaptics, installed it, and didn't need to use the Intel drivers at all (hence didn't need to make them). See if that works for you?

Mind you, would be nice to know if my 'make' command works or not :P

---

### Post by kohlerbn on 2006-08-30
Yeah I already hae network manager... but I still need to install ipw2200... I figured out that the make command doesn't work on any program I try to make. Any suggestions on how to fix that?

---

### Post by funchords on 2006-08-30
linux-headers-2.6.12-10-386 is pretty old.  With my limited experience, it's hard to know exactly where make is picking that up.  

The version I expect to see is the version that matches the results of the **uname -r** command.

---

### Post by kohlerbn on 2006-08-30
thanks for all your help everyone but i think i found the problem... I am running a very old version of UBUNTU... I think I am going to upgrade and then try stuff out.

---

### Post by kendals on 2006-08-30
Haha, good luck then :P Let us know how you go.

---

