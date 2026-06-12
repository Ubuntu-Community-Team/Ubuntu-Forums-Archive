---
title: "Canon ip3600 printer driver?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by SteveFJ on 2010-02-13
I don't know how I go about installing a driver for a Canon ip3600 printer. I would appreciate it if someone would assist me in this.

Much thanks.

---

### Post by Shpongle on 2010-02-13
have you tried just connecting it up to see if it works out of the box ? , linux has built in generic drivers that can deal with a wide range of hardware ? and peripherals 

also see this [http://www.linuxquestions.org/questions/linux-hardware-18/canon-pixma-ip3600-howto-721448/](http://www.linuxquestions.org/questions/linux-hardware-18/canon-pixma-ip3600-howto-721448/)

---

### Post by Shpongle on 2010-02-13
theres a .deb for it here [http://software.canon-europe.com/products/0010648.asp](http://software.canon-europe.com/products/0010648.asp)

---

### Post by SteveFJ on 2010-02-13
Hello, and thank you for your reply. I have tried thew printer and it dosn't work

I'm afraid I don't understand the link you have posted as I am very new to Ubuntu and Linux.

---

### Post by SteveFJ on 2010-02-13
> **DillByrne said:**
> theres a .deb for it here [http://software.canon-europe.com/products/0010648.asp](http://software.canon-europe.com/products/0010648.asp)

Thanks for that, I've downloaded the file but I don't know how to install it.

---

### Post by Shpongle on 2010-02-13
just double click it and it will prompt you for your password and self install. just to clarify you got the first link the debian(.deb) one and not the .rpm one used by redhat etc

---

### Post by Shpongle on 2010-02-13
sorry i just seen its a tar file there i assumed it'd be a deb, sorry for that , theyre should be a read me in it , extract it to you desktop and check it

---

### Post by Shpongle on 2010-02-13
ok extract the file , you have two deb file which you can double click to self install i think you can forget about the other tar file as it seems to be the same as one of the deb files

---

### Post by SteveFJ on 2010-02-13
I've now put that on my desktop. When I open it I have no Read files

i have the following folders:
333,
334,
336,
338,
341,
342,
346,
backend,
cngpij,
cngpijmon,
cnijfilter,
debian,
lgmon,
libs,
ppd,
printui,
pstocanonij,

and the following files:
cnijfilter-comon.spec,
licence-cnijfilter-3.00en.txt,
licence-cnijfilter-3.00fr.txt,
licence-cnijfilter-3.00jp.txt,
licence-cnijfilter-3.00sc.txt,
makefile,

and that it.

---

### Post by Shpongle on 2010-02-13
initially you should have the 1 tar file , when you extract that you should get 2 .deb files and a tar file . double click on the two deb files to install them . the second tar file inside the original one is the source and as far as i can tell its the same as one of the tar files, so you dont need to install it , only install it if it doesnt work( you can install the nested tar by cd to the directory and runing make and then sudo make install )

---

### Post by SteveFJ on 2010-02-13
That isn't what I am getting at all. Just the one folder with those listed inside it.

---

### Post by Shpongle on 2010-02-13
> **SteveFJ said:**
> That isn't what I am getting at all. Just the one folder with those listed inside it.

you must have extracted the sub folder out only ,delete the extracted files

ok go to the original downloaded file and copy it to a new folder eg ~/Desktop/temp, in temp click on the tar and click extract here , you should get three files listed in this pic

---

### Post by SteveFJ on 2010-02-13
Yes. thanks for that.

I've  tried to install the first and got the following message:

```
[COLOR=Red]Failed to completely install all dependencies
to fix this run 'sudo apt-get install -f' in a terminal window[/COLOR]
```

Ive now done that:
```

steve@Fran:~$ sudo apt-get install -f
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  bibledit-data billard-gl-data freeglut3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  cnijfilter-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 156kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142644 files and directories currently installed.)
Removing cnijfilter-common ...
steve@Fran:~$
```

Ive now tried to install the second file and have got the following:

```
cnijfilter-ip3600series
[COLOR=Red]
Error: Dependency is not satisfiable: cnijfilter-common (>= 3.00)[/COLOR]
```

---

### Post by Shpongle on 2010-02-13
> **SteveFJ said:**
> Yes. thanks for that.

I've  tried to install the first and got the following message:

```
[COLOR=Red]Failed to completely install all dependencies
to fix this run 'sudo apt-get install -f' in a terminal window[/COLOR]
```

Ive now done that:
```

steve@Fran:~$ sudo apt-get install -f
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  bibledit-data billard-gl-data freeglut3
Use 'apt-get autoremove' to remove them.
[COLOR=Red]The following packages will be REMOVED
  cnijfilter-common[/COLOR]
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 156kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142644 files and directories currently installed.)
[COLOR=Red]Removing cnijfilter-common ...[/COLOR]
steve@Fran:~$
```

Ive now tried to install the second file and have got the following:

```
cnijfilter-ip3600series
[COLOR=Red]
Error: Dependency is not satisfiable: cnijfilter-common (>= 3.00)[/COLOR]
```

try install the common deb file first then the ip3600series deb file ,

if that doesnt work extract the sub tar file and 'cd' into that directory, you should have the files you had originally when you extracted the first time and type make , then sudo make install , then try the two debs again

---

### Post by SteveFJ on 2010-02-13
> **DillByrne said:**
> try install the common deb file first then the ip3600series deb file ,

That's the way I tried it.

---

### Post by Shpongle on 2010-02-13
> **SteveFJ said:**
> That's the way I tried it.

ok , try this extract the sub tar file and 'cd' into that directory, you should have the files you had originally when you extracted the first time and type make , then sudo make install , then try the two debs again
__________________

---

### Post by SteveFJ on 2010-02-13
> **DillByrne said:**
> ok , try this extract the sub tar file and 'cd' into that directory, you should have the files you had originally when you extracted the first time and type make , then sudo make install , then try the two debs again
__________________


i'm not quite with you on the 'cd' bit?

As an edit now I've looked, where will I find the sub tar file?

---

### Post by Shpongle on 2010-02-13
> **SteveFJ said:**
> i'm not quite with you on the 'cd' bit?

in the terminal , its a command to change directory , eg if i wanted to change to my music folder , id type cd /home/dill/Music or cd ~/Music . ~/ is a shortcut for /home/username . you can use to command ls to list whats in your current directory , and cd .. will take you back a directory

---

### Post by SteveFJ on 2010-02-13
> **DillByrne said:**
> in the terminal , its a command to change directory , eg if i wanted to change to my music folder , id type cd /home/dill/Music or cd ~/Music . ~/ is a shortcut for /home/username . you can use to command ls to list whats in your current directory , and cd .. will take you back a directory

Right. So what would I type in to find the sub tar file?

Sorry if I appear thick, but I am new at this lot.

---

### Post by Shpongle on 2010-02-13
no it can be confusing i understand, ok you downloaded the file frm the website . this was in a tar format its similar to a rar or a zip file, in this tar file there was two deb files and another tar file which must also be extracted, you can click on it and click extract here. 

where have you extracted it to ?, like whats the path to the file, if it was on your desktop the path would be ~/Desktop

---

### Post by SteveFJ on 2010-02-14
Can you please confirm that it is the one for debian that I should be downloading from Canon.

As an edit, if so then these are the three files I now have on my desktop:

cinjfilter-common_3.00-1_i386.deb
cinjfilter-ip3600series_3.00-1_i386.deb
cinjfilter-common_3.00-1.tar.gz

I assume the sub file is the tar.gz?

If this is correct then I need to know what I need to key in to the terminal.

Much thanks.

---

### Post by Shpongle on 2010-02-14
> **SteveFJ said:**
> Can you please confirm that it is the one for debian that I should be downloading from Canon.

As an edit, if so then these are the three files I now have on my desktop:

cinjfilter-common_3.00-1_i386.deb
cinjfilter-ip3600series_3.00-1_i386.deb
cinjfilter-common_3.00-1.tar.gz

I assume the sub file is the tar.gz?

If this is correct then I need to know what I need to key in to the terminal.

Much thanks.

yea they are the three files , try double click cinjfilter-common_3.00-1_i386.deb first , then double click this cinjfilter-ip3600series_3.00-1_i386.deb.  if that doesnt work extract the cinjfilter-common_3.00-1.tar.gz file to your desktop. click on it and click extract here. it should be in its own folder now 

you should have these four items on your desktop now, the red one being the newly extracted folder

cinjfilter-common_3.00-1_i386.deb
cinjfilter-ip3600series_3.00-1_i386.deb
cinjfilter-common_3.00-1.tar.gz
[COLOR="Red"]cinjfilter-common_3.00[/COLOR]

in a terminal type ```
cd ~/Desktop/cinjfilter-common_3.00
make 
sudo make install
```

---

### Post by SteveFJ on 2010-02-14
Thanks for that. At first I got no result, but then noticed a couple of typos, so I entered this:

tesxt in Post not being recognised for some reason.

---

### Post by SteveFJ on 2010-02-14
This is a retry to enter text for above post:

i can't enter code in post

This is what I typed in

  	 	 	 	 	 	  > cd ~/Desktop/cnijfilter-common-3.00
make
sudo make install Post edited to include quote

---

### Post by SteveFJ on 2010-02-14
I'll try as a quote instead:



> steve@Fran:~$ cd ~/Desktop/cnijfilter-common-3.00
steve@Fran:~/Desktop/cnijfilter-common-3.00$ make
for dir in libs cngpij pstocanonij backend; do (cd $dir; make $target)|| exit 1; done
make[1]: Entering directory `/home/steve/Desktop/cnijfilter-common-3.00/libs'
make[1]: *** No targets specified and no makefile found. Stop.
make[1]: Leaving directory `/home/steve/Desktop/cnijfilter-common-3.00/libs'
make: *** [all] Error 1
steve@Fran:~/Desktop/cnijfilter-common-3.00$ sudo make install
target=install; for dir in libs cngpij pstocanonij backend; do (cd $dir; make $target)|| exit 1; done
make[1]: Entering directory `/home/steve/Desktop/cnijfilter-common-3.00/libs'
make[1]: *** No rule to make target `install'. Stop.
make[1]: Leaving directory `/home/steve/Desktop/cnijfilter-common-3.00/libs'
make: *** [install] Error 1
steve@Fran:~/Desktop/cnijfilter-common-3.00$

---

### Post by SteveFJ on 2010-02-20
While I am thankful to DillByrne for the help given here, I afraid I am having to bump this topic as the problem hasn't been resolved.

Any further help here to solve this would be most appreciated.

Much thanks.

---

