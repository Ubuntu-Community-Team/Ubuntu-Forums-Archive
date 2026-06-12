---
title: "Drivers"
date: 2019-03-25
forum: Networking &amp; Wireless
---

### Post by espectro2 on 2019-03-25
Hello colleagues from the forum
What is the function of this command?
sudo apt-get install build-essential
A very quick question in case a wired or wireless network driver is not recognized is there a default procedure for some initial resolution of Realtek?
Thanks for listening.

---

### Post by jeremy31 on 2019-03-25
That command will install programs necessary for compiling source code.  What realtek wifi do you have?  Please post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; rfkill list
```
Moved to Networking and Wireless

---

### Post by kc1di on 2019-03-25
HI espectro2,

The Package build-essentials is a package that installs a C/C++ build environment so you can build the realtek driver or other programs programed in C or C++ programing language.  It is a Debian package and is not installed by default because not everyone will need it.  The command ```
sudo apt install build-essentials
``` installs that environment to allow you to build the packages you will down load from git hub that will build the driver on your machine.  There is no binary .deb file for this driver at this time. 

Good Luck.

---

### Post by espectro2 on 2019-03-25
jeremy31
jeremy31 i Moderator I am going to connect the machine that is not recognizing the driver and has already resulted in the problem that the connection suddenly drops I just logged in the forum change of page connection falls or know how I will do to post the result I think I will buy USB Adapter 3.0 for RJ45 to send you the command kkk
Thank you for the attention of both of you.
Thankful.



[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=1839") 				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=1839"][B][COLOR=#000000]kc1di 
[/COLOR][/B][/URL]thanks for the explanation would like more to understand about this build-essential and about the package and linux-firmware understand what they are how they work
thankful.


[URL="https://ubuntuforums.org/member.php?u=1839"][B][COLOR=#000000]
[/COLOR][/B][/URL]

---

### Post by kc1di on 2019-03-25
[Here is a document]("https://help.ubuntu.com/community/CompilingEasyHowTo") that may be of help in understanding the build process.  The problem is that realtek does not have pre packaged drivers for ubuntu.
and the drivers have to be built from source code.  Normally most programs are packaged in .deb format Which can be installed with dpkg or apt or via software center. and this takes alot of the work away.  But in some instances like yours.  it will be needful to build the code into installable format first.  and thus the need for the build environment. Hope this helps. 
Jeremy is a expert in realtek drivers so follow his advice. 
Good Luck and Happy learning.

---

