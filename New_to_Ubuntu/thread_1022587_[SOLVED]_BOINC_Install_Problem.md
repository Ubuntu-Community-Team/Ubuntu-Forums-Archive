---
title: "[SOLVED] BOINC Install Problem"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by ritterm on 2008-12-27
Hi All,

I'm brand new to Linux and just managed to install Ubuntu on an old PC (separate partition, dual-boot w/Win XP).  That fact alone is a testament to how well the install CD and documentation was put together! :)

Anyway, I'm having trouble installing and running the BOINC client and manager.  I'm following the [[COLOR="RoyalBlue"]instructions[/COLOR]]("http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu") given at the BOINC website to do the install from the Ubuntu repository, but it's not successful.  Here's the output I get following the install command:

ritterm@linuxbox:~$ sudo aptitude install boinc-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  boinc-client{a} boinc-manager 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2195kB of archives. After unpacking 6054kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package boinc-client.
(Reading database ... 102745 files and directories currently installed.)
Unpacking boinc-client (from .../boinc-client_6.2.12-1_i386.deb) ...
Selecting previously deselected package boinc-manager.
Unpacking boinc-manager (from .../boinc-manager_6.2.12-1_i386.deb) ...
Processing triggers for man-db ...
Setting up boinc-client (6.2.12-1) ...
 * Starting BOINC core client: boinc                                                                      [ OK ] 
 * Setting up scheduling for BOINC core client and children:                                              [ OK ] 

Setting up boinc-manager (6.2.12-1) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

ritterm@linuxbox:~$

Continuing with the instructions, I entered the command to start the client as a daemon at boot time:

ritterm@linuxbox:~$ /sbin/chkconfig boinc-client on
bash: /sbin/chkconfig: No such file or directory

I then tried to manually start the client daemon (per the instructions) and again, no joy:

ritterm@linuxbox:~$ /sbin/service boinc-client start
bash: /sbin/service: No such file or directory

I've tried this process several times, all with the same result.  I used the synaptic package manager to remove previous installations and even tried the install using synaptic.

Thanks for any help.

MarkR

---

### Post by -kg- on 2008-12-27
I don't remember having such problems.

When you click on "Applications" on the top toolbar (if you're running the Gnome version), is there a "System Tools" in the drop down menu? If so, you'll likely find the BOINC Manager already running there.

All you have to do then is connect to your projects and set whatever local preferences.  Normally BOINC runs automatically at boot time and you don't have to manually launch it.

---

### Post by -kg- on 2008-12-27
I just re-read your post.

I did my BOINC install from the Synaptic Package manager.  While it isn't bleeding edge with the absolute latest distribution of BOINC, it is set up to automatically load and be ready to run if you install it with Synaptic.

Just go into Synaptic and do a "Search" for BOINC.  It will find the package for you which you check the box then "Apply" and it will automatically install BOINC.  It will then be running as I described before.

---

### Post by XCan on 2008-12-27
I believe you need to install the boinc-client as well, which is also available through synaptics. :)

---

### Post by -kg- on 2008-12-27
> I believe you need to install the boinc-client as well, which is also available through synaptics.

Yep.  I'm pretty sure that if you checked the BOINC Manager box that the BOINC Client would likely be one of the dependencies, though you might be able to install the client without the Manager.

You'll want them both, though, in any case.

---

### Post by ritterm on 2008-12-27
Thanks for the input kg and XCan. :)

Okay...Following the [instructions]("http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu") at the BOINC website, I installed the  package from the Ubuntu repository.  Then I entered the commands to manually start the client daemon and set it to start at boot time; however, both attempts failed because the commands aren't in the /sbin directory.

Having tried that, I brought up synaptic and it indicated that both the client and manager had been installed.  I used synaptic to remove completely and reinstall both.  Still, the commands to start and load at boot fail.  So, at this point, I'm thinking that the install didn't work or wasn't complete.

After starting this thread and reading kg's post suggesting to check System Tools, I did so, and there was the BOINC manager.  I was able to start the manager and connect to all of my projects.  I don't know yet if the client daemon will start on re-boot.

---

### Post by oldsoundguy on 2008-12-28
you have to have both client and manager installed or you can not set your preferences or attach to projects.  Once installed you will find it under the applications> systems tools.  Just click on it to start up the set up procedure.

---

### Post by ritterm on 2008-12-28
The instructions provided at the BOINC website were in error for installing from the Ubuntu repo, in that they included commands for an install under Red Hat (those have since been edited out).  Also, there is no mention of starting the manager from Applications -> System Tools -> BOINC Manager.

Based on my newbie experience, it looks like you can do a successful install from the command line or through synaptic, and the Ubuntu install starts the client daemon at boot time, by default.  (Note that the version in the repo is 6.2.12, a pre-release.)

Thanks for everybody's input -- I've managed to move up the learning curve a bit... :)

---

### Post by ritterm on 2008-12-28
For those interested in a little more info, here's [my cross-post]("http://boinc.berkeley.edu/dev/forum_thread.php?id=3456#22134") in the BOINC forum.  Also, the [wiki]("http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu") at the BOINC website for the Ubuntu install has been updated.

---

### Post by ritterm on 2008-12-28
> **-kg- said:**
> Yep.  I'm pretty sure that if you checked the BOINC Manager box that the BOINC Client would likely be one of the dependencies
That is correct.

---

