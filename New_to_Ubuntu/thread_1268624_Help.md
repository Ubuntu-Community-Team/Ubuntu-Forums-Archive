---
title: "Help"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by ray62 on 2009-09-17
Having problems with Ubuntu Tweak. Install did not work and cannot remove it.
Here is the error from terminal when trying to remove:
sudo dpkg -r ubuntu-tweak
dpkg: error processing ubuntu-tweak (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-tweak

---

### Post by pmlxuser on 2009-09-17
sudo apt-get remove -f ubuntu-tweak

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo apt-get remove -f ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
raymond@raymond-laptop:~$ 
??????????

---

### Post by ubongo2008 on 2009-09-17
try ```
sudo dpkg --purge ubuntu-tweak
```or  ```
sudo dpkg --force-remove-reinstreq --purge ubuntu-tweak 
```if you look at 

 ```
man dpkg
```

you'll see 

>   A package marked reinst-required is broken and requires reinstallation. These packages cannot be removed, unless forced with option --force-remove-reinstreq.

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo dpkg --force --purge ubuntu-tweak
dpkg: unknown force/refuse option `--purge'

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
raymond@raymond-laptop:~$ help lol

---

### Post by ray62 on 2009-09-17
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 128530 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--purge):
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
```
sudo dpkg --force-remove-reinstreq --purge ubuntu-tweak 
```^^ that did not do the trick?

sorry i did some editing ... maybe you did not see it ... i really should hit F5 more often

---

### Post by mapes12 on 2009-09-17
Your system wants you to reinstall before you can remove it. I've found the source so you can do this via Synaptic: [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by ubongo2008 on 2009-09-17
after that you may reinstall the package and see if you still have broken dependencies

---

### Post by ray62 on 2009-09-17
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 128530 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--purge):
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
still did'nt work wish i ad never bothered tryin to install it lol

---

### Post by ubongo2008 on 2009-09-17
can you reinstall the package?

---

### Post by mapes12 on 2009-09-17
See post #8

You're almost there....................

---

### Post by ray62 on 2009-09-17
cuold not open ubuntu tweak -0.4.9.1 karmac amd 64 deb 
the pakage might be corrupted or you are not allowedto open file please check permission
of the file ??????????

---

### Post by ubongo2008 on 2009-09-17
did you try 

```
sudo dpkg -i "packagename"
```if it fails redownload it 

_[https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9)_[]("http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-weak_0.4.9-1%7Ekarmic1_amd64.deb")

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo dpkg -i "packagename"
dpkg: error processing packagename (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 packagename
raymond@raymond-laptop:

and the link came up with error page not found ??

---

### Post by ray62 on 2009-09-17
tried to download it again came up with cuold not open ubuntu tweak -0.4.9.1 karmac amd 64 deb 
the pakage might be corrupted or you are not allowedto open file please check permission
of the file ??????????

---

### Post by ubongo2008 on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo dpkg -i "packagename"
dpkg: error processing packagename (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 packagename
raymond@raymond-laptop:

and the link came up with error page not found ??
  well please replace "packagename" by "ubuntu-tweak_0.4.9-1~karmic1_amd64.deb"

so 

```
sudo dpkg -i ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
```


here is an http download : _[https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9)_

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo dpkg -i ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
dpkg: error processing ubuntu-tweak_0.4.9-1~karmic1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
raymond@raymond-laptop:~$

---

### Post by ray62 on 2009-09-17
tried to download came up with cuold not open ubuntu tweak -0.4.9.1 karmac amd 64 deb 
the pakage might be corrupted or you are not allowedto open file please check permission
of the file ??????????

---

### Post by ubongo2008 on 2009-09-17
> **ray62 said:**
> raymond@raymond-laptop:~$ sudo dpkg -i ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
dpkg: error processing ubuntu-tweak_0.4.9-1~karmic1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
raymond@raymond-laptop:~$


well of course you need to specify the exact location of the file 

like ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
 or "cd" to the location where it is and use the above command again
edit:  i downloaded the file form [U][https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9)

and it seems to be ok
[/U]

---

### Post by ray62 on 2009-09-17
Sorry but you have completely lost me i appreciate all your help??

---

### Post by ubongo2008 on 2009-09-17
```

cd ~/Desktop
wget http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
sudo dpkg -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb

```

---

### Post by ubongo2008 on 2009-09-17
if it complains about missing depencies you may also download them or use synaptic by adding the repository to your /etc/apt/sources.list

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ cd ~/Desktop
raymond@raymond-laptop:~/Desktop$ wget [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb)
--2009-09-17 14:03:45--  [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb)
Resolving launchpad.net... 91.189.90.211
Connecting to launchpad.net|91.189.90.211|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://launchpadlibrarian.net/31701058/ubuntu-tweak_0.4.9-1%7Ekarmic1_amd64.deb](http://launchpadlibrarian.net/31701058/ubuntu-tweak_0.4.9-1%7Ekarmic1_amd64.deb) [following]
--2009-09-17 14:03:46--  [http://launchpadlibrarian.net/31701058/ubuntu-tweak_0.4.9-1%7Ekarmic1_amd64.deb](http://launchpadlibrarian.net/31701058/ubuntu-tweak_0.4.9-1%7Ekarmic1_amd64.deb)
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1217282 (1.2M) [application/x-debian-package]
Saving to: `ubuntu-tweak_0.4.9-1~karmic1_amd64.deb'

100%[======================================>] 1,217,282    509K/s   in 2.3s    

2009-09-17 14:03:48 (509 KB/s) - `ubuntu-tweak_0.4.9-1~karmic1_amd64.deb' saved [1217282/1217282]

raymond@raymond-laptop:~/Desktop$ sudo dpkg -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
[sudo] password for raymond: 
dpkg: error processing /home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 /home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_amd64.deb
raymond@raymond-laptop:~/Desktop$

---

### Post by ubongo2008 on 2009-09-17
well in one of your first posts you stated that you wanted the amd64 release but you have an i386 so you'll need that 

```
cd ~/Desktop
wget http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
sudo dpkg -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
```

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ cd ~/Desktop
raymond@raymond-laptop:~/Desktop$ wget [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb)
--2009-09-17 14:10:53--  [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb)
Resolving launchpad.net... 91.189.90.211
Connecting to launchpad.net|91.189.90.211|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://launchpadlibrarian.net/31701017/ubuntu-tweak_0.4.9-1%7Ekarmic1_i386.deb](http://launchpadlibrarian.net/31701017/ubuntu-tweak_0.4.9-1%7Ekarmic1_i386.deb) [following]
--2009-09-17 14:10:55--  [http://launchpadlibrarian.net/31701017/ubuntu-tweak_0.4.9-1%7Ekarmic1_i386.deb](http://launchpadlibrarian.net/31701017/ubuntu-tweak_0.4.9-1%7Ekarmic1_i386.deb)
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1213602 (1.2M) [application/x-debian-package]
Saving to: `ubuntu-tweak_0.4.9-1~karmic1_i386.deb'

100%[======================================>] 1,213,602    462K/s   in 2.6s    

2009-09-17 14:10:57 (462 KB/s) - `ubuntu-tweak_0.4.9-1~karmic1_i386.deb' saved [1213602/1213602]

raymond@raymond-laptop:~/Desktop$ sudo dpkg -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
Selecting previously deselected package ubuntu-tweak.
(Reading database ... 128531 files and directories currently installed.)
Preparing to replace ubuntu-tweak 0.4.9-1~karmic1 (using .../ubuntu-tweak_0.4.9-1~karmic1_i386.deb) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing /home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
raymond@raymond-laptop:~/Desktop$

---

### Post by ubongo2008 on 2009-09-17
sudo dpkg --*force*-*all* -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ sudo dpkg --force-all -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
(Reading database ... 128531 files and directories currently installed.)
Preparing to replace ubuntu-tweak 0.4.9-1~karmic1 (using .../ubuntu-tweak_0.4.9-1~karmic1_i386.deb) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing /home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /home/raymond/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
raymond@raymond-laptop:~$

---

### Post by ubongo2008 on 2009-09-17
it still wants to remove the old package and there are files missing 
so if even the force all switch does not work i dont know what to do anymore

sometimes creating or unpacking the missing files to the correct directories by hand may help

edit: you may extract the archive with the archive manager and then copy them where they should be
to copy them use  ALT-F2 then > gksudo nautilus

---

### Post by ubongo2008 on 2009-09-17
what is the output of 

```
file /usr/share/python-support/ubuntu-tweak.private
```

---

### Post by ray62 on 2009-09-17
raymond@raymond-laptop:~$ file /usr/share/python-support/ubuntu-tweak.private
/usr/share/python-support/ubuntu-tweak.private: ASCII text
raymond@raymond-laptop:~$ 

thanks for all u help but have to go to work now thanks again wil have another go later

---

### Post by ubongo2008 on 2009-09-17
strange problem anyway ok sorry i couldn't help:
(anyone  an idea?)


summary of commands which did not work:


> sudo apt-get remove -f ubuntu-tweak
sudo dpkg --purge ubuntu-tweak
sudo dpkg --force-remove-reinstreq --purge ubuntu-tweak
sudo dpkg -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.deb
sudo dpkg --*force*-*all* -i ~/Desktop/ubuntu-tweak_0.4.9-1~karmic1_i386.debmaybe 

sudo dpkg --force-all --purge ubuntu-tweak 

will work

so the file "/usr/share/python-support/ubuntu-tweak.private" exists but why should it be a directory

---

### Post by ray62 on 2009-09-17
Any one please pullin me hair out ere

---

### Post by bfleege on 2009-09-17
I just had this same problem.  It was because I tried to install the wrong package for my OS.

I think I figured out how to fix it.  dpkg was complaining that it couldn't access the directory at:
/usr/share/python-support/ubuntu-tweak.private

That file looked like this:
/usr/share/ubuntu-tweak/powermanager.py
/usr/share/ubuntu-tweak/ubuntu-tweak.py
/usr/share/ubuntu-tweak/session.py
/usr/share/ubuntu-tweak/preferences.py
/usr/share/ubuntu-tweak/filetype.py
/usr/share/ubuntu-tweak/thirdsoft.py
/usr/share/ubuntu-tweak/sourceeditor.py
/usr/share/ubuntu-tweak/utility.py
/usr/share/ubuntu-tweak/computer.py
/usr/share/ubuntu-tweak/shortcuts.py
[[lots more lines follow]]]

So, I think that file was actually supposed to be a symbollic link to the /usr/share/ubuntu-tweak/ folder.

This is what I did, and looks to have fixed the problem. (Do at your own risk!!!!!)

sudo cp /usr/share/python-support/ubuntu-tweak.private ~/Desktop/
sudo rm /usr/share/python-support/ubuntu-tweak.private
sudo ln -s /usr/share/ubuntu-tweak/ /usr/share/python-support/ubuntu-tweak.private
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak

Perhaps someone more knowledgeable than me can explain what exactly was happening.  My thought is: that file was supposed to be a symbollic link to a directory.  If you remove the file and make it a symbollic link to the directory, the uninstaller can work.

---

### Post by Crispyila on 2009-09-19
cant believe i tried all the instruction 4 pages ... well finally fixed i am happy .... wondering what is the correct way to install ubuntu-tweak he he he

---

