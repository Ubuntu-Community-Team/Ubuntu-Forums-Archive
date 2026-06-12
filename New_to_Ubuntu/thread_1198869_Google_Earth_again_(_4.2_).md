---
title: "Google Earth again ( 4.2 )"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by freeediver on 2009-06-28
I installed GE by following these inst.
[https://help.ubuntu.com/community/GoogleEarth#Installation](https://help.ubuntu.com/community/GoogleEarth#Installation)
using:
 sudo apt-get install googleearth
There are no follow on instructions for the installation using that command.
It looks like GE downloaded but now I can't find it or any way to run it, it does not show in Apps>internet.
I have also found it in package manager and tried marking it for re-install, that did not work either.
Any ideas what to do now, GE is in by box but I can't get it to install/run. How can I now get rid of it if I need to start over.
I have tried to find the program location without much success,
where could it be hiding and if I find it how do I dump it so I can start over clean?

Thanks

---

### Post by PureLoneWolf on 2009-06-28
Run a terminal and type

googleearth %f

That is the command in my menu icon

Hope that helps

---

### Post by beerrrttttiiiiillllll on 2009-06-28
**This is the process in terminal Ubuntu 9.4 64bit after try to instal google earth linux.bin**

marie@marie-laptop:~$ cd Desktop
marie@marie-laptop:~/Desktop$ sudo chmod a+x GoogleEarthLinux.bin
marie@marie-laptop:~/Desktop$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11733.9347..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
marie@marie-laptop:~/Desktop$ 

**What am I doing wrong?**

---

### Post by freeediver on 2009-06-28
Thanks
I tried that command and GE opens then instantly crashes my system.
Next question, How do I dump GE to start over?
I did find quite a few GE files using the search function, both 4.2 & 4.3 & who knows what other versions are hiding, I have never had this problem before. 
I found it using : Places>Computer>Filesystem>search

I just completed a fresh install of Hardy, prior to the new install GE 4.2 work very well.
Time to dump what I have and start over, is there an easy way to dump GE using terminal
considering the install method I used?
Thanks

---

### Post by QIII on 2009-06-28
sudo dpkg --purge googleearth

---

### Post by Acradon on 2009-06-28
I got the installation working, but when I open the program there is no world to be seen. I tried to configure the server, but the window opens only for a split second before disappearing again. Does anybody know why this is?

---

### Post by HotShotDJ on 2009-06-28
A couple of ideas that may help you:  Try the [Medibuntu]("http://www.medibuntu.org/") version of Googleearth.

Make sure you disable "Atmosphere" under the "View" menu in Googleearth.

---

