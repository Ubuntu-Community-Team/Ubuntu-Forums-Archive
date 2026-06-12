---
title: "GoogleEarth Installation: A Step by Step Guide"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by wijit on 2009-12-01
Having a big problem with installing GoogleEarth on Ubuntu (Karmic) drives me doing a research for both solving the problem and find the best way of installation. There are more than 25,000 topics in the Absolute Beginner Talk forum. About 200 of all relate to GE. Only 4 refer to the package googleearth_5.0.11733. ... Within the 4, [http://ubuntuforums.org/showthread.php?t=1198869](http://ubuntuforums.org/showthread.php?t=1198869) refers to GE installation and touches the use of "googleearth-package". None provides a step by step guide on installation. I'd like to contribute the community by telling out my experience on this issue. The whole procedure is very easy so just a 1 2 3 is enough for the explanation. What I did on 2 of my notebooks are generally the same but with slightly different results. Here's the details:
1. Install package "googleearth-package" using any method. Synaptic seems easy for beginners than apt-get which has to do in Terminal (command prompt). However, next steps after this need Terminal. Hench, start the whole thing in Terminal is preferably adviced.
Code:
sudo apt-get install googleearth-package
2. Next, depending on whether you have downloaded the file "GoogleEarthLinux.bin", the command will try to look for the file on your file system or download if not found before create a Debian package. In Terminal,
Code:
make-googleearth-package
On my Karmic notebook which was upgraded and previously has GE installed but crashed after the upgrade, the command uses existing "GoogleEarthLinux.bin" to create the googleearth_5.0.11733.9347+0.5.6-1_i386.deb package. You will find the package in the directory you launched the command. However, on the other machine which has freashly installed Jaunty, the command downloads the bin file and stops after download finished with a message unknown version of the target file and suggested to use - - force to build the package. If you get the same result as this just run the command again with - - force option:
Code:
make-googleearth-package - - force
As a result, I've got slightly elder version, googleearth_5.0.11733.9347+0.5.4.1-1_i386.deb instead.
3. The final step, install the package you've built with "dpkg" which as simple as:
Code:
sudo dpkg -i <the Debian Package name>

After the process finished, you will find Google Earth launcher under the Internet menu where you can click and run. I have no problem with the Jaunty notebook. However, I have a file permission problem on my Karmic one. The program runs:P:P only with sudo. The problem inherits from Jaunty and I have had no idea on how to solve. Please go to [http://ubuntuforums.org/showthread.php?t=998345](http://ubuntuforums.org/showthread.php?t=998345) for problem solving.

---

### Post by donaldshelton on 2010-02-16
Thanks for this post.  It actually worked for me!!

All I need to do is print these instructions for later use!!!

---

### Post by mgmiller on 2010-02-16
google earth is in the medibuntu repository.  Once medibuntu is in, google earth is easily installed from synaptic.  You should use medibunto to get the win32(64) codecs and other stuff any way.

Just go here and follow the instructions for adding the repository.  It's just a copy paste of one phrase into terminal, everything else is done in synpatic if you like after that.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ankspo71 on 2010-02-16
Hi,
Google Earth can be installed by medibuntu, as said above, which I have done many times, but the downloaded bin file can easily be installed by the terminal too. I think it can also be installed by ubuntutweak (not sure about that one because I don't use ubuntu tweak.)

I currently have version 5.1.3533.1731 installed in Ubuntu 10.04 (lucid testing release), downloaded from the Google Earth site.

The command I use is either 
sh GoogleEarthLinux.bin
or 
bash GoogleEarthLinux.bin

I find it better to not use sudo during installation, because it seems to work better if installed to my home directory. (note this only applies to googleearth)

In Jaunty, I preferred the medibutu google earth, but since Karmic and Lucid, I prefer the version directly from google.

Also, to avoid using the terminal, someone might still be able to right click on the bin file and select "open with other application", then "use custom command", then type sh or bash into the box, then click "open". I did that for other things in the past.

Hope this helps, and I wish I would have known you needed help with this earlier ;)

---

