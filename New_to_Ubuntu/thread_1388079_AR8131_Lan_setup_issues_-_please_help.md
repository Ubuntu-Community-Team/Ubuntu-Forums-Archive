---
title: "AR8131 Lan setup issues - please help"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Bridgette on 2010-01-22
Hi All
 
Im new to the forum( about a week ) and new to Linux, (3 weeks), have a DOS history and come programming history years ago in C and C++, Linux is a steep learning curve for me.
I so far on my system installed KK 9.10 server edition and as I go am reading every tutorial on commnds and working my way through how to do things at the commnd line. I found that the system couldnt detect the onboard LAN card, its a Gigabytes MB with an onboard AR8131 chipset LAN. 
I found the appropriate driver using my windows pc and loaded onto a USB stick, worked out how to mount this, then to copy it into a directory I made and then unpack it. (worked for days on all this)
Now when I do the Make Install I get an error - Makefile:120: *** Complier not found. Stop.
Have done a Less Makefile on the file and im not good enough to determine what the problem is, however the comments in the section im looking at are # pick a compiler, it looks as though its searching through searching for a string
 
if neg (,$(findstring egcs-2.91.66, $(shell cat /proc/version)))
CC :=kgcc gcc cc
else
CC :=gcc cc
end if 
test_cc = $(shell $(cc) --version > /dev/null 2>&1 && echo $(cc))
CC :=$(foreach cc, $(cc), $(test_cc))
CC :=$(firstword $(CC))
ifeq (,$(CC))
$(error Compiler not found)
endif
 
 
in the first line the string its looking for I can find in the version file and the shell command I cant find in the linux command set, well not in the form shell by itself without a switch of some sorts.
From the version file I looked at I think its gcc and even without the shell command I think it defaults to gcc by the code ?
 
Somethings a miss and I cant sort it
 
I have thought of getting a plug in LAN card or going to the desktop version instead of the server version but I hate giving up and this is the best way to learn, once I can at least get it connected to a LAN i can start working on Apache setup
 
Thanks
Bree

---

### Post by NCLI on 2010-01-22
You need to install the latest version of the GNU C Compiler(GCC). This is neccesary for manually building packages in Ubuntu. It should be in the repos. If you don't know how to get it from there, post again, and I'll explain in more detail :)

---

### Post by Bridgette on 2010-01-22
Hi
 
I will need more help, did a find and couldnt find gcc did a sudo apt-get .....  but guess that was incorrect as well, would like some more help on where to find this compiler and is it something that should have been installed with the server software or something that has to be installe later on, 
 
thanks 
Bree

---

