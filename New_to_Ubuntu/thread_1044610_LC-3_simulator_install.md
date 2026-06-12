---
title: "LC-3 simulator install"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by DaEMoN390 on 2009-01-19
I was having a problem installing a LC-3 simulator for Hardy. I tried Simplc and that installed correctly but, the UI bash command was not recognized. The terminal version ran fine. Next I tried to run LC3Tools but, I couldn't get the configure file to even run. I know there is probably a more elegant solution but, what I had to do was pull some of the bin files off of my school's servers. If anyone else had this problem with Simpl, hope this helps.

---

### Post by bragr on 2010-07-10
Sorry for the bump, but I was having trouble with this as well, and I know that some others were as well, so I though I would share.
I got the official LC3 program to compile and run on 10.4. Here is how I managed to do it:
[LIST=1]
[*][Get the latest version of LC3 here]("http://highered.mcgraw-hill.com/sites/dl/free/0072467509/104652/lc3tools_v12.zip")
[*]Install 2 dependencies, specifically Flex and tcl/tk. So: ```
sudo apt-get install tk8.5 flex
```
[*]Configure. You will need to make the configure script exicutable first. ```
chmod u+x ./configure
``` Then you need to run it, optionally you can set the location to install the files in. I like to install all software that didn't come in a .deb in /opt so for me:  ```
./configure --installdir /opt/lc3
``` For the defaults you can just run ```
./configure
``` 
[*]Now run make and it should compile for you. You will probably get a few pages of warnings, ignore them, it is normal. Optionally you can run "make install" to install it (in /opt/lc3 in my case) or you can just leave it where it is and run it out of that directory.
[*]If it won't make for you, try opening up the Makefile, find the line that says "OS_SIM_LIBS = -lcurses" (line 41 for me) and change it to "OS_SIM_LIBS ="
[*]Run it! You can run the command line version with lc3sim, or the GUI version with lc3sim-tk. You will need to compile the assembly files with lc3as.
[/LIST]



As far as SimpLC, I could never get it to compile, but I do know that in order to enable the graphical component, you need to install some QT libraries. I was able to install them with ```
sudo apt-get install libqt3-mt-dev
``` but then I got stuck with everyone's favorite "ERROR 1".

---

