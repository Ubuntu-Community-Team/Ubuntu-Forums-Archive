---
title: "There seems to be a programming error in aptdaemon"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by ProfessorUnicorn on 2011-07-21
Hey, I'm new to Ubuntu, and after just a day, I'm already getting this annoying error every time I try to install or uninstall something: There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I see that many others have had this problem, and I have tried what worked for some, but nothing has pulled through :(

---

### Post by sanderj on 2011-07-21
> **ProfessorUnicorn said:**
> 
<snip>
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I see that many others have had this problem, and I have tried what worked for some, but nothing has pulled through :(

It would useful if you told what you've tried, and what the result was. Because if I now advice you to "sudo apt-get install ttf-mscorefonts-installer", and you say "I've done that already", that's not so handy for you and me ...

---

### Post by ProfessorUnicorn on 2011-07-21
Well.. I didn't exactly know what I was doing. So I want to start from the beginning. I shouldn't have even said I tried anything, sorry 'bout that. Anyways when I try that command, I get: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Hmm.. -_-

---

### Post by Krytarik on 2011-07-21
> **ProfessorUnicorn said:**
> Anyways when I try that command, I get: 

E: dpkg was interrupted, you must manually run '**sudo dpkg --configure -a**' to correct the problem. 

Hmm.. -_-
Then you should just do that:
```
sudo dpkg --configure -a
```Then handle the hopefully upcoming confirmation screen with Tab, Arrow keys and Enter.

Greetings.

---

### Post by ProfessorUnicorn on 2011-07-21
Just did that, and nothing happened, so I ran the first command again. I got this:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/34.9 kB of archives.
After this operation, 221 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 157790 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.3ubuntu3 (using .../ttf-mscorefonts-installer_3.3ubuntu3_all.deb) ...

---

### Post by sanderj on 2011-07-21
> **ProfessorUnicorn said:**
> Just did that, and nothing happened, so I ran the first command again. I got this:

<snip>

Preparing to replace ttf-mscorefonts-installer 3.3ubuntu3 (using .../ttf-mscorefonts-installer_3.3ubuntu3_all.deb) ...


... and then? Nothing, or more lines?

---

### Post by ProfessorUnicorn on 2011-07-21
Nope :( It's still up and still that's all it says.

---

### Post by Krytarik on 2011-07-21
Then try purging (removing) it:
```
sudo apt-get purge ttf-mscorefonts-installer
```And reinstalling it:
```
sudo apt-get install ttf-mscorefonts-installer
```Then do the suggested "autoremove" to get rid of the old kernel packages. You may also want to purge the related kernel image. Both of these frees up considerable disk space:
```
sudo apt-get autoremove
sudo apt-get purge linux-image-2.6.38-8-generic
```

---

### Post by ProfessorUnicorn on 2011-07-21
Ugh. I have gotten this annoying error in the past, and am getting it now when I try to put in a command:


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


When I go to system monitor to kill the apt-get process, everything freezes up for some reason and won't let me. :(

---

### Post by Krytarik on 2011-07-21
You can run only one package manager at a time, it seems like you have Synaptic running concurrently, close it. ;-)

---

### Post by ProfessorUnicorn on 2011-07-21
I don't think it is... I never opened it...

---

### Post by ProfessorUnicorn on 2011-07-21
There is no window for it up, at least. Hmm..

---

### Post by Krytarik on 2011-07-21
Is the process from post #5 actually still running? If so, and you can't stop it orderly, by pressing Ctrl+C in the respective terminal, or closing the terminal itself, or like you already tried, by stopping the process via System Monitor, I think, you may be in real trouble now. If all that fails, just try logging out, then restart, to be sure. But you may be forced to do a hard reset.

---

### Post by ProfessorUnicorn on 2011-07-21
No, I closed out of the terminal shortly after that.

---

### Post by sanderj on 2011-07-21
You could find the 'locking' process, but it's easier to reboot. After the reboot, try again. If still locked, remove the lock-file (use "sudo rm ...")>

---

### Post by ProfessorUnicorn on 2011-07-21
I have rebooted several times, and after about 5 minutes, the process starts again. So to remove the process would it be like... "sudo rm apt-get" ? I think that's the process

---

### Post by sanderj on 2011-07-21
> **ProfessorUnicorn said:**
> 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


What's the output of

```
ls -al /var/lib/dpkg/

```

Here's mine:

```
sander@R540:~$ ls -al /var/lib/dpkg/
total 7052
drwxr-xr-x  7 root root    4096 2011-07-17 08:42 .
drwxr-xr-x 70 root root    4096 2011-06-30 13:31 ..
drwxr-xr-x  2 root root    4096 2011-07-17 08:42 alternatives
-rw-r--r--  1 root root 1679398 2011-07-17 08:28 available
-rw-r--r--  1 root root 1678229 2011-07-17 08:27 available-old
-rw-r--r--  1 root root       8 2011-04-13 12:47 cmethopt
-rw-r--r--  1 root root     978 2011-04-18 08:32 diversions
-rw-r--r--  1 root root    1049 2011-04-18 08:32 diversions-old
-rw-r--r--  1 root root       1 2011-04-13 12:47 format
drwxr-xr-x  2 root root  319488 2011-07-17 08:28 info
-rw-r-----  1 root root       0 2011-07-17 08:42 lock
drwxr-xr-x  2 root root    4096 2011-03-25 01:16 parts
-rw-r--r--  1 root root     135 2011-04-13 13:03 statoverride
-rw-r--r--  1 root root     105 2011-04-13 13:00 statoverride-old
-rw-r--r--  1 root root 1738757 2011-07-17 08:42 status
-rw-r--r--  1 root root 1740859 2011-07-17 08:28 status-old
drwxr-xr-x  2 root root    4096 2011-07-17 08:42 triggers
drwxr-xr-x  2 root root    4096 2011-07-17 08:42 updates
sander@R540:~$ 
```

---

### Post by Krytarik on 2011-07-21
> **ProfessorUnicorn said:**
> I have rebooted several times, and after about 5 minutes, the process starts again.
It seems like Update Notifier keeps jumping in, try disabling it in Startup Applications.

---

### Post by ProfessorUnicorn on 2011-07-21
> **sanderj said:**
> What's the output of

```
ls -al /var/lib/dpkg/

```

Here's mine:

```
sander@R540:~$ ls -al /var/lib/dpkg/
total 7052
drwxr-xr-x  7 root root    4096 2011-07-17 08:42 .
drwxr-xr-x 70 root root    4096 2011-06-30 13:31 ..
drwxr-xr-x  2 root root    4096 2011-07-17 08:42 alternatives
-rw-r--r--  1 root root 1679398 2011-07-17 08:28 available
-rw-r--r--  1 root root 1678229 2011-07-17 08:27 available-old
-rw-r--r--  1 root root       8 2011-04-13 12:47 cmethopt
-rw-r--r--  1 root root     978 2011-04-18 08:32 diversions
-rw-r--r--  1 root root    1049 2011-04-18 08:32 diversions-old
-rw-r--r--  1 root root       1 2011-04-13 12:47 format
drwxr-xr-x  2 root root  319488 2011-07-17 08:28 info
-rw-r-----  1 root root       0 2011-07-17 08:42 lock
drwxr-xr-x  2 root root    4096 2011-03-25 01:16 parts
-rw-r--r--  1 root root     135 2011-04-13 13:03 statoverride
-rw-r--r--  1 root root     105 2011-04-13 13:00 statoverride-old
-rw-r--r--  1 root root 1738757 2011-07-17 08:42 status
-rw-r--r--  1 root root 1740859 2011-07-17 08:28 status-old
drwxr-xr-x  2 root root    4096 2011-07-17 08:42 triggers
drwxr-xr-x  2 root root    4096 2011-07-17 08:42 updates
sander@R540:~$ 
```

Mine:


drwxr-xr-x  8 root root    4096 2011-07-21 12:56 .
drwxr-xr-x 59 root root    4096 2011-07-20 11:50 ..
drwxr-xr-x  2 root root    4096 2011-07-20 19:00 alternatives
-rw-r--r--  1 root root 1488788 2011-07-20 19:17 available
-rw-r--r--  1 root root 1481684 2011-07-20 18:52 available-old
-rw-r--r--  1 root root       8 2011-04-25 17:51 cmethopt
-rw-r--r--  1 root root     978 2011-07-20 11:29 diversions
-rw-r--r--  1 root root    1049 2011-07-20 11:28 diversions-old
-rw-r--r--  1 root root       1 2011-04-25 17:50 format
drwxr-xr-x  2 root root  274432 2011-07-20 22:23 info
-rw-r-----  1 root root       0 2011-07-21 12:56 lock
drwxr-xr-x  2 root root    4096 2011-04-14 15:17 parts
-rw-r--r--  1 root root     135 2011-04-25 18:07 statoverride
-rw-r--r--  1 root root     105 2011-04-25 18:03 statoverride-old
-rw-r--r--  1 root root 1526192 2011-07-21 12:56 status
-rw-r--r--  1 root root 1526192 2011-07-21 12:56 status-old
drwxr-xr-x  2 root root    4096 2010-11-25 12:52 tmp.ci
drwxr-xr-x  2 root root    4096 2011-07-21 00:51 triggers
drwxr-xr-x  2 root root    4096 2011-07-21 12:56 updates

---

### Post by ProfessorUnicorn on 2011-07-21
> **Krytarik said:**
> It seems like Update Notifier keeps jumping in, try disabling it in Startup Applications.

I did that and rebooted, but again, It started and gave me the error when entering a command.

---

### Post by Krytarik on 2011-07-21
> **ProfessorUnicorn said:**
> I did that and rebooted, but again, It started and gave me the error when entering a command.
How about not logging in to the desktop, but switching to the console from the login screen and trying the commands there?

Therefore

[LIST=1]
[*]press Ctrl+Alt+F1 to switch to the console
[*]log in there
[*]run the commands
[*]press Ctrl+Alt+F7 or F8 to switch back to the login screen
[/LIST]

---

### Post by ProfessorUnicorn on 2011-07-21
> **Krytarik said:**
> How about not logging in to the desktop, but switching to the console from the login screen and trying the commands there?

Therefore

[LIST=1]
[*]press Ctrl+Alt+F1 to switch to the console
[*]log in there
[*]run the commands
[*]press Ctrl+Alt+F7 or F8 to switch back to the login screen
[/LIST]


I still get the lock error.

---

### Post by Krytarik on 2011-07-21
> **ProfessorUnicorn said:**
> I still get the lock error.
Ok, but is "apt-get" running there too, as you said earlier?:
```
ps ax |grep -v grep |grep apt
```If not, try removing the lock file as suggested by *sanderj*:
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by ProfessorUnicorn on 2011-07-21
> **Krytarik said:**
> Ok, but is "apt-get" running there too, as you said earlier?:
```
ps ax |grep -v grep |grep apt
```If not, try removing the lock file as suggested by *sanderj*:
```
sudo rm /var/lib/dpkg/lock
```


Sorry, this is a stupid question, but do I type the ps ax |grep -v grep |grep apt all on one line? and what do I do after that? I'm not very good at this yet, haha :)

---

### Post by Krytarik on 2011-07-21
> **ProfessorUnicorn said:**
> Sorry, this is a stupid question, but do I type the ps ax |grep -v grep |grep apt all on one line? and what do I do after that?
Yeah, as it stands in one line, one line. ;-)

Then, if "apt-get", "apt" or anything like that is running, you would an output. Since I'm not exactly sure if the process is actually called "apt-get", I left it with just "apt".

If you get an output, thus there is a process running, you can try to kill it with:
```
pkill PROCESS
```
Then try removing the lock file and try again.

---

### Post by ProfessorUnicorn on 2011-07-21
Okay I am pretty sure I closed out of apt-get with the pkill command. So what can I do about the aptdaemon error now?

---

### Post by Krytarik on 2011-07-21
> **ProfessorUnicorn said:**
> Okay I am pretty sure I closed out of apt-get with the pkill command. So what can I do about the aptdaemon error now?
If you still get the error, try this ;-) :
> **Krytarik said:**
> Then try removing the lock file and try again.

---

### Post by ProfessorUnicorn on 2011-07-21
I just installed a package! But... it wasn't without errors. Are the errors in this going to cause me problems? --


shane@ProfessorUnicorn:~$ sudo apt-get install rhythmbox
[sudo] password for shane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdmapsharing2 libmusicbrainz4c2a rhythmbox-plugin-cdrecorder
  rhythmbox-plugins
Suggested packages:
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
  rhythmbox-plugin-coherence
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following NEW packages will be installed:
  libdmapsharing2 libmusicbrainz4c2a rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins
0 upgraded, 5 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1,654 kB of archives.
After this operation, 6,107 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libmusicbrainz4c2a i386 2.1.5-4ubuntu2 [81.5 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main rhythmbox i386 0.13.3-0ubuntu6 [986 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main rhythmbox-plugin-cdrecorder i386 0.13.3-0ubuntu6 [15.8 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libdmapsharing2 i386 2.1.13-0ubuntu1 [62.3 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main rhythmbox-plugins i386 0.13.3-0ubuntu6 [509 kB]
Fetched 1,654 kB in 3s (432 kB/s)          
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 157789 files and directories currently installed.)
Removing ttf-mscorefonts-installer ...
Selecting previously deselected package libmusicbrainz4c2a.
(Reading database ... 157790 files and directories currently installed.)
Unpacking libmusicbrainz4c2a (from .../libmusicbrainz4c2a_2.1.5-4ubuntu2_i386.deb) ...
Selecting previously deselected package rhythmbox.
Unpacking rhythmbox (from .../rhythmbox_0.13.3-0ubuntu6_i386.deb) ...
Selecting previously deselected package rhythmbox-plugin-cdrecorder.
Unpacking rhythmbox-plugin-cdrecorder (from .../rhythmbox-plugin-cdrecorder_0.13.3-0ubuntu6_i386.deb) ...
Selecting previously deselected package libdmapsharing2.
Unpacking libdmapsharing2 (from .../libdmapsharing2_2.1.13-0ubuntu1_i386.deb) ...
Selecting previously deselected package rhythmbox-plugins.
Unpacking rhythmbox-plugins (from .../rhythmbox-plugins_0.13.3-0ubuntu6_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
shane@ProfessorUnicorn:~$

---

### Post by Krytarik on 2011-07-21
First, why didn't you stick to the task set in post #8!? Which was to purge and reinstall "ttf-mscorefonts-installer".

Second, the installation you've tried was *not* successful.

So, please do this:

[LIST=1]
[*]Reboot.
[*]Log in at the console as before.
[*]Make sure no "apt-get" process is running.
[*]Try purging/reinstalling "ttf-mscorefonts-installer" as per commands in post #8.
[/LIST]

---

### Post by ProfessorUnicorn on 2011-07-21
I did do that before, and It sure seems like it is.. the program is functioning fine, but sure, I'll do that.

---

### Post by Krytarik on 2011-07-21
Remember, you need to confirm any upcoming license dialog when installing "ttf-mscorefonts-installer". Otherwise, you end up in that stalled status as you were before.

---

### Post by ProfessorUnicorn on 2011-07-21
Turns out I didn't successfully do what was in post #8, like you said! Haha Thank you so much! No more errors!!! (:

---

### Post by Krytarik on 2011-07-21
Great then! Finally! :-)

---

### Post by Le Omar on 2011-08-03
Thank you guys, problems solved with me as well. :)

---

