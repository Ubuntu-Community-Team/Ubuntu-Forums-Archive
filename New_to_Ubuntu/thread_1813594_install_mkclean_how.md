---
title: "install mkclean?? how??"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Russell Burrows on 2011-07-28
I downloaded mkclean and extracted it but then I have no idea what to do next??

Thank you.

---

### Post by jerrrys on 2011-07-29
how bout a link to the download site you used and what package you downloaded.  im finding more than one source.

---

### Post by Russell Burrows on 2011-07-29
[http://matroska.org/downloads/mkclean.html](http://matroska.org/downloads/mkclean.html)

version 8.4

---

### Post by jerrrys on 2011-07-29
ok, this is a source package.  you got some work cutout for you, but not to worry,  you don't have to be a rocket sciences to figure it out.

[https://help.ubuntu.com/community/InstallingSoftware#Source%20or%20Binary?](https://help.ubuntu.com/community/InstallingSoftware#Source%20or%20Binary?)

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=source+package+install+how+to&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=source+package+install+how+to&sa=Search&cof=FORID:9#926)

[http://matroska.org/downloads/linux.html](http://matroska.org/downloads/linux.html)

and its 2am here, time for bed.  got any questions?  i will check back in tomorrow.  good luck

---

### Post by kimda on 2011-07-29
THis is a post of someone else compiling this program. It might help you. 

[http://ubuntuforums.org/showthread.php?t=1489706](http://ubuntuforums.org/showthread.php?t=1489706)

---

### Post by vhook on 2011-07-29
This is done from the command line:

After you extract the archive, cd to the directory (i.e. cd ~/Downloads/mkclean-0.8.4)
Then do the following
```

sudo apt-get install build-essential checkinstall
./configure
make -C mkclean
sudo checkinstall -y

```

---

### Post by benlebowski on 2013-04-17
> **vhook said:**
> This is done from the command line:

After you extract the archive, cd to the directory (i.e. cd ~/Downloads/mkclean-0.8.4)
Then do the following
```

sudo apt-get install build-essential checkinstall
./configure
make -C mkclean
sudo checkinstall -y

```

thanks vhook, it worked with your command :)
however, how do I compile mkwdclean ?
thanks

---

### Post by overdrank on 2013-04-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

