---
title: "Downloaded files"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by vivek40 on 2010-03-26
Hii ! 
I have used Synaptic for installing and uninstalling plenty of softwares . When it installed something for the first time, I saw synaptic downloading some files before installing them. Then later after I uninstalled them and tried instaling them again for whatever reason, Synaptic just installed the required packages without having to download anything. Does that mean that even after the uninstallation , the specific files were stored somewhere in my computer , and when asked to install again, synaptic just used them , without having to download anything.
 If this is the case, should I not try to manually go and delete those files , so that they dont eat up the memory. 
Any help would be really appreciated
Regards
Vivek

---

### Post by sandyd on 2010-03-26
> **vivek40 said:**
> Hii ! 
I have used Synaptic for installing and uninstalling plenty of softwares . When it installed something for the first time, I saw synaptic downloading some files before installing them. Then later after I uninstalled them and tried instaling them again for whatever reason, Synaptic just installed the required packages without having to download anything. Does that mean that even after the uninstallation , the specific files were stored somewhere in my computer , and when asked to install again, synaptic just used them , without having to download anything.
 **If this is the case, should I not try to manually go and delete those files , so that they dont eat up the memory. **
Any help would be really appreciated
Regards
Vivek
1. They are stored in /var/cache/apt/archives
2. There is a difference between memory and hard disk space. Memory usually refers to volatile memory (RAM)[Random Access Memory], while, well hard disk space refers to storing stuff on your hard disk.
The data in the memory (RAM) is wiped out when the computer is shut down, so there is no reason to have to delete files in it.

3. clean the files by
```

sudo rm /var/cache/apt/archives/*.deb
```

---

### Post by Gixxy on 2010-03-27
Most packages are small... if you eat through your entire disk installing stuff I'd suggest help for your packrat syndrome. :D

You can use 
```
sudo apt-get autoremove
```
to cleanup unused or erroneous packages.

For the most part I would not worry about eating disk space from installing programs.

---

### Post by Rocket2DMn on 2010-03-27
Rather than manually deleting the deb files, you can also have a package manager do it for you:
```
sudo apt-get clean
```
In Synaptic, you can do ot Settings->Preferences and click *Delete Cached Package Files*.  Here you can also configure whether packages are stored on disk after installation.

---

### Post by vivek40 on 2010-03-27
Thanks a lot guys! I will do that Rocket, the easy way.. and yeah Gixxy! Packrat syndrome-- nice term.. can use it for my presentations .. lol.. !
Thanks!!!!!!!:-)

---

### Post by vivek40 on 2010-03-27
And yes Thanks Carlee! By memory I meant the hard disk space only.. Just used the wrong term. However Thanks a lot!

---

