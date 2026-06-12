---
title: "Madwifi build problem"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by Raznog on 2007-01-26
So i've done everything it said to do at the madwifi site...
I am using dapper

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

#first thing i do is 
cd /madwifi  
#(to get into the mad wifi directory)

ifconfig ath0 down
ifconfig wifi0 down

cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh /lib/modules/
cd ..

#I do this one and it says its going to ask me if i want to delete the old modules(which it doesnt do) so i proceed to the next step

make

#This is where it tells me bash: make: command not found. any help would be greatly appricated. BTW im using a 17" Macbook pro...

---

### Post by spd106 on 2007-01-27
Try running **sudo apt-get install build-essential** to get the tools you need.

---

### Post by Raznog on 2007-01-27
ok thanks alot... that got me to the next step =D but now it gives me a new error after i say make it now says

/bin/sh: line 0: cd: /lib/modules/2.6.15-23-386/build: No such file or directoryMakefile.inc:89: *** /lib/modules/2.6.15-23-386/build is missing, please set KERNELPATH.  Stop.

any help here? thanks alot =D

---

### Post by geekgod on 2007-01-27
I had nothing but nightmares with madwifi and 5.10 so I upgrader to 6.10 and madwifi was built in no setup required:)

---

### Post by spd106 on 2007-01-27
You need to create a symlink to the kernel sources, I think this will work. ```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```

---

### Post by Raznog on 2007-01-28
nope it still says

/bin/sh: line 0: cd: /lib/modules/2.6.15-27-386/build: No such file or directoryMakefile.inc:66: *** /lib/modules/2.6.15-27-386/build is missing, please set KERNELPATH.  Stop.

---

### Post by spd106 on 2007-01-28
Check that you have the kernel headers installed. You can find them in Synaptic, the package will be called linux-headers-2.6.15.27.

---

### Post by Raznog on 2007-01-28
That did it! thanks alot =D

---

### Post by Ephilei on 2007-03-19
Thanks! That solved the problem, but now there's something else. The makefile references links in the headers directory that are broken, for instance, $(uname -r)/arch/i386/makefile where arch/ is broken.

---

