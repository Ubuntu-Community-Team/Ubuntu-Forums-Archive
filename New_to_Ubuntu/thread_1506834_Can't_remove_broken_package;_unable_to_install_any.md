---
title: "Can't remove broken package; unable to install anything"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by charliechip95 on 2010-06-10
Okay, so I've been trying to figure out how to use my Dazzle DVC USB capture card with Linux Ubuntu, and got it so it can work with TVtime well. But TVtime doesn't record (which I need), so I thought I'd give Cinelerra a shot. Anyway, I tried installing it using the normal "sudo apt-get install cinelerra" command in the terminal, and it ran into some errors:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcinelerra
The following NEW packages will be installed:
  cinelerra libcinelerra
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.7MB of archives.
After this operation, 29.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/akirad/akirad/ubuntu/ lucid/main libcinelerra 2.1.1-git20100325~ppa5~lucid [2,441kB]
Get:2 http://ppa.launchpad.net/akirad/akirad/ubuntu/ lucid/main cinelerra 2.1.1-git20100325~ppa5~lucid [11.3MB]
Fetched 13.7MB in 1min 53s (121kB/s)                                           
Selecting previously deselected package libcinelerra.
(Reading database ... 159886 files and directories currently installed.)
Unpacking libcinelerra (from .../libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmpeg3hv-1.5.0.so.1.0.0', which is also in package libmpeg3hv 1:2.1.0-2svn20070109
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Man that looks complicated. I tried to uninstall it using Synaptic Package Manager, and...

```
(Reading database ... 159885 files and directories currently installed.)
Removing Cinelerra ...
Description:    Ubuntu 10.04 LTS
locale "en_US.ISO-8859-15" not in archive
locale "ru_KU.KOI8-R" not in archive
rm: cannot remove '/usr/bin/Cinelerra' No such file or directory
dpkg: error processing cinelerra (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 cinerella
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:


```

So that didn't work. I'm not sure what I can do to remove it now. Is there any way I can force the removal?

And now I can't install any new programs; when I try to, it tells me "The package system is broken", and clicking "details" it says "cinelerra". So hopefully no new programs are required to fix this. Because I can't install them. :rolleyes:

Any help would be appreciated! :p

---

### Post by apjone on 2010-06-10
Open a terminal and type

```

sudo apt-get remove cinelerra

```

If that does not work post the output here.

---

### Post by charliechip95 on 2010-06-10
I tried it and got this error message:

```
user@computer-desktop:~$ sudo apt-get remove cinelerra
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerra
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 23.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 159885 files and directories currently installed.)
Removing cinelerra ...
Description:	Ubuntu 10.04 LTS
locale "ru_RU.KOI8-R" not in archive
locale "en_US.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by apjone on 2010-06-10
Not a nice method but seems to do the job

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8796859](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8796859)

---

### Post by 67GTA on 2010-06-10
The package didn't install correctly for some reason. I would first try ```
sudo dpkg --configure -a
``` to try and force the install to finish and free up the package manager. If that doesn't work, we will have to dig a little deeper.

---

### Post by charliechip95 on 2010-06-11
Alrighty, put it in the terminal, and it worked fine (if no response is fine ;) )

```
user@computer-desktop:~$ sudo dpkg --configure -a
 [sudo] password for user: 
user@computer-desktop:~$
```

Afterwords I tried removing Cinelerra through the terminal and got the usual error message.

```
user@computer-desktop:~$ sudo apt-get remove cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerra
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 23.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 159885 files and directories currently installed.)
Removing cinelerra ...
Description:	Ubuntu 10.04 LTS
locale "ru_RU.KOI8-R" not in archive
locale "en_US.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And the response from Synaptic Package Manager seems the same too. I'm ready to dig 'er in deep! :p

---

### Post by Soul-Sing on 2010-06-11
```
gksudo nautilus
```

via /var/lib/dpkg/info
remove the "broken" files.

```
sudo apt-get update
```

---

### Post by elliotn on 2010-06-11
When I had this problem I did sudo amptitude update or install and it worked well

---

### Post by charliechip95 on 2010-06-11
leoquant: Sorry, I don't completely understand your instructions. Do you mean, enter gksudo nautilus in the terminal, then cd to /var/lib/dpkg/info and enter sudo apt-get update? Do I have to become root during any of this? And what will this do? Sorry, I'm a fairly-advanced Windows user but I'm not very experienced with following Terminal instructions.

---

### Post by marcoftheknight on 2010-06-11
> **leoquant said:**
> ```
gksudo nautilus
```via /var/lib/dpkg/info
remove the "broken" files.

```
sudo apt-get update
```

gksu nautilus will run the Graphical directory user interface in admin rights the rest I dont know how he wants you to apply it

---

### Post by 67GTA on 2010-06-11
Enter ```
gksudo nautilus
``` in a terminal and hit enter. This will require you to enter your user password and start the nautilus file browser with temporary admin powers so you can delete files in the root directory. Then navigate to /var/lib/dpkg/info using nautilus and delete any files pertaining to cinerella. Close nautilus, and then run ```
sudo apt-get update
``` in the terminal.

---

### Post by 67GTA on 2010-06-11
You are essentially erasing apt's memory of the broken file so you can either reinstall or remove cinerella.

---

### Post by bodhi.zazen on 2010-06-11
See this blog :

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by charliechip95 on 2010-06-11
Thanks for the help! :D Just one more question: how do I go about deleting the files pertaining to Cinelerra? I don't know what the files to be deleted are called. And I'd still like to use Cinelerra if I can and I'm not sure how to go about re-installing it.

---

### Post by 67GTA on 2010-06-11
There should theoretically only be one file. It will have cinerella in it's name. Once you do this and run apt-get update, you should be able to remove/install it again.

---

### Post by charliechip95 on 2010-06-11
It worked! There were 3 files that had "cinelerra" in the name -- deleted all of them, ran apt-get update, and completely removed it in Synaptic. But I still can't get it to re-install Cinelerra properly:

```
user@computer-desktop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcinelerra
The following NEW packages will be installed:
  cinelerra libcinelerra
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
Need to get 0B/13.7MB of archives.
After this operation, 29.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 160141 files and directories currently installed.)
Unpacking libcinelerra (from .../libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmpeg3hv-1.5.0.so.1.0.0', which is also in package libmpeg3hv 1:2.1.0-2svn20070109
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Just to try something, I deleted the Cinelerra files in dpkg again and tried to reinstall in Synaptic, if that makes any sense (which, now I think of it, doesn't really). Ran across same error:

```
E: /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb: trying to overwrite '/usr/lib/libmpeg3hv-1.5.0.so.1.0.0', which is also in package libmpeg3hv 1
```

---

### Post by 67GTA on 2010-06-11
The version of cinerella you are trying to install is not compatible with the other package versions. Try just installing it from the repos, or find a ppa repo for your version of Ubuntu.

---

### Post by Soul-Sing on 2010-06-12
there were similar problems with cinelerra on ubuntuforums.
it somehow breaks -apt

---

### Post by semika on 2012-06-14
Thanks

---

