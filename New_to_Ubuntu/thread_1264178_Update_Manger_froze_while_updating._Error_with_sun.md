---
title: "Update Manger froze while updating. Error with sun-java6-fonts"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-09-11
I was updating my system with Update Manager. It was downloading all the packages, than it froze. restarted by hitting the ALT+Print Screen with hitting the keys R+E+I+S+U+B.

than i opened a terminal and typed in:
```

sudo apt-get update
sudo apt-get upgrade

```

it told me to do:
```
sudo dpkg --configure -a
```
to fix the problem.

which i did, it unpack some packages and installed everything correctly. including all the sun-java products which are:

```

sun-java6-bin 
sun-java6-jre 
sun-java6-fonts 
sun-java6-plugin

```

but since this incident happen. I got an error with the sun-java6-fonts:

```
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I used Synaptic Package Manager, looked up sun-java6-fonts, i picked the reinstall box, it reinstalled everything, which are:
```

sun-java6-bin 
sun-java6-jre 
sun-java6-fonts 
sun-java6-plugin

```

than try complete removal and installed again all the sun java packages.

I still keep getting that sun-java6-fonts error. the error still shows up on the command line everytime i do:

```
sudo apt-get autoremove
```

```
kenny@kenny-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kenny@kenny-laptop:~$ 

```

how do i fix this problem?

later on, someone told me to do this:

```
kenny@kenny-laptop:~$ sudo dpkg -r --force-all sun-java6-bin
dpkg: sun-java6-bin: dependency problems, but removing anyway as you request:
 sun-java6-plugin depends on sun-java6-bin (= 6-16-0ubuntu1.9.04).
 sun-java6-jre depends on sun-java6-bin (= 6-16-0ubuntu1.9.04) | ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04); however:
  Package sun-java6-bin is to be removed.
  Package ia32-sun-java6-bin is not installed.
(Reading database ... 135819 files and directories currently installed.)
Removing sun-java6-bin ...
Processing triggers for menu ...
kenny@kenny-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installed
E: Unmet dependencies. Try using -f.
kenny@kenny-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin
The following NEW packages will be installed:
  sun-java6-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/29.1MB of archives.
After this operation, 86.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 135450 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Processing triggers for menu ...
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up sun-java6-bin (6-16-0ubuntu1.9.04) ...

Processing triggers for menu ...
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kenny@kenny-laptop:~$ sudo dpkg -r --force-all sun-java6-fonts
(Reading database ... 135819 files and directories currently installed.)
Removing sun-java6-fonts ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
kenny@kenny-laptop:~$ 

```

---

### Post by zvacet on 2009-09-12
```
sudo dpkg --configure sun-java6-fonts
```

---

### Post by shiningkenmonster on 2009-09-12
```
kenny@kenny-laptop:~$ sudo dpkg --configure sun-java6-fonts
[sudo] password for kenny: 
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
kenny@kenny-laptop:~$ 

```

---

### Post by oldos2er on 2009-09-12
Are you running 64-bit Ubuntu? Can you check your Software Sources, and make sure you have the multiverse repository enabled?

 And, can you post the output of **ls /etc/defoma/hints **?

---

### Post by shiningkenmonster on 2009-09-13
no, I am using the Ubuntu 9.04 Netbook Remix.

yes, the multiverse repository is enabled.

as for that code:
```
kenny@kenny-laptop:~$ ls /etc/defoma/hints
gsfonts.hints             ttf-dejavu-core.hints       ttf-lao.hints                    ttf-sil-andika.hints
sun-java6-fonts.hints     ttf-dejavu-extra.hints      ttf-liberation.hints             ttf-sjfonts.hints
ttf-arabeyes.hints        ttf-dustin.hints            ttf-mscorefonts-installer.hints  ttf-thai-tlwg.hints
ttf-arphic-uming.hints    ttf-freefont.hints          ttf-sazanami-gothic.hints        ttf-unfonts-core.hints
ttf-bitstream-vera.hints  ttf-indic-fonts-core.hints  ttf-sazanami-mincho.hints
kenny@kenny-laptop:~$ 
```

the thing is that. i have another netbook that is very identical to this laptop. the other netbook updated correctly without the freeze. It didnt have the same problem.

---

