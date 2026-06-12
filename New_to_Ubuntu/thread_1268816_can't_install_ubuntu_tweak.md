---
title: "can't install ubuntu tweak"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by ray62 on 2009-09-17
tryin 2 reinstall ubuntu tweaks as it tells me 2 do that so i can uninstall ?

summary of commands which did not work:


 	Quote:
 	 	 		 			 				sudo apt-get remove -f ubuntu-tweak
sudo dpkg --purge ubuntu-tweak
sudo dpkg --force-remove-reinstreq --purge ubuntu-tweak
sudo dpkg -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
sudo dpkg --*force*-*all* -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb

---

### Post by HolyShnikes on 2009-09-17
Try this. 

apt-get remove --purge "package names"

---

### Post by ray62 on 2009-09-17
wot for?

---

### Post by HolyShnikes on 2009-09-17
sorry I think I entered an invalid code the first post, so I didn't want you to try anything that was going to screw it up.  :) 

Give that one a try.

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ apt-get remove --purge "package names"
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
raymond@raymond-laptop:~$

---

### Post by vantsochev on 2009-09-17
type sudo or login as root... and "package names" should be replaced :)

---

### Post by ray62 on 2009-09-17
a complete novice at this dont no wot u mean ???

---

### Post by HolyShnikes on 2009-09-17
> **vantsochev said:**
> type sudo or login as root... and "package names" should be replaced :)

Duh :roll:

---

### Post by steveneddy on 2009-09-17
> **ray62 said:**
> **wot** for?

did you actually mean to ask "**What** for?

try this

sudo dpkg -r ubuntu-tweak

---

### Post by vantsochev on 2009-09-17
Okay, type the following in terminal

```
 sudo apt-get remove --purge ubuntu-tweak 
```

Then just delete the files on the desktop.

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo dpkg -r ubuntu-tweak
dpkg: error processing ubuntu-tweak (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-tweak
raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo dpkg -r ubuntu-tweak
dpkg: error processing ubuntu-tweak (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-tweak
raymond@raymond-laptop:~$

Try running the following command. It will reinstall the package and then remove it.

```

sudo apt-get install --reinstall ubuntu-tweak && sudo apt-get remove --purge ubuntu-tweak 

```

Hope this helps,
Bodsda

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$  sudo apt-get remove --purge ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo apt-get reinstall ubuntu-tweak && sudo apt-get remove --purge ubuntu-tweak
E: Invalid operation reinstall
raymond@raymond-laptop:

---

### Post by HolyShnikes on 2009-09-17
I think...

```
sudo apt-get install --reinstall packagename
``` 

?

---

### Post by Bodsda on 2009-09-17
> **HolyShnikes said:**
> I think...

```
sudo apt-get install --reinstall packagename
``` 

?

Yeah, see my edit above

> **ray62 said:**
> raymond@raymond-laptop:~$ sudo apt-get reinstall ubuntu-tweak && sudo apt-get remove --purge ubuntu-tweak
E: Invalid operation reinstall
raymond@raymond-laptop:
I edited my post, please paste the newer command

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo apt-get install --reinstall ubuntu tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo apt-get install --reinstall ubuntu tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

Error in the package name, you missed the '-'. It should be 'ubuntu-tweak'

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> Yeah, see my edit above


I edited my post, please paste the newer command


raymond@raymond-laptop:~$ sudo apt-get install --reinstall ubuntu-tweak && sudo apt-get remove --purge ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo apt-get install --reinstall ubuntu-tweak && sudo apt-get remove --purge ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

Hmm, ok maybe apt-get cant fix this. lets go the dpkg route.

Please run the following
```

dpkg --remove --force-remove-reinstreq ubuntu-tweak

```
and paste the results

Hope this helps,
Bodsda

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> Hmm, ok maybe apt-get cant fix this. lets go the dpkg route.

Please run the following
```

dpkg --remove --force-remove-reinstreq ubuntu-tweak

```and paste the results

Hope this helps,
Bodsda


raymond@raymond-laptop:~$ dpkg --remove --force-remove-reinstreq ubuntu-tweak
dpkg: requested operation requires superuser privilege
raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ dpkg --remove --force-remove-reinstreq ubuntu-tweak
dpkg: requested operation requires superuser privilege
raymond@raymond-laptop:~$

oh, sorry add a sudo in front of that.
```

sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak

```
Hope this helps,
Bodsda

---

### Post by vantsochev on 2009-09-17
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak

---

### Post by vantsochev on 2009-09-17
also you may try removing it using aptitude:

sudo aptitude purge ubuntu-tweak

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo aptitude remove purge ubuntu-tweak
[sudo] password for raymond: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Couldn't find package "purge".  However, the following
packages contain "purge" in their name:
  libdir-purge-perl localepurge 
Couldn't find package "purge".  However, the following
packages contain "purge" in their name:
  libdir-purge-perl localepurge 
The following packages will be REMOVED:
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
  ubuntu-tweak 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 79.2MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing ubuntu-tweak (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 128530 files and directories currently installed.)
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> oh, sorry add a sudo in front of that.
```

sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak

```Hope this helps,
Bodsda


raymond@raymond-laptop:~$ sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak
[sudo] password for raymond: 
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 112228 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
raymond@raymond-laptop:~$

---

### Post by HolyShnikes on 2009-09-17
I saw a lot in that script.  Did it install or not?

Type 

sudo dpkg --get-selections > installed

and in your home directory there should be a file called "installed".  Right click on it and open it in text editor, scroll through the list and see if it is installed.

---

### Post by jpeddicord on 2009-09-17
> **vantsochev said:**
> also you may try removing it using aptitude:

sudo aptitude remove purge ubuntu-tweak

That should probably be:

```
sudo aptitude purge ubuntu-tweak
```

(otherwise it treats "purge" as a package name)

---

### Post by vantsochev on 2009-09-17
> **jacobmp92 said:**
> That should probably be:

```
sudo aptitude purge ubuntu-tweak
```

(otherwise it treats "purge" as a package name)


sorry... that was a typo... fixed it :)

---

### Post by HolyShnikes on 2009-09-17
Dumb question, but doesnt ubuntu-tweaks have a repository?  Cant this be done in synaptic?

---

### Post by ray62 on 2009-09-17
> **HolyShnikes said:**
> I saw a lot in that script.  Did it install or not?

Type 

sudo dpkg --get-selections > installed

and in your home directory there should be a file called "installed".  Right click on it and open it in text editor, scroll through the list and see if it is installed.


raymond@raymond-laptop:~$ sudo dpkg --get-selections > installed
raymond@raymond-laptop:~$ 
bash: shannon1997: command not found
raymond@raymond-laptop:~$ 

wer is my home directory ??

---

### Post by HolyShnikes on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo dpkg --get-selections > installed
raymond@raymond-laptop:~$ 
bash: shannon1997: command not found
raymond@raymond-laptop:~$ 

wer is my home directory ??

Places > Home Folder

---

### Post by ray62 on 2009-09-17
> **jacobmp92 said:**
> That should probably be:

```
sudo aptitude purge ubuntu-tweak
```(otherwise it treats "purge" as a package name)


raymond@raymond-laptop:~$ sudo aptitude purge ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages will be REMOVED:
  ubuntu-tweak{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4481kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing ubuntu-tweak (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done

raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo dpkg --get-selections > installed
raymond@raymond-laptop:~$ 
bash: shannon1997: command not found
raymond@raymond-laptop:~$ 

wer is my home directory ??

Your home directory is ```
/home/raymond
``` or can be referenced as ```
~/
```

Please try reinstalling ubuntu-tweak now with
```
sudo apt-get install ubuntu-tweak
```

---

### Post by ray62 on 2009-09-17
> **HolyShnikes said:**
> Places > Home Folder

found this ?????
ubuntu-tweak                    deinstall

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> Your home directory is ```
/home/raymond
``` or can be referenced as ```
~/
```Please try reinstalling ubuntu-tweak now with
```
sudo apt-get install ubuntu-tweak
```

raymond@raymond-laptop:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$

Ok you may like to try this. WARNING: This is a copy paste from another tutorial but from a reputable source. I trust this source.

```

sudo dpkg –remove –force-depends –force-remove-reinstreq ubuntu-tweak

```

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> Ok you may like to try this. WARNING: This is a copy paste from another tutorial but from a reputable source. I trust this source.

```

sudo dpkg –remove –force-depends –force-remove-reinstreq ubuntu-tweak

```


raymond@raymond-laptop:~$ sudo dpkg –remove –force-depends –force-remove-reinstreq ubuntu-tweak
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
raymond@raymond-laptop:~$

---

### Post by Bodsda on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo dpkg –remove –force-depends –force-remove-reinstreq ubuntu-tweak
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
raymond@raymond-laptop:~$

Ok, slight error with the copy paste formatting, try this
```

sudo dpkg --remove --force-depends --force-remove-reinstreq ubuntu-tweak

```

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> Ok, slight error with the copy paste formatting, try this
```

sudo dpkg --remove --force-depends --force-remove-reinstreq ubuntu-tweak

```


raymond@raymond-laptop:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq ubuntu-tweak
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 112228 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
raymond@raymond-laptop:~$

---

### Post by ubongo2008 on 2009-09-17
@everyone whos allready ripping hairs out of his/her head please have a look here
[http://ubuntuforums.org/showthread.php?t=1268624](http://ubuntuforums.org/showthread.php?t=1268624)
for commands which allready have been tryed.


the best thing you may do is extract the package using dpkg, copy all files where they should be and then try an uninstall.

i belive that the package itself may be bad or something messed it up since you get this phyton error


EDIT:  for an complete description of the command

use ```
man dpkg
```EDIT: Don't forget it is an karmic package [COLOR=Red]THIS IS ALPHA[/COLOR] anyway

---

### Post by ubongo2008 on 2009-09-17
doublepost

---

### Post by Bodsda on 2009-09-17
> **ubongo2008 said:**
> @everyone whos allready ripping hairs out of his/her head please have a look here
[http://ubuntuforums.org/showthread.php?t=1268624](http://ubuntuforums.org/showthread.php?t=1268624)
for commands which allready have been tryed.


the best thing you may do is extract the package using dpkg, copy all files where they should be and then try an uninstall.

i belive that the package itself may be bad or something messed it up since you get this phyton error


EDIT: use for an complete description of the command

use ```
man dpkg
```EDIT: Don't forget it is an karmic package [COLOR=Red]THIS IS ALPHA[/COLOR] anyway

Care to provide the OP some instructions on doing that?

---

### Post by ubongo2008 on 2009-09-17
> **Bodsda said:**
> Care to provide the OP some instructions on doing that?
well we've already tried nearly everything in this thread therefore  it would have been helpfull to provide the info that there is already an existing thread

---

### Post by ray62 on 2009-09-17
> **Bodsda said:**
> Care to provide the OP some instructions on doing that?


How do i extract the files wer from and wer do i but sorry but i am a novice and appreciate your help

---

### Post by ubongo2008 on 2009-09-17
dpkg --extract "PackageFileName" "DestinationDirectory"

---

### Post by ray62 on 2009-09-17
sorry dont understand been on linux about a wk 
thanx for all your help anyway

---

### Post by ubongo2008 on 2009-09-17
you can extract it using:

```
mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/

```Then copy everything using

```
ALT+F2 then gksudo nautilus 
``` where it should be
if that dosn't help and also 

```
 sudo dpkg --force-all --purge ubuntu-tweak 
```is unable to remove the package then it is not possible to remove it using apt, synaptic or dpkg

EDIT:

> Unlike dpkg, apt-get does not understand .deb files, it works with the packages proper name and can only install .deb archives from a source specified in /etc/apt/sources.list. **[COLOR=Red] apt-get will call dpkg directly after downloading the .deb archives[/COLOR]**
Source: [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)

END OF EDIT

that would be something for an bugreport in my opinion

As i already said it is an alpha version which you have had installed

EDIT:
 sorry had a typo 

```
mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/

```

---

### Post by ray62 on 2009-09-17
> **ubongo2008 said:**
> you can extract it using:

```
mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/

```Then copy everything using

```
ALT+F2 then gksudo nautilus 
``` where it should be
if that dosn't help and also 

```
 sudo dpkg --force-all --purge ubuntu-tweak 
```is unable to remove the package then it is not possible to remove it using apt, synaptic or dpkg

EDIT:

Source: [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)

END OF EDIT

that would be something for an bugreport in my opinion

As i already said it is an alpha version which you have had installed


raymond@raymond-laptop:~$ mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
mkdir: cannot create directory `/home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386': File exists
raymond@raymond-laptop:~$ dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/
dpkg-deb: failed to read archive `/home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb': No such file or directory
raymond@raymond-laptop:~$

---

### Post by ubongo2008 on 2009-09-17
sorry that was my error 
```

mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/
```

---

### Post by desperado665 on 2009-09-17
I'm not sure about karmic, but up to Jaunty, ubuntu-tweak is not in the repos. go to [www.ubuntu-tweak.com/downloads](www.ubuntu-tweak.com/downloads) and follow the instructions in blue to add the PPA so it will show up in your repo list.

---

### Post by ray62 on 2009-09-17
> **ubongo2008 said:**
> sorry that was my error 
```

mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/
```


raymond@raymond-laptop:~$ mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
mkdir: cannot create directory `/home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386': File exists
raymond@raymond-laptop:~$ dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/
dpkg-deb: failed to read archive `/home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb': No such file or directory
raymond@raymond-laptop:~$ 


thanx for all your help but i give up

---

### Post by ray62 on 2009-09-17
> **desperado665 said:**
> I'm not sure about karmic, but up to Jaunty, ubuntu-tweak is not in the repos. go to [www.ubuntu-tweak.com/downloads]("http://www.ubuntu-tweak.com/downloads") and follow the instructions in blue to add the PPA so it will show up in your repo list.


tried that way but thanks

---

### Post by ubongo2008 on 2009-09-17
the problem isn't karmic or jaunty the problem is the package cant be removed using dpkg, apt, or synaptic

maybe downloading the correct version of the deb file and then extracting it and coping  its contents to the correct locations would help to fix that problem

---

### Post by ray62 on 2009-09-17
wer wud i download the correct file ??????

---

### Post by ubongo2008 on 2009-09-17
please post output of 

dpkg -l | grep tweak

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ raymond@raymond-laptop:~$ dpkg -l | grep tweak
bash: raymond@raymond-laptop:~$: command not found
raymond@raymond-laptop:~$ ii  mousetweaks                                2.26.0-0ubuntu1                           mouse accessibility enhancements for the GNO
The program 'ii' is currently not installed.  You can install it by typing:
sudo apt-get install ii
bash: ii: command not found
raymond@raymond-laptop:~$ pFR ubuntu-tweak                               0.4.9-1~karmic1                           config Ubuntu tool
bash: pFR: command not found
raymond@raymond-laptop:~$ raymond@raymond-laptop:~$ 
bash: raymond@raymond-laptop:~$: command not found
raymond@raymond-laptop:~$

---

### Post by ubongo2008 on 2009-09-17
```
dpkg -l | grep tweak
iU  ubuntu-tweak                               0.4.9-1~karmic1                          config Ubuntu tool

```


```
sudo dpkg --purge  ubuntu-tweak
(Reading database ... 135538 files and directories currently installed.)
Removing ubuntu-tweak ...
Purging configuration files for ubuntu-tweak ...
```


well the package is ok, atleast  i can install and uninstall it

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ dpkg -l | grep tweak
ii  mousetweaks                                2.26.0-0ubuntu1                           mouse accessibility enhancements for the GNO
pFR ubuntu-tweak                               0.4.9-1~karmic1                           config Ubuntu tool
raymond@raymond-laptop:~$ iU  ubuntu-tweak                               0.4.9-1~karmic1                          config Ubuntu tool

raymond@raymond-laptop:~$ sudo dpkg --purge  ubuntu-tweak
dpkg: error processing ubuntu-tweak (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-tweak
raymond@raymond-laptop:~$ (Reading database ... 135538 files and directories currently installed.)
bash: Reading: command not found
raymond@raymond-laptop:~$ Removing ubuntu-tweak ...
bash: Removing: command not found
raymond@raymond-laptop:~$ Purging configuration files for ubuntu-tweak ...
bash: Purging: command not found
raymond@raymond-laptop:~$

---

### Post by ubongo2008 on 2009-09-17
ok your version is "0.4.9-1~karmic1"

so you need ubuntu-tweak_0.4.9-1~karmic1_i386.deb

---

### Post by ubongo2008 on 2009-09-17
download the file and try

> **ubongo2008 said:**
> you can extract it using:

```
mkdir ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386
dpkg --extract ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386/

```Then copy everything using

```
ALT+F2 then gksudo nautilus 
``` where it should be
if that dosn't help and also 

```
 sudo dpkg --force-all --purge ubuntu-tweak 
```is unable to remove the package then it is not possible to remove it using apt, synaptic or dpkg

that would be something for an bugreport in my opinion

As i already said it is an alpha version which you have had installed
 

---

### Post by ubongo2008 on 2009-09-17
you should save it to your desktop for the above commands

By the way i am also on jaunty but amd64 so it is no problem for dpkg on jaunty to deal  with karmic packgages

---

### Post by ray62 on 2009-09-17
thanks for your help but its all double dutch to me

---

### Post by steveneddy on 2009-09-17
In terminal:

```
locate ubuntu-tweak
```

A list of file locations shows up in terminal.

Just open nautilus as root:

```
gksudo nautilus
```

and while looking at the terminal, go to those folders and just remove the offending software manually.

Just delete anything with the ubuntu-tweak name on it.

Then you're done.

Hint:

If the web site for the software is written in real bad English, you may want to reconsider installing that software.

---

### Post by bapoumba on 2009-09-18
Please post your sources.list
```
cat /etc/apt/sources.list
```

and the output to 
```
aptitude show ubuntu-tweak
```

---

### Post by Brad54 on 2009-09-18
Been following yr posts; I had same issue w. ubuntu-tweak 0.4.9. I went to synaptic package mgr., searched "tweak" and clicked properties. That yielded a list of places where the files are. In my installation, the stuff was at:
```
/.
/etc
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/ubuntu-tweak-daemon.conf
/usr
/usr/share
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/128x128
/usr/share/icons/hicolor/128x128/apps
/usr/share/icons/hicolor/128x128/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/22x22
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/22x22/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/64x64
/usr/share/icons/hicolor/64x64/apps
/usr/share/icons/hicolor/64x64/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/36x36
/usr/share/icons/hicolor/36x36/apps
/usr/share/icons/hicolor/36x36/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/96x96
/usr/share/icons/hicolor/96x96/apps
/usr/share/icons/hicolor/96x96/apps/ubuntu-tweak.png
/usr/share/icons/hicolor/24x24
/usr/share/icons/hicolor/24x24/apps
/usr/share/icons/hicolor/24x24/apps/ubuntu-tweak.png
/usr/share/applications
/usr/share/applications/ubuntu-tweak.desktop
/usr/share/python-support
/usr/share/python-support/ubuntu-tweak.private
/usr/share/dbus-1
/usr/share/dbus-1/system-services
/usr/share/dbus-1/system-services/com.ubuntu_tweak.daemon.getconfig.service
/usr/share/dbus-1/system-services/com.ubuntu_tweak.daemon.packageconfig.service
/usr/share/dbus-1/system-services/com.ubuntu_tweak.daemon.service
/usr/share/pixmaps
/usr/share/pixmaps/ubuntu-tweak.png
/usr/share/doc
/usr/share/doc/ubuntu-tweak
/usr/share/doc/ubuntu-tweak/changelog.gz
/usr/share/doc/ubuntu-tweak/changelog.Debian.gz
/usr/share/doc/ubuntu-tweak/copyright
/usr/share/PolicyKit
/usr/share/PolicyKit/policy
/usr/share/PolicyKit/policy/com.ubuntu-tweak.daemon.policy
/usr/share/ubuntu-tweak
/usr/share/ubuntu-tweak/powermanager.py
/usr/share/ubuntu-tweak/common
/usr/share/ubuntu-tweak/common/config.py
/usr/share/ubuntu-tweak/common/canvas.py
/usr/share/ubuntu-tweak/common/download.py
/usr/share/ubuntu-tweak/common/notify.py
/usr/share/ubuntu-tweak/common/settings.py
/usr/share/ubuntu-tweak/common/misc.py
/usr/share/ubuntu-tweak/common/package.py
/usr/share/ubuntu-tweak/common/systeminfo.py
/usr/share/ubuntu-tweak/common/gui.py
/usr/share/ubuntu-tweak/common/inifile.py
/usr/share/ubuntu-tweak/common/widgets
/usr/share/ubuntu-tweak/common/widgets/containers.py
/usr/share/ubuntu-tweak/common/widgets/treeviews.py
/usr/share/ubuntu-tweak/common/widgets/__init__.py
/usr/share/ubuntu-tweak/common/widgets/dialogs.py
/usr/share/ubuntu-tweak/common/widgets/cellrendererbutton.py
/usr/share/ubuntu-tweak/common/widgets/widgets.py
/usr/share/ubuntu-tweak/common/widgets/utils.py
/usr/share/ubuntu-tweak/common/factory.py
/usr/share/ubuntu-tweak/common/consts.py
/usr/share/ubuntu-tweak/common/__init__.py
/usr/share/ubuntu-tweak/common/appdata.py
/usr/share/ubuntu-tweak/common/debug.py
/usr/share/ubuntu-tweak/common/policykit
/usr/share/ubuntu-tweak/common/policykit/polkitbutton.py
/usr/share/ubuntu-tweak/common/policykit/__init__.py
/usr/share/ubuntu-tweak/common/policykit/dbusproxy.py
/usr/share/ubuntu-tweak/common/utils.py
/usr/share/ubuntu-tweak/ubuntu-tweak.py
/usr/share/ubuntu-tweak/session.py
/usr/share/ubuntu-tweak/preferences.py
/usr/share/ubuntu-tweak/filetype.py
/usr/share/ubuntu-tweak/data
/usr/share/ubuntu-tweak/data/applogos
/usr/share/ubuntu-tweak/data/applogos/chmsee.png
/usr/share/ubuntu-tweak/data/applogos/tasque.png
/usr/share/ubuntu-tweak/data/applogos/agave.png
/usr/share/ubuntu-tweak/data/applogos/galaxium.png
/usr/share/ubuntu-tweak/data/applogos/lxde.png
/usr/share/ubuntu-tweak/data/applogos/transmission-gtk.png
/usr/share/ubuntu-tweak/data/applogos/ubuntu-x.png
/usr/share/ubuntu-tweak/data/applogos/leafpad.png
/usr/share/ubuntu-tweak/data/applogos/mirage.png
/usr/share/ubuntu-tweak/data/applogos/avidemux.png
/usr/share/ubuntu-tweak/data/applogos/gajim.png
/usr/share/ubuntu-tweak/data/applogos/isomaster.png
/usr/share/ubuntu-tweak/data/applogos/gparted.png
/usr/share/ubuntu-tweak/data/applogos/monodevelop.png
/usr/share/ubuntu-tweak/data/applogos/backintime-gnome.png
/usr/share/ubuntu-tweak/data/applogos/wine-doors.png
/usr/share/ubuntu-tweak/data/applogos/eioffice-personal.png
/usr/share/ubuntu-tweak/data/applogos/netbeans.png
/usr/share/ubuntu-tweak/data/applogos/ubuntu-tweak.png
/usr/share/ubuntu-tweak/data/applogos/zim.png
/usr/share/ubuntu-tweak/data/applogos/christine.png
/usr/share/ubuntu-tweak/data/applogos/ubudsl.png
/usr/share/ubuntu-tweak/data/applogos/vlc.png
/usr/share/ubuntu-tweak/data/applogos/swiftweasel.png
/usr/share/ubuntu-tweak/data/applogos/gnote.png
/usr/share/ubuntu-tweak/data/applogos/wine.png
/usr/share/ubuntu-tweak/data/applogos/openoffice.png
/usr/share/ubuntu-tweak/data/applogos/breathe-icon-theme.png
/usr/share/ubuntu-tweak/data/applogos/compiz.png
/usr/share/ubuntu-tweak/data/applogos/pidgin.png
/usr/share/ubuntu-tweak/data/applogos/gcolor2.png
/usr/share/ubuntu-tweak/data/applogos/shutter.png
/usr/share/ubuntu-tweak/data/applogos/build-essential.png
/usr/share/ubuntu-tweak/data/applogos/devhelp.png
/usr/share/ubuntu-tweak/data/applogos/giver.png
/usr/share/ubuntu-tweak/data/applogos/mono.png
/usr/share/ubuntu-tweak/data/applogos/gpicview.png
/usr/share/ubuntu-tweak/data/applogos/ubuntu-restricted-extras.png
/usr/share/ubuntu-tweak/data/applogos/liferea.png
/usr/share/ubuntu-tweak/data/applogos/gtk-recordmydesktop.png
/usr/share/ubuntu-tweak/data/applogos/mplayer.png
/usr/share/ubuntu-tweak/data/applogos/azureus.png
/usr/share/ubuntu-tweak/data/applogos/soundconverter.png
/usr/share/ubuntu-tweak/data/applogos/gnome-colors.png
/usr/share/ubuntu-tweak/data/applogos/audacious.png
/usr/share/ubuntu-tweak/data/applogos/eclipse.png
/usr/share/ubuntu-tweak/data/applogos/specto.png
/usr/share/ubuntu-tweak/data/applogos/avant-window-navigator.png
/usr/share/ubuntu-tweak/data/applogos/inkscape.png
/usr/share/ubuntu-tweak/data/applogos/midori.png
/usr/share/ubuntu-tweak/data/applogos/amarok-nightly.png
/usr/share/ubuntu-tweak/data/applogos/meld.png
/usr/share/ubuntu-tweak/data/applogos/blueman.png
/usr/share/ubuntu-tweak/data/applogos/snes9x-gtk.png
/usr/share/ubuntu-tweak/data/applogos/clutter.png
/usr/share/ubuntu-tweak/data/applogos/filezilla.png
/usr/share/ubuntu-tweak/data/applogos/smplayer.png
/usr/share/ubuntu-tweak/data/applogos/mozilla-security.png
/usr/share/ubuntu-tweak/data/applogos/terminator.png
/usr/share/ubuntu-tweak/data/applogos/anjuta.png
/usr/share/ubuntu-tweak/data/applogos/shiki-colors.png
/usr/share/ubuntu-tweak/data/applogos/google-gadgets.png
/usr/share/ubuntu-tweak/data/applogos/ibus-table.png
/usr/share/ubuntu-tweak/data/applogos/skype.png
/usr/share/ubuntu-tweak/data/applogos/ibus.png
/usr/share/ubuntu-tweak/data/applogos/synapse.png
/usr/share/ubuntu-tweak/data/applogos/stardict.png
/usr/share/ubuntu-tweak/data/applogos/deluge-torrent.png
/usr/share/ubuntu-tweak/data/applogos/empathy.png
/usr/share/ubuntu-tweak/data/applogos/opera.png
/usr/share/ubuntu-tweak/data/applogos/gloobus.png
/usr/share/ubuntu-tweak/data/applogos/google.png
/usr/share/ubuntu-tweak/data/applogos/gnome-games.png
/usr/share/ubuntu-tweak/data/applogos/ghex.png
/usr/share/ubuntu-tweak/data/applogos/lastfm.png
/usr/share/ubuntu-tweak/data/applogos/banshee.png
/usr/share/ubuntu-tweak/data/applogos/gnome-globalmenu.png
/usr/share/ubuntu-tweak/data/applogos/gnome-core-devel.png
/usr/share/ubuntu-tweak/data/applogos/google-chrome-unstable.png
/usr/share/ubuntu-tweak/data/applogos/moblin.png
/usr/share/ubuntu-tweak/data/applogos/codeblocks.png
/usr/share/ubuntu-tweak/data/applogos/rar.png
/usr/share/ubuntu-tweak/data/applogos/qt-creator.png
/usr/share/ubuntu-tweak/data/applogos/googleearth.png
/usr/share/ubuntu-tweak/data/applogos/avant-window-navigator-trunk.png
/usr/share/ubuntu-tweak/data/applogos/moovida.png
/usr/share/ubuntu-tweak/data/applogos/gtg.png
/usr/share/ubuntu-tweak/data/applogos/cairo-dock.png
/usr/share/ubuntu-tweak/data/applogos/exaile.png
/usr/share/ubuntu-tweak/data/applogos/screenlets.png
/usr/share/ubuntu-tweak/data/applogos/ibus-table-wubi.png
/usr/share/ubuntu-tweak/data/applogos/backintime-kde4.png
/usr/share/ubuntu-tweak/data/applogos/ibus-pinyin.png
/usr/share/ubuntu-tweak/data/applogos/ubuntu-cn.png
/usr/share/ubuntu-tweak/data/applogos/webkitgtk.png
/usr/share/ubuntu-tweak/data/applogos/amule.png
/usr/share/ubuntu-tweak/data/applogos/gloobus-preview.png
/usr/share/ubuntu-tweak/data/applogos/playonlinux.png
/usr/share/ubuntu-tweak/data/applogos/checkgmail.png
/usr/share/ubuntu-tweak/data/applogos/getdeb.png
/usr/share/ubuntu-tweak/data/applogos/pcmanfm.png
/usr/share/ubuntu-tweak/data/applogos/compizconfig-settings-manager.png
/usr/share/ubuntu-tweak/data/applogos/kino.png
/usr/share/ubuntu-tweak/data/applogos/gimp.png
/usr/share/ubuntu-tweak/data/applogos/emesene.png
/usr/share/ubuntu-tweak/data/applogos/miro.png
/usr/share/ubuntu-tweak/data/applogos/virtualbox-3.0.png
/usr/share/ubuntu-tweak/data/applogos/gnome-do-plugins.png
/usr/share/ubuntu-tweak/data/applogos/gftp.png
/usr/share/ubuntu-tweak/data/applogos/gmail-notify.png
/usr/share/ubuntu-tweak/data/applogos/audacity.png
/usr/share/ubuntu-tweak/data/applogos/chromium-browser.png
/usr/share/ubuntu-tweak/data/applogos/picasa.png
/usr/share/ubuntu-tweak/data/applogos/mail-notification.png
/usr/share/ubuntu-tweak/data/applogos/qt.png
/usr/share/ubuntu-tweak/data/applogos/geany.png
/usr/share/ubuntu-tweak/data/applogos/firefox.png
/usr/share/ubuntu-tweak/data/applogos/nautilus-dropbox.png
/usr/share/ubuntu-tweak/data/applogos/xbmc.png
/usr/share/ubuntu-tweak/data/applogos/medibuntu.png
/usr/share/ubuntu-tweak/data/applogos/rednotebook.png
/usr/share/ubuntu-tweak/data/applogos/virtualbox.png
/usr/share/ubuntu-tweak/data/applogos/virtualbox-ose.png
/usr/share/ubuntu-tweak/data/applogos/kde-4.png
/usr/share/ubuntu-tweak/data/applogos/gnome-do.png
/usr/share/ubuntu-tweak/data/applogos/gmchess.png
/usr/share/ubuntu-tweak/data/applogos/gwibber.png
/usr/share/ubuntu-tweak/data/applogos/spicebird.png
/usr/share/ubuntu-tweak/data/applogos/vmware-player.png
/usr/share/ubuntu-tweak/data/applogos/arc-colors.png
/usr/share/ubuntu-tweak/data/aptkeys
/usr/share/ubuntu-tweak/data/aptkeys/exaile.gpg
/usr/share/ubuntu-tweak/data/aptkeys/mozilla-security.gpg
/usr/share/ubuntu-tweak/data/aptkeys/awn.gpg
/usr/share/ubuntu-tweak/data/aptkeys/virtualboxose.gpg
/usr/share/ubuntu-tweak/data/aptkeys/wine-doors.gpg
/usr/share/ubuntu-tweak/data/aptkeys/synapse.gpg
/usr/share/ubuntu-tweak/data/aptkeys/kde4.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gwibber.gpg
/usr/share/ubuntu-tweak/data/aptkeys/transmission_nightly.gpg
/usr/share/ubuntu-tweak/data/aptkeys/chromium-browser.gpg
/usr/share/ubuntu-tweak/data/aptkeys/clutter.gpg
/usr/share/ubuntu-tweak/data/aptkeys/globalmenu.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gwibber-daily.gpg
/usr/share/ubuntu-tweak/data/aptkeys/ubuntu-x-unstable.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gtg.gpg
/usr/share/ubuntu-tweak/data/aptkeys/screenlets.gpg
/usr/share/ubuntu-tweak/data/aptkeys/terminator.gpg
/usr/share/ubuntu-tweak/data/aptkeys/do.gpg
/usr/share/ubuntu-tweak/data/aptkeys/smplayer.gpg
/usr/share/ubuntu-tweak/data/aptkeys/shutter.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gmchess.gpg
/usr/share/ubuntu-tweak/data/aptkeys/spicebird.gpg
/usr/share/ubuntu-tweak/data/aptkeys/specto.gpg
/usr/share/ubuntu-tweak/data/aptkeys/rednotebook.gpg
/usr/share/ubuntu-tweak/data/aptkeys/empathy.gpg
/usr/share/ubuntu-tweak/data/aptkeys/cairo-dock.gpg
/usr/share/ubuntu-tweak/data/aptkeys/midori.gpg
/usr/share/ubuntu-tweak/data/aptkeys/lxde.gpg
/usr/share/ubuntu-tweak/data/aptkeys/amule-release.gpg
/usr/share/ubuntu-tweak/data/aptkeys/smplayer-testing.gpg
/usr/share/ubuntu-tweak/data/aptkeys/ubuntu-x.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gnote.gpg
/usr/share/ubuntu-tweak/data/aptkeys/compiz.gpg
/usr/share/ubuntu-tweak/data/aptkeys/backintime.gpg
/usr/share/ubuntu-tweak/data/aptkeys/xbmc.gpg
/usr/share/ubuntu-tweak/data/aptkeys/webkitgtk.gpg
/usr/share/ubuntu-tweak/data/aptkeys/tweak.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gnome-colors.gpg
/usr/share/ubuntu-tweak/data/aptkeys/google.gpg
/usr/share/ubuntu-tweak/data/aptkeys/banshee-stable.gpg
/usr/share/ubuntu-tweak/data/aptkeys/moblin-karmic.gpg
/usr/share/ubuntu-tweak/data/aptkeys/ibus-dev.gpg
/usr/share/ubuntu-tweak/data/aptkeys/firefox.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gimp-testing.gpg
/usr/share/ubuntu-tweak/data/aptkeys/mono.gpg
/usr/share/ubuntu-tweak/data/aptkeys/ooo.gpg
/usr/share/ubuntu-tweak/data/aptkeys/christine.gpg
/usr/share/ubuntu-tweak/data/aptkeys/galaxium.gpg
/usr/share/ubuntu-tweak/data/aptkeys/pol.gpg
/usr/share/ubuntu-tweak/data/aptkeys/qt.gpg
/usr/share/ubuntu-tweak/data/aptkeys/banshee-unstable.gpg
/usr/share/ubuntu-tweak/data/aptkeys/vlc.gpg
/usr/share/ubuntu-tweak/data/aptkeys/liferea.gpg
/usr/share/ubuntu-tweak/data/aptkeys/breathe-icon-theme.gpg
/usr/share/ubuntu-tweak/data/aptkeys/chmsee.gpg
/usr/share/ubuntu-tweak/data/aptkeys/moovida.gpg
/usr/share/ubuntu-tweak/data/aptkeys/geany.gpg
/usr/share/ubuntu-tweak/data/aptkeys/moblin-jaunty.gpg
/usr/share/ubuntu-tweak/data/aptkeys/pidgin.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gadgets.gpg
/usr/share/ubuntu-tweak/data/aptkeys/tweak-unstable.gpg
/usr/share/ubuntu-tweak/data/aptkeys/virtualbox.gpg
/usr/share/ubuntu-tweak/data/aptkeys/awn-testing.gpg
/usr/share/ubuntu-tweak/data/aptkeys/transmission_beta.gpg
/usr/share/ubuntu-tweak/data/aptkeys/gnome-games.gpg
/usr/share/ubuntu-tweak/data/aptkeys/neon.gpg
/usr/share/ubuntu-tweak/data/aptkeys/opera.gpg
/usr/share/ubuntu-tweak/data/aptkeys/wine.gpg
/usr/share/ubuntu-tweak/data/aptkeys/ubudsl.gpg
/usr/share/ubuntu-tweak/data/aptkeys/medibuntu.gpg
/usr/share/ubuntu-tweak/data/aptkeys/transmission_stable.gpg
/usr/share/ubuntu-tweak/data/aptkeys/mplayer-libs.gpg
/usr/share/ubuntu-tweak/data/aptkeys/blueman.gpg
/usr/share/ubuntu-tweak/data/gui
/usr/share/ubuntu-tweak/data/gui/traceback.glade
/usr/share/ubuntu-tweak/data/gui/sourceeditor.glade
/usr/share/ubuntu-tweak/data/gui/preferences.glade
/usr/share/ubuntu-tweak/data/gui/type_edit.glade
/usr/share/ubuntu-tweak/data/pixmaps
/usr/share/ubuntu-tweak/data/pixmaps/shortcuts.png
/usr/share/ubuntu-tweak/data/pixmaps/templates.png
/usr/share/ubuntu-tweak/data/pixmaps/scripts.png
/usr/share/ubuntu-tweak/data/pixmaps/filetype.png
/usr/share/ubuntu-tweak/data/pixmaps/history.png
/usr/share/ubuntu-tweak/data/pixmaps/root.png
/usr/share/ubuntu-tweak/data/pixmaps/ubuntu-tweak.png
/usr/share/ubuntu-tweak/data/pixmaps/gnome.png
/usr/share/ubuntu-tweak/data/pixmaps/metacity.png
/usr/share/ubuntu-tweak/data/pixmaps/compiz-fusion.png
/usr/share/ubuntu-tweak/data/pixmaps/powermanager.png
/usr/share/ubuntu-tweak/data/pixmaps/banner_left.png
/usr/share/ubuntu-tweak/data/pixmaps/autostart.png
/usr/share/ubuntu-tweak/data/pixmaps/third-soft.png
/usr/share/ubuntu-tweak/data/pixmaps/package.png
/usr/share/ubuntu-tweak/data/pixmaps/applications.png
/usr/share/ubuntu-tweak/data/pixmaps/installer.png
/usr/share/ubuntu-tweak/data/pixmaps/service.png
/usr/share/ubuntu-tweak/data/pixmaps/banner_right.png
/usr/share/ubuntu-tweak/data/pixmaps/image.png
/usr/share/ubuntu-tweak/data/pixmaps/lockdown.png
/usr/share/ubuntu-tweak/data/pixmaps/ubuntu-tweak-64.png
/usr/share/ubuntu-tweak/data/pixmaps/personal.png
/usr/share/ubuntu-tweak/data/pixmaps/sourceeditor.png
/usr/share/ubuntu-tweak/data/pixmaps/system.png
/usr/share/ubuntu-tweak/data/pixmaps/desktop.png
/usr/share/ubuntu-tweak/data/pixmaps/nautilus.png
/usr/share/ubuntu-tweak/data/pixmaps/welcome.png
/usr/share/ubuntu-tweak/data/pixmaps/userdir.png
/usr/share/ubuntu-tweak/data/pixmaps/startup.png
/usr/share/ubuntu-tweak/data/pixmaps/icon.png
/usr/share/ubuntu-tweak/data/pixmaps/splash.png
/usr/share/ubuntu-tweak/data/pixmaps/computer.png
/usr/share/ubuntu-tweak/data/pixmaps/nautilus-cd-burner.png
/usr/share/ubuntu-tweak/data/pixmaps/session.png
/usr/share/ubuntu-tweak/data/scripts
/usr/share/ubuntu-tweak/data/scripts/create-launcher
/usr/share/ubuntu-tweak/data/scripts/set-image-as-wallpaper
/usr/share/ubuntu-tweak/data/scripts/copy-to-download
/usr/share/ubuntu-tweak/data/scripts/copy-to
/usr/share/ubuntu-tweak/data/scripts/check-md5-sum
/usr/share/ubuntu-tweak/data/scripts/search-in-current
/usr/share/ubuntu-tweak/data/scripts/link-to-home
/usr/share/ubuntu-tweak/data/scripts/copy-to-home
/usr/share/ubuntu-tweak/data/scripts/move-to
/usr/share/ubuntu-tweak/data/scripts/move-to-home
/usr/share/ubuntu-tweak/data/scripts/convert-image-to-gif
/usr/share/ubuntu-tweak/data/scripts/browse-as-root
/usr/share/ubuntu-tweak/data/scripts/link-to-download
/usr/share/ubuntu-tweak/data/scripts/open-with-your-favourite-text-editor
/usr/share/ubuntu-tweak/data/scripts/convert-image-to-png
/usr/share/ubuntu-tweak/data/scripts/convert-image-to-jpg
/usr/share/ubuntu-tweak/data/scripts/link-to-desktop
/usr/share/ubuntu-tweak/data/scripts/move-to-desktop
/usr/share/ubuntu-tweak/data/scripts/move-to-download
/usr/share/ubuntu-tweak/data/scripts/copy-to-desktop
/usr/share/ubuntu-tweak/data/scripts/open-with-your-favourite-text-editor-as-root
/usr/share/ubuntu-tweak/data/scripts/link-to
/usr/share/ubuntu-tweak/data/scripts/make-hard-shadow-to-image
/usr/share/ubuntu-tweak/data/keys.xml
/usr/share/ubuntu-tweak/data/appcates
/usr/share/ubuntu-tweak/data/appcates/internet.png
/usr/share/ubuntu-tweak/data/appcates/image.png
/usr/share/ubuntu-tweak/data/appcates/theme.png
/usr/share/ubuntu-tweak/data/appcates/mail.png
/usr/share/ubuntu-tweak/data/appcates/cd.png
/usr/share/ubuntu-tweak/data/appcates/desktop.png
/usr/share/ubuntu-tweak/data/appcates/video.png
/usr/share/ubuntu-tweak/data/appcates/im.png
/usr/share/ubuntu-tweak/data/appcates/sound.png
/usr/share/ubuntu-tweak/data/appcates/ftp.png
/usr/share/ubuntu-tweak/data/appcates/text.png
/usr/share/ubuntu-tweak/data/appcates/all.png
/usr/share/ubuntu-tweak/data/appcates/p2p.png
/usr/share/ubuntu-tweak/data/appcates/emulator.png
/usr/share/ubuntu-tweak/data/appcates/develop.png
/usr/share/ubuntu-tweak/data/templates
/usr/share/ubuntu-tweak/data/templates/ods-spreadsheet.ods
/usr/share/ubuntu-tweak/data/templates/shell-script.sh
/usr/share/ubuntu-tweak/data/templates/python-script.py
/usr/share/ubuntu-tweak/data/templates/odp-presentation.odp
/usr/share/ubuntu-tweak/data/templates/pygtk-example.py
/usr/share/ubuntu-tweak/data/templates/plain-text-document.txt
/usr/share/ubuntu-tweak/data/templates/odt-document.odt
/usr/share/ubuntu-tweak/data/templates/html-document.html
/usr/share/ubuntu-tweak/data/templates/odb-database.odb
/usr/share/ubuntu-tweak/backends
/usr/share/ubuntu-tweak/backends/packageconfig.py
/usr/share/ubuntu-tweak/backends/getconfig.py
/usr/share/ubuntu-tweak/backends/__init__.py
/usr/share/ubuntu-tweak/thirdsoft.py
/usr/share/ubuntu-tweak/sourceeditor.py
/usr/share/ubuntu-tweak/utility.py
/usr/share/ubuntu-tweak/computer.py
/usr/share/ubuntu-tweak/shortcuts.py
/usr/share/ubuntu-tweak/userdir.py
/usr/share/ubuntu-tweak/gnomesettings.py
/usr/share/ubuntu-tweak/installer.py
/usr/share/ubuntu-tweak/nautilus.py
/usr/share/ubuntu-tweak/ScriptWorker.py
/usr/share/ubuntu-tweak/lockdown.py
/usr/share/ubuntu-tweak/scripts.py
/usr/share/ubuntu-tweak/mainwindow.py
/usr/share/ubuntu-tweak/updatemanager.py
/usr/share/ubuntu-tweak/templates.py
/usr/share/ubuntu-tweak/autostart.py
/usr/share/ubuntu-tweak/compiz.py
/usr/share/ubuntu-tweak/metacity.py
/usr/share/ubuntu-tweak/icons.py
/usr/share/ubuntu-tweak/cleaner.py
/usr/share/locale
/usr/share/locale/th
/usr/share/locale/th/LC_MESSAGES
/usr/share/locale/th/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fa
/usr/share/locale/fa/LC_MESSAGES
/usr/share/locale/fa/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nn
/usr/share/locale/nn/LC_MESSAGES
/usr/share/locale/nn/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/mk
/usr/share/locale/mk/LC_MESSAGES
/usr/share/locale/mk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_AU
/usr/share/locale/en_AU/LC_MESSAGES
/usr/share/locale/en_AU/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pt
/usr/share/locale/pt/LC_MESSAGES
/usr/share/locale/pt/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fo
/usr/share/locale/fo/LC_MESSAGES
/usr/share/locale/fo/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_CA
/usr/share/locale/en_CA/LC_MESSAGES
/usr/share/locale/en_CA/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ms
/usr/share/locale/ms/LC_MESSAGES
/usr/share/locale/ms/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sr
/usr/share/locale/sr/LC_MESSAGES
/usr/share/locale/sr/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bn
/usr/share/locale/bn/LC_MESSAGES
/usr/share/locale/bn/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/hi
/usr/share/locale/hi/LC_MESSAGES
/usr/share/locale/hi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/kk
/usr/share/locale/kk/LC_MESSAGES
/usr/share/locale/kk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nb
/usr/share/locale/nb/LC_MESSAGES
/usr/share/locale/nb/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/jv
/usr/share/locale/jv/LC_MESSAGES
/usr/share/locale/jv/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bs
/usr/share/locale/bs/LC_MESSAGES
/usr/share/locale/bs/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ml
/usr/share/locale/ml/LC_MESSAGES
/usr/share/locale/ml/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/be
/usr/share/locale/be/LC_MESSAGES
/usr/share/locale/be/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ka
/usr/share/locale/ka/LC_MESSAGES
/usr/share/locale/ka/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/is
/usr/share/locale/is/LC_MESSAGES
/usr/share/locale/is/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/oc
/usr/share/locale/oc/LC_MESSAGES
/usr/share/locale/oc/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ar
/usr/share/locale/ar/LC_MESSAGES
/usr/share/locale/ar/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/uk
/usr/share/locale/uk/LC_MESSAGES
/usr/share/locale/uk/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ga
/usr/share/locale/ga/LC_MESSAGES
/usr/share/locale/ga/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/lt
/usr/share/locale/lt/LC_MESSAGES
/usr/share/locale/lt/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sl
/usr/share/locale/sl/LC_MESSAGES
/usr/share/locale/sl/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/en_GB
/usr/share/locale/en_GB/LC_MESSAGES
/usr/share/locale/en_GB/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/te
/usr/share/locale/te/LC_MESSAGES
/usr/share/locale/te/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sq
/usr/share/locale/sq/LC_MESSAGES
/usr/share/locale/sq/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/eo
/usr/share/locale/eo/LC_MESSAGES
/usr/share/locale/eo/LC_MESSAGES/ubuntu-tweak.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/ubuntu-tweak.mo
/usr/bin
/usr/bin/ubuntu-tweak
/usr/bin/script-worker
/usr/bin/ubuntu-tweak-daemon
***************************************
```
the uninstall routines insisted that one of the .py files was not a directory so I fired up dolphin as a superuser and deleted the offending .py file using the path listed in the terminal window that's listed as "details" when you use synaptic pkg. mgr. to try and uninstall. the error message gives a lot of detail regarding file locations. there were details in python directory regarding ubuntu-tweak that got trashed. Then the directory listed in the error details. Then the offending .py file listed in the error detail. Then cleaned out trash. Debug log then shows, "2009-09-18 09:44:24 status not-installed ubuntu-tweak <none>" I think this is what we want. after the detetions the synaptic pkg. mgr. did not show the item. The acid test comes upon reboot, I was ready to reinstall everything if this didn't work, but I will add a post to let you lnow how it worked. Please forgive the long winded message, but I wanted to help out, here.

---

### Post by Brad54 on 2009-09-18
On restart, Ubuntu-tweak is gone from the menus. unsuccessful attempts to uninstall will yield a message, if you look at it there is a "details" caret. Click the caret to find out where to find the files that hang the uninstall process. I copied the message to file, and went after the files manually. I went at it in kind of a ham-handed way yet did not break the OS. That is a testament to the robust nature of Ubuntu!! (pride goeth before a fall, snicker) I will check back 4 u, hope this helps.:)

---

### Post by Brad54 on 2009-09-19
"/usr/share/python-support/ubuntu-tweak.private is not a directory "
  seems to come up alot for you.. My synaptic mistook a .py file for a directory and ended process with similar error code. I used a file manager  with the code gksudo nautilus and found the single entry that synaptic was choking on, (the full path is in the error details) then deleted that file. Then I reran synaptic to remove the rest of it. Reboot.

---

### Post by c2006 on 2009-09-25
I hate to say it, but the best way of going forward may be to nuke the drive and start again. I ran into similar problems with ubuntu-tweak. Thankfully I had the prescience to have /home on a separate partition and didn't lose any data.

I will grant that this was essentially self-imposed -- I accidentally downloaded the **karmic** package for ubu-tweak and proceeded to install it on my **jaunty** system... :lolflag:

Though you can try what Brad54 said. It just might work.

I forgot the single most important lesson: Do not go installing things when you are dog tired (as I was at the time).

---

