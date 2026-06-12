---
title: "I screwed up when installing brother printer driver."
date: 2009-10-30
forum: New to Ubuntu
---

### Post by lenich89 on 2009-10-30
Hello, and thanks to everyone here at Ubuntu for all the hard work with no pay. I am not that great at linux, used it a few years ago but now i am trying out 9.10 and so far i really like it and replaced my vista and im not looking back. I have a fujitsu t4220.

I installed my printer yesterday, a brother hl-2070n but i didnt really follow a guide i made a noob mistake and just installed a bunch of stuff and now whenever i do basically anything it tries to install the driver. I tried to get rid of it in synaptic but i couldn't delete it. Im sure its a simple fix and after a few months of using linux im going to feel like an idiot for this post but ne way here are a couple of errors i get. 

john@john-laptop:~$ sudo dpkg --configure -a
Setting up cupswrapperhl2070n (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64: cannot create /usr/share/cups/model/HL2070N.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/HL2070N.ppd': No such file or directory
dpkg: error processing cupswrapperhl2070n (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl2070n

I get this one after i try and install a program using the software center. it says it fails to install but it is just failing to install this package that gets added onto everything i do. i only included the part that fail due to this driver. 

 
Processing triggers for desktop-file-utils ... 
Setting up cupswrapperhl2070n (2.0.1-2) ... 
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64: cannot create /usr/share/cups/model/HL2070N.ppd: Directory nonexistent 
 * Restarting Common Unix Printing System: cupsd 
   ...done. 
cp: cannot stat `/usr/share/cups/model/HL2070N.ppd': No such file or directory 
dpkg: error processing cupswrapperhl2070n (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up liblzma0 (4.999.8beta-0ubuntu2) ... 
 

Any help will be greatly appreciated. 
Thanks,
John (Linux noob)

---

### Post by lenich89 on 2009-10-31
idk wat proper time is to bump but bump?

---

### Post by pootan on 2009-10-31
I'm just a noob myself but maybe you try to create this set of folders manually in /user/local     Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64    and then try running it again.  It's worked for me before with a similar installation error.

---

### Post by PorkyPie on 2009-10-31
> **lenich89 said:**
> Hello, and thanks to everyone here at Ubuntu for all the hard work with no pay. I am not that great at linux, used it a few years ago but now i am trying out 9.10 and so far i really like it and replaced my vista and im not looking back. I have a fujitsu t4220.

I installed my printer yesterday, a brother hl-2070n but i didnt really follow a guide i made a noob mistake and just installed a bunch of stuff and now whenever i do basically anything it tries to install the driver. I tried to get rid of it in synaptic but i couldn't delete it. Im sure its a simple fix and after a few months of using linux im going to feel like an idiot for this post but ne way here are a couple of errors i get. 

john@john-laptop:~$ sudo dpkg --configure -a
Setting up cupswrapperhl2070n (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64: cannot create /usr/share/cups/model/HL2070N.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/HL2070N.ppd': No such file or directory
dpkg: error processing cupswrapperhl2070n (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl2070n

I get this one after i try and install a program using the software center. it says it fails to install but it is just failing to install this package that gets added onto everything i do. i only included the part that fail due to this driver. 

 
Processing triggers for desktop-file-utils ... 
Setting up cupswrapperhl2070n (2.0.1-2) ... 
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64: cannot create /usr/share/cups/model/HL2070N.ppd: Directory nonexistent 
 * Restarting Common Unix Printing System: cupsd 
   ...done. 
cp: cannot stat `/usr/share/cups/model/HL2070N.ppd': No such file or directory 
dpkg: error processing cupswrapperhl2070n (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up liblzma0 (4.999.8beta-0ubuntu2) ... 
 

Any help will be greatly appreciated. 
Thanks,
John (Linux noob)

Since I use a brother printer, I'll try to help:

[LIST=1]
[*]Go to System -> Administration -> Synaptic Package Manager, and search and mark for complete uninstallation: cupswrapperhl2070n (if you can't do this, you probably will need to run ```
sudo apt-get remove cupswrapperhl2070n
```
[*]Dowload the official drivers from Brother: [LPR driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2070nlpr-2.0.1-1.i386.deb&lang=English_lpr") [CUPSWrapperr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2070N-2.0.1-2.i386.deb&lang=English_gpl")
[*]Now, open a terminal, and do the following commands: ```
sudo aa-complain cupsd
``` ... then ```
sudo mkdir /usr/share/cups/model
```
[*]Now that that's done, you'll have to install the drivers. To do this, run these commands: ```
dpkg  -i  --force-all  /path/to/lpr-drivername
```... Replaceing "/path/to/lpr-drivername" with the full location of the LPR driver.
[*]Now... run this ```
dpkg  -i  --force-all  /path/to/cupswrapper-drivername
``` ... of cource, the same as last time, only the path to the cupswraper.
[*]To make sure the installation was successful, run this: ```
dpkg  -l  |  grep  Brother
```
[/LIST]
Hope this helps!,
PP

---

### Post by lenich89 on 2009-11-01
Thank you very much for the reply, all i had to do was the apt-get remove command. ty

---

### Post by PorkyPie on 2009-11-01
Your welcome.

---

