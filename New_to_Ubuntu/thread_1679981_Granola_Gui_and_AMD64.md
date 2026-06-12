---
title: "Granola Gui and AMD64"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by gulmer on 2011-02-01
I installed Granola on a i386 pent.4 with Ubuntu 10.04 and the GUI came up. I install Granola on my AMD64 dual core and the GUI doesn't show up on the desktop. What can I do to get it to show so I can unlock it?

---

### Post by [Snc] on 2011-02-02
> **gulmer said:**
> I installed Granola on a i386 pent.4 with Ubuntu 10.04 and the GUI came up. I install Granola on my AMD64 dual core and the GUI doesn't show up on the desktop. What can I do to get it to show so I can unlock it?

Have you installed the 64bit version?

At the bottom of [http://grano.la/help/](http://grano.la/help/) you can pick your version, make sire it is of the right architecture!

PS. Running it in terminal will post back the error codes and other information, it would be good if you could copy and paste those into a "code" section here (access the "code" section with the '#' button on top of the reply form)

---

### Post by gulmer on 2011-02-05
> **'[Snc] said:**
> Have you installed the 64bit version?

At the bottom of [http://grano.la/help/](http://grano.la/help/) you can pick your version, make sire it is of the right architecture!

PS. Running it in terminal will post back the error codes and other information, it would be good if you could copy and paste those into a "code" section here (access the "code" section with the '#' button on top of the reply form)

 ```

``` Here's what I get when running granola in terminal: gene@gene-desktop:~$ granola
granola[9886]: Version 3.0.8 is starting.
granola[9886]: Can't open lockfile /var/run/granola.pid: Permission denied
granola[9886]: Failed to start, error obtaining lockfile
granola[9886]: Already running or do we not have have permission to write to '/var/run/granola.pid'?
gene@gene-desktop:~$ 

 On the granola web site at the bottom, the versions that you can pick are for Tarball Release for Other Distributions. Since I'm running Ubuntu 10.10, I just followed the instructions for installing under that distro. It installed but the GUI doesn't work. 
 
 I also ran this in terminal: gene@gene-desktop:~$ apt-cache search MiserWare
granola - MiserWare intelligent power management for PCs
granola-gui - MiserWare Granola graphical interface
granola-stats - MiserWare Granola daemon to upload saving stats
miserware-repo - MiserWare software repository
gene@gene-desktop:~$ 

 I sent MiserWare an email on this, no reply yet. Still no GUI.

---

### Post by davidmohammed on 2011-02-05
granola is the daemon I think - you dont run this to start the gui

try

granola-gui

---

### Post by gulmer on 2011-02-05
> **davidmohammed said:**
> granola is the daemon I think - you dont run this to start the gui

try

granola-gui

```

``` 
 OK, this is what I get when running the gui:
gene@gene-desktop:~$ granola-gui
Granola Error: Unable to read report data (/var/lib/miserware/granola_stats), have you run Granola yet?
[[Errno 2] No such file or directory: '/var/lib/miserware/granola_stats']

 Does that help?

---

### Post by davidmohammed on 2011-02-05
suggest remove granola and reinstall via the command line - any errors seen?

sudo apt-get purge granola

sudo apt-get purge granola-gui

sudo apt-get install granola

sudo apt-get install granola-gui

---

### Post by gulmer on 2011-02-05
> **davidmohammed said:**
> suggest remove granola and reinstall via the command line - any errors seen?

sudo apt-get purge granola

sudo apt-get purge granola-gui

sudo apt-get install granola

sudo apt-get install granola-gui

 ```

``` I followed your instructions and this is what happened: gene@gene-desktop:~$ sudo apt-get purge granola
[sudo] password for gene: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  granola* granola-gui*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 938kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 231588 files and directories currently installed.)
Removing granola-gui ...
Removing granola ...
Purging configuration files for granola ...
Processing triggers for python-support ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
gene@gene-desktop:~$ sudo apt-get install granola
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  granola
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/110kB of archives.
After this operation, 377kB of additional disk space will be used.
Selecting previously deselected package granola.
(Reading database ... 231515 files and directories currently installed.)
Unpacking granola (from .../granola_3.0.8-0maverick1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up granola (3.0.8-0maverick1) ...
 Removing any system startup links for /etc/init.d/ondemand ...
 * Starting Granola granola                                              [fail] 
gene@gene-desktop:~$ sudo apt-get install granola-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  granola-gui
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/227kB of archives.
After this operation, 561kB of additional disk space will be used.
Selecting previously deselected package granola-gui.
(Reading database ... 231527 files and directories currently installed.)
Unpacking granola-gui (from .../granola-gui_3.0.4-0maverick1_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up granola-gui (3.0.4-0maverick1) ...
Processing triggers for python-support ...

 Still no gui.

---

### Post by davidmohammed on 2011-02-05
the bit in the trace that is of interest is

* Starting Granola granola [fail] 

why?

any errors displayed when you attempt to start the daemon using sudo?

sudo granola

---

### Post by gulmer on 2011-02-05
> **davidmohammed said:**
> the bit in the trace that is of interest is

* Starting Granola granola [fail] 

why?

any errors displayed when you attempt to start the daemon using sudo?

sudo granola

```

```
 This is what I get: gene@gene-desktop:~$ sudo granola
[sudo] password for gene: 
granola[17525]: Version 3.0.8 is starting.
granola[17525]: Using config file '/etc/granola.conf'
granola[17525]: Set LogLevel to notice
granola[17525]: Set Policy to MiserWare
granola[17525]: Error opening scaling governor file '/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor' in read mode
granola[17525]: Is cpufreq enabled in this kernel and do you have a CPU which supports DVFS?
granola[17525]: Can't manage DVFS for any CPUs
granola[17525]: Warning, could not set up a configuration for managing the CPUs
granola[17525]: Failed to start, error initializing

 My system is an AMD Athlon 64 X2 Dual Core 4400+
 I'm not sure, but I think this supports DVFS.

---

### Post by ebasa on 2011-02-05
Have you tried here:

[https://download.miserware.com/linux/deb/ubuntu/maverick/amd64/](https://download.miserware.com/linux/deb/ubuntu/maverick/amd64/)

---

### Post by davidmohammed on 2011-02-05
> **gulmer said:**
> ```

```
 This is what I get: gene@gene-desktop:~$ sudo granola
[sudo] password for gene: 
granola[17525]: Version 3.0.8 is starting.
granola[17525]: Using config file '/etc/granola.conf'
granola[17525]: Set LogLevel to notice
granola[17525]: Set Policy to MiserWare
granola[17525]: Error opening scaling governor file '/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor' in read mode
granola[17525]: Is cpufreq enabled in this kernel and do you have a CPU which supports DVFS?
granola[17525]: Can't manage DVFS for any CPUs
granola[17525]: Warning, could not set up a configuration for managing the CPUs
granola[17525]: Failed to start, error initializing

 My system is an AMD Athlon 64 X2 Dual Core 4400+
 I'm not sure, but I think this supports DVFS.

I think you need to have a close look in the BIOS options to check for CPU frequency and DVFS options (these might be under different named options)

---

### Post by gulmer on 2011-02-06
> **ebasa said:**
> Have you tried here:

[https://download.miserware.com/linux/deb/ubuntu/maverick/amd64/](https://download.miserware.com/linux/deb/ubuntu/maverick/amd64/)

I'll try this, but before I load this I need to remove the existing miserware, correct? Including the version of granola?

 Ok, I tried and got this message, "Sorry,MiserWare-repo is not available for this type of computer(AMD64)

 So that's that. Still got it on my other 2 computers, though the AMD64 is the one we use the most. Maybe they'll get a version up for the AMD64. 
 
 Thanks for all the help.

---

### Post by davidmohammed on 2011-02-06
yes - follow the purge removal steps as before - 

I think ebasa could be correct - wont hurt to try.

---

