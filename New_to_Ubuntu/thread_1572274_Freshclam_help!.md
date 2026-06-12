---
title: "Freshclam help!"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by leeannec on 2010-09-10
I cannot access permissions to run freshclam. 

here is what the problem reads:

> ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
I was messing around in the terminal (I shouldn't, I know squat about using terminals) and I ran freshclam in the root terminal and saved the action accidentally to a root file. I don't know if this did anything. Hopefully not.  :oops:

Lee Anne

---

### Post by sandyd on 2010-09-10
> **leeannec said:**
> I cannot access permissions to run freshclam. 

here is what the problem reads:

I was messing around in the terminal (I shouldn't, I know squat about using terminals) and I ran freshclam in the root terminal and saved the action accidentally to a root file. I don't know if this did anything. Hopefully not.  :oops:

Lee Anne
```

sudo touch /var/log/clamav/freshclam.log
sudo chown clamav /var/log/clamav/freshclam.log 
sudo chmod 666 /var/log/clamav/freshclam.log

```

---

### Post by leeannec on 2010-09-10
when I typed in

> sudo touch /var/log/clamav/freshclam.log 

it asked for my password and I typed it in, and hit enter, and my username@ubuntu came back up on the terminal.

I typed in the second code

> sudo chown clamav /var/log/clamav/freshclam.log

And the same error reading came up.

---

### Post by sandyd on 2010-09-10
> **leeannec said:**
> when I typed in



it asked for my password and I typed it in, and hit enter, and my username@ubuntu came back up on the terminal.

I typed in the second code



And the same error reading came up.
oops. forgot one.

---

### Post by boog321 on 2010-09-10
I had the same issue, I had to reboot. I think something makes it auto update, and it locks the file.

---

### Post by leeannec on 2010-09-10
> ERROR: Can't create temporary directory /var/lib/clamav//clamav-9fe42872084fff2e46198b3c5579fd82
Hint: The database directory must be writable for UID 1000 or GID 1000


uh oh

---

### Post by sandyd on 2010-09-10
> **leeannec said:**
> uh oh
```

chown root:root /var/lib/clamav/

```
this is why you don't randomly change permissions...

---

### Post by leeannec on 2010-09-10
> chown root:root /var/lib/clamav/
 
 this is why you don't randomly change permissions... 	

 I didn't think typing freshclam and hitting enter would randomly change the permission. All it did was list information about the program. 


> root:root: command not found

---

### Post by leeannec on 2010-09-10
This is the message I got when I entered freshclam in the root terminal

> ClamAV update process started at Fri Sep 10 21:40:37 2010
main.cvd is up to date (version: 52, sigs: 704727, f-level: 44, builder: sven)
daily.cld is up to date (version: 11867, sigs: 122571, f-level: 53, builder: neo)
bytecode.cld is up to date (version: 46, sigs: 10, f-level: 53, builder: edwin)


This is the only action I did in the root terminal. Would that change a permission?

---

### Post by leeannec on 2010-09-10
next step re-install? I'll figure it out in the morning.

---

### Post by sandyd on 2010-09-10
> **leeannec said:**
> I didn't think typing freshclam and hitting enter would randomly change the permission. All it did was list information about the program.
type the entire thing.

---

### Post by leeannec on 2010-09-11
> **sandyd said:**
> type the entire thing.

type the entire thing...

I did use your first codes

sudo touch /var/log/clamav/freshclam.log sudo chown clamav /var/log/clamav/freshclam.log  sudo chmod 666 /var/log/clamav/freshclam.log
and now I get this if I type in freshclam.

> ERROR: Can't create temporary directory /var/lib/clamav//clamav-9fe42872084fff2e46198b3c5579fd82
Hint: The database directory must be writable for UID 1000 or GID 1000 			 		

So perhaps it's not the permissions at this point.

---

### Post by wizandrew on 2010-11-20
hello i have a similar problem with klamav 0.46 (clamav 0.96.3) it wont update!

running (also with sudo)  freshclam returns:
```
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

```i tried to reinstall it already happens during the installation:
```
Preconfiguring packages ...
Selecting previously deselected package libclamav6.
(Reading database ... 182681 files and directories currently installed.)
Unpacking libclamav6 (from .../libclamav6_0.96.3+dfsg-2ubuntu1.1_amd64.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.96.3+dfsg-2ubuntu1.1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.96.3+dfsg-2ubuntu1.1_amd64.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.96.3+dfsg-2ubuntu1.1_amd64.deb) ...
Selecting previously deselected package klamav.
Unpacking klamav (from .../klamav_0.46-3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Setting up libclamav6 (0.96.3+dfsg-2ubuntu1.1) ...
Setting up clamav-base (0.96.3+dfsg-2ubuntu1.1) ...
Setting up clamav-freshclam (0.96.3+dfsg-2ubuntu1.1) ...
 * Starting ClamAV virus database updater freshclam                             ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
                                                                         [fail]
Setting up clamav (0.96.3+dfsg-2ubuntu1.1) ...
Setting up klamav (0.46-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```i am running kubuntu 10.10 x64
tried changing permissions for freshclam.log didn't help... :(

running kalmav as a regular user grays out the update button and as root u get update process died unexpectedly did you kill it manually?
any ideas?

p.s.
after ready this [http://ubuntuforums.org/showthread.php?t=1547713](http://ubuntuforums.org/showthread.php?t=1547713)
it changes the database dir and now i can press the update button when u run klamav (as regular user not root) however it now says: "unknown option passed"
running freshclam returns the same error as before.

---

### Post by rburkartjo on 2010-11-21
lee try this open your home folder chick the show hidden files option delete .clamtk
then delete the whole program and reinstall. just an idea

---

### Post by wizandrew on 2010-11-22
> **rburkartjo said:**
> lee try this open your home folder chick the show hidden files option delete .clamtk
then delete the whole program and reinstall. just an idea
no such dir....

---

