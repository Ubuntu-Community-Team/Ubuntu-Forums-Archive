---
title: "reinstalling synaptic package manager"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by rutiezer on 2009-11-09
Release 8.04
Kernel Linux 2.6.24-25-generic

Using 8.04 because version supported by tech support where I got computer.
Later versions are not.

Was updating system with synaptic.
One of the many modules synaptic was installing was "at".
Think that "at" was going to install a new version of synaptic, but it was going to first uninstall it, then install the new version. Looks like the uninstall succeeded but the new install failed. Synaptic crashed and disappeared and don't see it from System < 

Tried to reinstall with



 sudo aptitude update

 sudo apt-get install synaptic
 and got

 dpkg: error processing /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb (--unpack):
  trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin
  dpkg-deb: subprocess paste killed by signal (Broken pipe)
  Errors were encountered while processing:
   /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb
   E: Sub-process /usr/bin/dpkg returned an error code (1)


Suggestions for re-installing synaptic?

Thanks.

---

### Post by travmanx on 2009-11-09
> **rutiezer said:**
> Release 8.04
Kernel Linux 2.6.24-25-generic

Using 8.04 because version supported by tech support where I got computer.
Later versions are not.

Was updating system with synaptic.
One of the many modules synaptic was installing was "at".
Think that "at" was going to install a new version of synaptic, but it was going to first uninstall it, then install the new version. Looks like the uninstall succeeded but the new install failed. Synaptic crashed and disappeared and don't see it from System < 

Tried to reinstall with



 sudo aptitude update

 sudo apt-get install synaptic
 and got

 dpkg: error processing /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb (--unpack):
  trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin
  dpkg-deb: subprocess paste killed by signal (Broken pipe)
  Errors were encountered while processing:
   /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb
   E: Sub-process /usr/bin/dpkg returned an error code (1)


Suggestions for re-installing synaptic?

Thanks.
Try
sudo aptitude reinstall synaptic

---

### Post by winotree on 2009-11-09
*Totally Off Topic* but Cumberland, Maryland is mighty pretty country!  :)

---

### Post by QIII on 2009-11-09
I would try

```
sudo apt-get install --reinstall synaptic
```

... but I'm not sure how well that would go.  You might get the dreaded "There is already another apt running" warning.

The --reinstall flag should grab all the prerequisites and dependencies and make them right.

---

### Post by seeker5528 on 2009-11-09
> **rutiezer said:**
> Release 8.04
 dpkg: error processing /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb (--unpack):
  trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin


This looks like your first problem.

If you don't need the belocs locales try:

```
sudo dpkg --purge belocs-locales-bin
```

Then delete the belocs locals package from /var/cache/apt/archive.

The next thing to do:

```
sudo dpkg --force-overwrite --configure -a
```

: if you opted to get rid of the belocs locales package, you should be able to leave the --force-overwrite out of the above command.

Later, Seeker

---

### Post by rutiezer on 2009-11-09
Tried both suggestions and got the following:

  sudo dpkg --purge belocs-locales-bin
dpkg: dependency problems prevent removal of belocs-locales-bin:
 locales depends on belocs-locales-bin (>= 2.4-2.2ubuntu2).
dpkg: error processing belocs-locales-bin (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 belocs-locales-bin

So did not do the next step

delete the belocs locals package from /var/cache/apt/archive.


For the other suggestion got:

 sudo apt-get install --reinstall synaptic
... [ deleted lines ]
dpkg: considering deconfiguration of libc6, which would be broken by installation of libc-bin ...
dpkg: yes, will deconfigure libc6 (broken by libc-bin).
(Reading database ... 135325 files and directories currently installed.)
Unpacking libc-bin (from .../libc-bin_2.10.1-5_i386.deb) ...
De-configuring libc6 ...
Replacing files in old package libc6 ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin 0:2.4-2.2ubuntu7
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.10.1-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Suggestions, please.

---

### Post by seeker5528 on 2009-11-11
If you look in /var/cache/apt/archives and it looks like it contains every update you ever installed Then you probably want to do something like:

```
cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite libc* *locales*
```

If it looks reasonably clean or you go through ahead of time and delete some of the things you know you don't need to re-install, then you can do:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/*.deb
```

Later, Seeker

---

### Post by rutiezer on 2009-11-11
Did 

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite libc* *locales*

Got message about package configuration and note in red that says
"Configuring libc6"

Then it continues with
&#9474;                                                                                                       Running services and programs that are using NSS need to be restarted, otherwise they might not be able to do lookup or authentication any more. The installation process is able to restart some services (such as ssh or telnetd), but other programs cannot be restarted automatically. One such  program that needs manual stopping and restart after the glibc upgrade by yourself is xdm - because automatic restart might disconnect your active X11 sessions.          
                                                                             
This script detected the following installed services which must be stopped before the upgrade: gdm   
                                                                                                     If you want to interrupt the upgrade now and continue later, please answer No to the question below.
                                                                                                      Do you want to upgrade glibc now? 

Then chose "yes".

I've attached the results of "dpkg -i --force-overwrite libc* *locales*"
in the attached file "overwrite.txt". 

Can no longer start a terminal.
Will try rebooting and see if things are any better starting a terminal.

---

### Post by rutiezer on 2009-11-11
Tried to reboot and can't get to the desktop.

Get ubuntu orange progress bar then only get command line.
Message says 
"kinit: no resume image, doing normal boot".

Get command line login and I can login.
Then I shut it down with ctrl-alt-delete

and get orange progress bar again.

Computer is setup to dual boot between ubuntu and Windows XP. Logged on to Windows XP to get to this forum.

---

### Post by seeker5528 on 2009-11-11
> **rutiezer said:**
> 
Get command line login and I can login.
Then I shut it down with ctrl-alt-delete


If you can log in at the command line and use the command:

```
sudo apt-get autoclean
```

: that should clean out packages that are no longer in the repositories, leaving behind the ones that are still downloadable.

Then try the earlier commands again:

```
cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite libc* *locales*
```

Don't know why GDM, KDM, etc... are in the list of things to restart when the libc stuff is upgraded, didn't used to be and I expect a lot of people will not know they should take these out of the list.

Later, Seeker

---

### Post by rutiezer on 2009-11-11
Tried

sudo apt-get autoclean

and that appears to have run ok.

Then once again did

cd /var/cache/apt/archive
sudo dpkg -i --force-overwrite libc* *locales*

Looks like the later completed ok.
All the messages went by rather quickly.

But then same problem: can't get the desktop.

Get the message:
"kinit: no resume image, doing normal boot"

And still in the command line interface.

Rebooted and still no desktop, only the command line interface.

How do I get the desktop back?

Then I can try the re-install of synaptic and see if the prior commands were effective in restoring the environment so that I could reinstall synaptic.

---

### Post by seeker5528 on 2009-11-12
Try typing:

```
sudo /etc/init.d/gdm start
```

If that gets you the GUI login, then once you get logged in, open a terminal window and type:

```
sudo dpkg-reconfigure gdm
```

: should get you the option to choose GDM as your display manager.

If you get a message that makes it look like GDM is already running try hitting the key combo 'Alt'+'F7'.

If you get something that makes it look like GDM is not installed do:

```
sudo apt-get install gdm
```

If none of that gets you back to a GUI login try typing:

```
startx
```

Later, Seeker

---

### Post by rutiezer on 2009-11-12
Tried
  sudo /etc/init.d/gdm start
which failed. Looks like gdm is not installed. 

Did this anyway
  sudo dpkg -reconfigure gdm
and failed.

Did 
  sudo apt-get install gdm
and failed.

Did not get the GUI login so did
  startx
which failed.

For startx got message during startup saying there will be flicking and some other things. Then got error messages:

The install failed because of dependency conflicts.
Can write down and post some of them. There were lots.

Ran prior commands with "tee" to create a log file.
If I knew how to mail the output of the prior commands to myself from the command line could add logs as attachments.

For startx the error messages were

expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc

Then these prior three lines are repeated followed by:


Waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"
refcount is 2, should be 1; fixing


I don't know if this makes any difference:
There are dual monitors.

---

### Post by seeker5528 on 2009-11-12
A list of some of the dependency errors would probably help.

It would be helpful too to know if your connection to the internet is actually up, ping can tell you that.

```
sudo ping www.google.com
```

One thing you can try is:

```
sudo apt-get update
sudo apt-get -f install
```

:this will try to figure out some combination of installing/removing packages to get the package system back to a state where you can install things again, if there are broken packages.

If that completes without errors, then try:

```
sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop gdm
```

If it fails because of dependency issues and you can see one or more packages that are not going to be installed because of the conflicts, hit the up arrow key to repeat the last command and add the listed packages to the command line. 

Another option, if you use the recovery boot option, see if the option is there to repair broken packages, it does a little more than 'apt-get -f install' to try to get the installed set of packages back to a good base again, which could include adding packages, removing packages, re-writing your sources.list file and disabling unofficial repositories, so before doing that you probably want to make a copy of your existing sources.list file. To copy it to your home directory do:

```
cp /etc/apt/sources.list ~/
```

Don't know what to make of the errors when you attempt to do startx, there may be something different in the .xsession-errors file that gives a better indication.

Later, Seeker

---

### Post by rutiezer on 2009-11-13
pinging google worked ok.


There were no dependency issues this time with

sudo apt-get update       # looks like this worked fine
sudo apt-get -f install   # this did not; see below

With the second command got these errors:

invoke-rc.d: unknown initscript, /etc/init.d/ -query not found
dpkg: error processing 
/var/cache/apt/archives/libc6_2.10.1-6_i386.deb (--unpack)
subprocess new pre-installation script returned exit status 100
Errors were encountered while processing
/var/cache/apt/archives/libc6_2.10.1-6_i386.deb (--unpack)

and I stopped here.

Before doing these commands tried to install sendmail so that I could use tee to create a file of messages from each command and mail it to myself to post with replies.
Installation failed with many dependency errors. Tried to pick last dependency and install that package but that failed giving more dependcies. The dependency tree was too large for me to keep track of.

Also tried to install mail program mutt and that failed for similar reasons.

---

### Post by seeker5528 on 2009-11-13
I was afraid of something like this when you listed the services that were being restarted earlier.

Because that included the display manager, the X session was killed, and since you were doing the upgrade inside the X session, the upgrade was interrupted before the libc6 packages were completely installed.

Now it looks like in impasse, things are failing because libc6 is not completely installed and the libc6 install can't be completed because things are failing.

If 8.04 has the recovery boot, and the recovery boot has the option to attempt to repair broken packages, it's still worth a shot, but it's a very difficult situation to get around without re-installing.

Later, Seeker

---

### Post by rutiezer on 2009-11-14
Tried recovery mode.

Ubuntu 8.04.3 LTS, kernel 2.6-24-25-generic  recovery mode

Xfix  Try to fix X server

and rebooted, but back to command line.
Not sure what errors were found.

Tried again

Ubuntu 8.04.3 LTS, kernel 2.6-24-25-generic  recovery mode

then 

dpkg Repair broken packages

Saw errors with libc6 and other errors.

Reboot went to command line.


Tried other choice for recovery mode:

Ubuntu 8.04.3 LTS, kernel 2.6-24-24-generic  recovery mode

and separately tried each then reboot: 

xfix  Try to fix X server 
and
dpkg   Repair broken packages


Sounds like I need to reinstall?

Can I do that without losing the dual boot?
How?
Someone else did the dual boot for me.
One hard drive for each operating system.

I believe he first installed Ubuntu, then Windows XP.
Then tried to setup dual boot and failed.
Problems with "what is the primary drive" and Windows would not work, I think.


Then he started again, first installed Windows XP on one drive, then Ubuntu on the other. Did That succeeded. Don't know what he did.

---

### Post by seeker5528 on 2009-11-14
Yes, it sounds like you need to re-install.

If you need to move some files around from the Linux partition to the Windows partition, there is a mini distro by the name of RIP that is pretty good for that.

[http://rip.7bf.de/current/](http://rip.7bf.de/current/)

Normally when Windows is already installed it will be recognized during installation of Ubuntu and an entry added to the boot menu for it, if it doesn't get picked up for some reason, you should be able to ask about that in the forums and get it taken care of pretty easily.

Other than saving any files that you don't want to lose to another parition, the main thing is to make sure you get the right partition selected during the installation. If you have two physical hard drives there may be a basic option that allows you to select the existing hard drive and do the rest automatically. If it is a single hard drive with two partitions, you might have to use the advance option then select the existing partition where Ubuntu is currently installed. If you are not sure, it is probably better to do the advanced option so you can see what paritions exist and select from them.

When you do it, if you have questions about the partitioning, it's better to cancel before any changes are actually made and ask questions rather than to guess and find out later it was the wrong choice.

With only two partitions I don't think it should be all that hard/confusing, but if it's your first time installing you want to make sure you read things through, don't rush it. 

Later, Seeker

---

### Post by rutiezer on 2009-11-14
Thanks for your help.

Howard

---

### Post by rutiezer on 2009-11-14
Two separate hard drives, one for Windows XP, the other for Ubuntu.

---

