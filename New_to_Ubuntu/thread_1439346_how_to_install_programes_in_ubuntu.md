---
title: "how to install programes in ubuntu"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by medtahan on 2010-03-26
:P how to install programes in ubuntu
in windows by run a file called setup.exe
what in ubunt ???
 
 
and what is the command line??     how to use it ???

---

### Post by sxmaxchine on 2010-03-26
look in the software centre and when looking for software on the interweb ubuntu uses .deb not .exe. deb files work very similar to .exe files

---

### Post by the yawner on 2010-03-26
Also, please note that unless you're using a certain program, you won't be able to install programs made specifically for Windows on an Ubuntu machine. Just try to explore what programs are available on the Software Center first before you go about downloading .deb files here and there.

---

### Post by sxmaxchine on 2010-03-26
forgot to tell you that you can use the command line by openng the terminal,
you can install a program through command line by opening terminal and typing this:
sudo apt-get install program name

were i wrote program name you type the name of the program

---

### Post by medtahan on 2010-03-26
> **sxmaxchine said:**
> look in the software centre and when looking for software on the interweb ubuntu uses .deb not .exe. deb files work very similar to .exe files
 
 
and what if i want to install program from other website
for ex. i use phpmaker to generate php sql pages in windows
 
sorry my english not good
my first lang. is arabic

---

### Post by scorpious on 2010-03-26
> **medtahan said:**
> 
what is the command line??

The command line (or terminal) is like the console that you find in Windows.
you need it to install stuff.

> **medtahan said:**
> 
how to install programes in ubuntu

Find the programme you want to install.
Open up the terminal ( Applications - system - terminal)
type Sudo apt-get install (thing you want to install)

eg if I'm installing clive I type
"sudo apt-get install clive" 

The pc does the rest

---

### Post by medtahan on 2010-03-26
cool   thank you my friends

---

### Post by sxmaxchine on 2010-03-26
windows programs (.exe) will not run on ubuntu, however you can get it them to work by installing them through wine: you can find out more about wine [here]("http://www.winehq.org/")

after wine is installed just find the .exe file and open it like you would on windows. however i should mention that not all programs will work properly through wine.

hope i answered your queston right

---

### Post by mastablasta on 2010-03-26
In the menu you will find software center. In it there are many programmes.
 
You can then do it via command line if oyu prefer typing. 
 
You can also find programme on the internet with .deb file extension, donwload it to oyur ocmputer and double click it just like .exe in windows. yay!

---

### Post by yasir.elsharif on 2010-03-26
salam medtahan,
do you use phpmaker? I love this program, I couldn't install it on wine/ubuntu at all. Please tell me if you succeeded.
Yasir

---

### Post by Wataru8675 on 2010-03-26
> **medtahan said:**
> and what if i want to install program from other website
for ex. i use phpmaker to generate php sql pages in windows
 

A lot of the time, you won't be able to use the exact same programs in Ubuntu that you used in Windows.  It doesn't look like PHPMaker has Linux compatibility (as you can see [here,]("http://www.hkvstore.com/phpmaker/download.asp") it only mentions Windows systems that you can install to).  This means you'll probably have to find an alternative program to use on Linux, or you can dual boot (aka, have both Windows and Ubuntu on the same computer) and switch over to Windows when you need to use PHPMaker.

---

### Post by yasir.elsharif on 2010-04-06
But don't forget wine. where you can run many windows applications on linux.
and the other way is using vertual machine like vertual box.

---

### Post by Drenriza on 2010-04-06
Installing programs/software in ubuntu can be done in driffent ways.

You can install with a graphical user interface. Using a package manager.

you can install from the debian apt-get package manager. Using reposatories.
```
apt-get package-name install
```

you can install a tarball package. Instead of an .exe extension they are called .tar.tgz / .tar.gz2 / .tar / .zip

---

