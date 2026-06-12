---
title: "fwbackups installation"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by longtom on 2009-07-26
Hi,

fwbackups is something which looks just about right for my purpose.  However - it doesn't appear to be in the repositories and googling didn't get me anywhere either.

It is available as download for windows or as source.  Has anybody installed it before in Ubuntu and point me in the correct direction to install it myself?  I'd love to test this program and see what it can do.

So far I am using Cobian (and because of that have a windows machine running).  This looks close to Cobian (which I like) and I could potentially run it in Ubuntu.

If it would be easier to run it in some other flavour of Linux - I would give that a shot as well.

Thank you.

---

### Post by longtom on 2009-07-26
I figured it out myself and once I have it running I will certainly share what I did.  I didn't see any error messages and assume my compilatiopn was successful.  What bafles me a bit is, that the Windows install file is 22MB and the source file 500 odd KB....

In the meantime I have to search where this program is.....*scratch

---

### Post by Liolikas on 2009-07-26
Try fwbackups command.

---

### Post by longtom on 2009-07-26
> **Liolikas said:**
> Try fwbackups command.

Tried that.  This is what I get:

```

Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 59, in <module>
    from fwbackups import backend
  File "/usr/local/lib/python2.5/site-packages/fwbackups/backend.py", line 26, in <module>
    import paramiko
ImportError: No module named paramiko

```

hmm....anybody?

---

### Post by Liolikas on 2009-07-26
That is *.
You will have to deal with deps manually.

ImportError: No module named paramiko
Google for paramiko:
[http://www.lag.net/paramiko/](http://www.lag.net/paramiko/)
You need it. 
But better try to find it in package manager (apt-get it) and install in this way, because you may end up with 100 deps compilation and installation or worse like circular deps.

---

### Post by longtom on 2009-07-26
> **longtom said:**
> Tried that.  This is what I get:

```

Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 59, in <module>
    from fwbackups import backend
  File "/usr/local/lib/python2.5/site-packages/fwbackups/backend.py", line 26, in <module>
    import paramiko
ImportError: No module named paramiko

```

hmm....anybody?

figured that one out - install python-paramiko.  No I have this one:

```

<class 'gobject.GError'>: Failed to open file '/usr/share/pixmaps/fwbackups.svg': No such file or directory

```

Is that the hell of dependencies one has to go through they were talking about back in the days?

---

### Post by Liolikas on 2009-07-26
You do job in Slackware 1994 way. :)
But no problem really someone even today have to create *.deb files from source so basically complete all this hell for everyone.

Fedora 11 has *.rpm for this program ([https://admin.fedoraproject.org/pkgdb/packages/name/fwbackups?_csrf_token=954a858b743d608556f3be7074a2b371628b4f8c#Fedora11](https://admin.fedoraproject.org/pkgdb/packages/name/fwbackups?_csrf_token=954a858b743d608556f3be7074a2b371628b4f8c#Fedora11)).
All you have to do is install rpm somehow on ubuntu:
[http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/](http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/)

---

### Post by longtom on 2009-07-26
Right - got it going.  So for the benefit of those coming here via Google - this is what I did.

1. Download the file fwbackups-1.43.2.tar.gz from [http://www.diffingo.com/oss/fwbackups](http://www.diffingo.com/oss/fwbackups)

2. Install gettext via Synaptic (or any other means you fancy).

3. Install python-paramiko.

4. Follow [this guide](https://help.ubuntu.com/community/CompilingEasyHowTo) (./configure, make, sudo make install)

5. Move or copy as administrator the directory ***fwbackups*** from ***usr/local/share*** to ***usr/share***

6. Move or copy as administrator the files ***fwbackups, fwbackups-run, fwbackups-runonce*** from the directory ***usr/local/bin*** to the directory ***usr/bin*** 

7. Go to the terminal and type: **fwbackups** or go to **System>Preferences>fwbackups**.


Should be firing up.  I made some tests.  It always gives me an error in the program itself after the backup (An error occurred while running a subprocess!).  However, the backup is in good order.  I always backup without compression - so I haven't tested compression yet.

In this week I will put Ubuntu on a PC and test it on a bigger network with schedules - see how it does.

Haven't got it to read my mixed network yet, so one would have to use fstab to get it to backup Folders from a network.  That's a bit of a showstopper.

Any suggestions and help will be appreciated.

---

### Post by BDNiner on 2009-07-26
I followed your guide but was unsuccessful at installing the application properly. It get an error when I run 'fwbackups' from the terminal
```

bdniner@kabalagala:~$ fwbackups
python: can't open file '/fwbackups/fwbackups-runapp.pyw': [Errno 2] No such file or directory

```

I didn't think that a file called fwbackups-runapp.pyw was created. I am looking into it now.

---

### Post by longtom on 2009-07-27
> **BDNiner said:**
> I followed your guide but was unsuccessful at installing the application properly. It get an error when I run 'fwbackups' from the terminal
```

bdniner@kabalagala:~$ fwbackups
python: can't open file '/fwbackups/fwbackups-runapp.pyw': [Errno 2] No such file or directory

```

I didn't think that a file called fwbackups-runapp.pyw was created. I am looking into it now.

Search the file on your machine.  This is how I figured that I needed to move some files and directories into usr/share and usr/bin.

Check your terminal when you compile and comb it to make sure compiling, making and installing went without an error.

I'll search for your missing file here and let you know once I found it.

---

### Post by longtom on 2009-07-27
Mine is in usr/share/fwbackups.

You should have a look if your fwbackups directory is not in usr/local/share.  It should be in **usr/share**.

Just have a look at point 5 of my installation post and also cast your eye at post 6.

If that is not helping and you got it going anyway, let us know how.

---

### Post by BDNiner on 2009-07-27
Ok, I will give it a try when i get home. I am trying to install version 1.43.3 release candidate 2. Not the last stable version because I am backing up to a NAS, and there are supposedly bugs with remote backups in version 1.43.2

---

### Post by chronos00 on 2009-07-27
I am starting to wonder if this app is really worth all this hasle.

You can find here: [http://blogs.techrepublic.com.com/10things/?p=895](http://blogs.techrepublic.com.com/10things/?p=895)
the top 10 backing up utilities for linux, being fwbackup the first.

Regrettably, it is not in the repos... reason enough for me not to use it...


On the other hand, the second app in the top ten (Bacula) is in the repos, but it's installation failed for me in two different systems.

Has anyone had any luck with this or other back up software?

---

### Post by firewing1 on 2009-07-27
I'm glad to hear you're interested in fwbackups (I'm the author) :)

I'm sorry about the troubles you're having, I test mainly on Fedora, Windows and OS X although I should really test on Ubuntu as well... I installed Ubuntu 9.04 a few days ago, so when 1.43.3rc3 is released installing fwbackups will be much smoother.

I am going to add generic dependency information on the fwbackups website later today, but python-paramiko, python-notify and python-gtk2 are the packages you'll need to run fwbackups under Ubuntu. For Fedora it the glib2-devel and gnome-doc-utils packages are also required to build form source, so if the build fails try installing the Ubuntu equivalents of these (libglib2-dev and gnome-doc-utils). Here is how you can install fwbackups in a few steps:```

apt-get install intltool gnome-doc-utils python-paramiko python-notify python-gtk2
wget http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
tar xfj fwbackups-1.43.3rc2.tar.bz2
cd fwbackups-1.43.3rc2
./configure --prefix=/usr --datadir=/usr/share
make && sudo make install
```

I've attached a patch to fix a problem with one-time backups in 1.43.3rc2 to this post, if you wish to apply it then download the file to the "fwbackups-1.43.3rc2" folder in your home and run this command before "make":
```
patch -p1 < fwbackups-1.43.3rc2-onetime.txt
```

Earlier in the discussion there was a question about why the Windows installers are so large - this is actually because Windows doesn't come with Python, GTK or cron preinstalled like most Linux distros do. So in addition to fwbackups which is quite small by itself (~500kB), I need to include a full GTK+ and Python installation!

Stewart

---

### Post by BDNiner on 2009-07-28
Yeah I installed fwbackups using wine and saw all the other applications it installed along side the software. Thank you for your reply firewing1. I can't wait to try this when I find sometime tonight, or maybe tomorrow. I read the article on the techrepublic blog as well and that is what made me try and install your software.

---

### Post by BDNiner on 2009-07-28
Thanks for the instructions firewing1 it seemed to have worked I was able to run the application. There are no error messages when I run it from the terminal.

---

### Post by BDNiner on 2009-07-28
But I do get an error message when I try to backup some files to my NAS. My Nas does not support SSH (until I hack it). So I have mounted some folders to /media/. This is where I am trying to save a backup.

After configuring the backup and then running it nothing happens! The status says working, but no files are being copied, there is no network traffic. The log says
```

Jul 28 19:26:09 :: INFO : Starting automatic backup operation of set `Documents Backups'

```

And sits there for a while. The longest I let it run was 30 minutes. When I close the application I get the error message 
```

/usr/lib/python2.6/dist-packages/fwbackups/widgets.py:146: GtkWarning: gtk_text_layout_get_iter_location: assertion `GTK_IS_TEXT_LAYOUT (layout)' failed
  self.textview.scroll_to_iter(self.buffer.get_end_iter(), 0.0)

```
I ran it again and got
```

/usr/lib/python2.6/dist-packages/fwbackups/widgets.py:146: GtkWarning: gtk_text_layout_get_iter_location: assertion `GTK_IS_TEXT_LAYOUT (layout)' failed
  self.textview.scroll_to_iter(self.buffer.get_end_iter(), 0.0)

```
and a bug report was saved to
```

fwbackups bug report written saved at 07:30 PM on 2009-07-28

Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 1367, in on_main2BackupSetNowButton_clicked
    self.startSetBackup()
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 2426, in startSetBackup
    time.sleep(0.01)
KeyboardInterrupt

```

Is there somewhere else you would like me to send the info?

---

### Post by firewing1 on 2009-07-28
The first two errors are GTK warnings about widgets, so that's nothing to worry about concerning the backup. The error during the backup was a KeyboardInterrupt which means ctrl+c was pressed to interrupt the program - this is normal if you did so.

By default, fwbackups logs all error messages and won't print them to the terminal. If you open fwbackups, do you see any relevant messages in the "Log Viewer" tab? If not, try enabling debug messages (under Edit > Preferences) and try running the backup again to see if there are any additional debug messages.

BTW - If you want messages to also be printed to the terminal, run fwbackups with the --verbose argument :)

---

### Post by BDNiner on 2009-07-28
Ok, I am making some progress. I have gotten the One-Time Backup feature to work. I can copy files to my NAS so long as I archive the files first. When I tried to copy over the directory structure I got an rsync error about creating timestamps, I have figured out that I need to take ownership of that folder inorder for rsync to create a timestamp on the files that I am copying over. I will figure that one out.

The backup sets feature I what I was trying to run before and I guess it is more that I don't understand exactly what I am doing. After creating the schedule for the backup and I select 'backup now' does it wait for the time I set to run the backup? I was under the impression that it creates a backup at this moment and then when the set time matches the system clock. Maybe that is why nothing happens?

---

### Post by BDNiner on 2009-07-28
I guess because is mounted the folder in /media/ I can not change the ownership. I remounted the folder in my home directory and I am not getting the rsync errors. When I start a Backup Set the status is 'working' and the Backup Progress is 'Cleaning Old Backups'. I will let it run for a while and see if anything is backed up.

---

### Post by firewing1 on 2009-07-28
I'm glad to hear one-time backups are working. Like you thought backup sets will start automatically at the times specified, and clicking "Backup now" should start the backup immediately regardless of the schedule. Depending on the format of previous backups, removing old backups could take a bit of time to complete but usually not more than a few minutes... If after 10 minutes nothing has changed, see if the the log has any errors.

If it's not working, one thing to test would be to try to do a local backup out of the networked mount and see if that works - although theoretically a mounted network filesystem should work fine, I haven't tested this (I've only programmed SFTP for remote backups).

---

### Post by BDNiner on 2009-07-28
After letting it run for a half hour nothing was copied to the remote folder. The last thing in the error log was 
```

Jul 28 21:19:56 :: DEBUG : Parsing configuration files
Jul 28 21:20:04 :: INFO : Starting automatic backup operation of set `test'
Jul 28 21:20:04 :: DEBUG : Destination folder `/home/bdniner/fwbackups' exists

```
I created a new backup schedule and set it to backup to a local folder in my home directory. After 10 minutes nothing has happened. The same message is displayed in the log file just relating to the new directory.
```

Jul 28 22:48:42 :: DEBUG : Parsing configuration files
Jul 28 22:48:45 :: INFO : Starting automatic backup operation of set `test'
Jul 28 22:48:45 :: DEBUG : Destination folder `/home/bdniner/Public' exists

```
It seems like nothing happens after it checks that the directory exists. Gotta get up early for work, I will attempt to run it again tomorrow.

---

### Post by firewing1 on 2009-07-28
I'm not sure what's happening, but if you can test backing up a local directory (outside the network mount) and let me know how that works, I may be able to help troubleshoot this. This is most probably some sort of bad interaction between the tar/rsync processes fwbackups calls and the network mount.

---

### Post by BDNiner on 2009-07-29
Ok, when I get off work I will run some more tests. I will also see if I can create a DEB when compiling the program so that other users can try it out.

---

### Post by firewing1 on 2009-07-29
That would be great! I'm very familiar with building RPMs but not so much for the debian packaging so I've never created any debs for fwbackups. You may want to communicate with Olivier Hervieu, he also offered to package fwbackups in Launchpad: [https://bugs.launchpad.net/bugs/298942](https://bugs.launchpad.net/bugs/298942)

---

### Post by BDNiner on 2009-07-29
OK, I tried to create a backup set that would backup files from a local directory in my home folder to another local directory in my home folder compressing them into a tar archive. after letting it run for 10 minutes the Backup Progress says please wait.. but there is nothing in the log viewer indicating that something is happening and the folder I am backup to is empty

---

### Post by firewing1 on 2009-07-29
How large are the files you're compressing? Unfortunately there's no way to offer a progress when using tar and compression, so it will always say "Please wait..." until it finishes compressing.

---

### Post by BDNiner on 2009-07-29
Oh ok. I am compressing 144 files about 70MB of data for this test. I will let it run until I get some kind of response.

---

### Post by firewing1 on 2009-07-30
Something doesn't sound right about 10 minutes for 70MB though... I just tested on OSX and my Ubuntu install, it works in OS X but not Ubuntu. I'll investigate some more and let you know what's going on.
Edit: Found the problem; If package lists are enabled in the backup options and dpkg is present on the system, the backup job stalls because "dpkg -l" generated too much output at once. I've fixed this in git, but a workaround in the mean time is just to untick the "Print package lists to file" checkbox in the backup options.

---

### Post by BDNiner on 2009-07-30
Thank you for your time. Unticking the option "print package lists to file" worked. I am now able to use the backup sets option to backup to a local directory. I am still getting rsync errors when backing up to the network share. I will investigate the permissions and see if I can figure that out.

*I ended up taking ownership of the share when I boot the computer so now I don't get the rsync errors. This is a great product thank you for your hard work!*

---

### Post by MScapee on 2009-08-09
Firewing1,  I tried your instructions (including the patch) and everything worked up to the make which then failed with lots of "fireworks".  I suspect that the reason for this is because I'm trying to install fwbackups under the ubuntu 9.04 live cd.  Below is everything that spewed forth from make.  As I'm a Linux newb, it's mostly Greek to me. ;-)

```
root@ubuntu:~/fwbackups-1.43.3rc2# make && sudo make install
cd . && /bin/bash /root/fwbackups-1.43.3rc2/missing --run aclocal-1.10 
configure.ac:18: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
 cd . && /bin/bash /root/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
gnome-doc-utils.make:74: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:74: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:77: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:77: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:110: if $(DOC_USER_FORMATS: non-POSIX variable name
gnome-doc-utils.make:110: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: if $(filter environment,$(origin LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: filter $(LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: shell xmllint --format $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: notdir $(patsubst %/$(notdir $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: if $(_ENABLE_SK: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: wildcard $(_DOC_ABS_SRCDIR: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:173: call db2omf_args,$@,$<,'docbook': non-POSIX variable name
gnome-doc-utils.make:173: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:188: call db2omf_args,$@,$<,'xhtml': non-POSIX variable name
gnome-doc-utils.make:188: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter docbook,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:206: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:206: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:210: foreach ent,$(DOC_ENTITIES: non-POSIX variable name
gnome-doc-utils.make:210: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:214: foreach inc,$(DOC_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:214: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: if $(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: foreach fig,$(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: patsubst $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:237: foreach f,                        \
gnome-doc-utils.make:237:     $(shell xsltproc --xinclude             \
gnome-doc-utils.make:237:       --stringparam db.chunk.basename "$(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:237: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach inc,$(_DOC_C_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: notdir $(inc: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach doc,$(_DOC_C_HTML: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: notdir $(doc: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:274: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:274: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: patsubst C/%,$(lc: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach fig,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: patsubst C/%,%,$(fig: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:288: dir $@: non-POSIX variable name
gnome-doc-utils.make:288: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:318: dir $@: non-POSIX variable name
gnome-doc-utils.make:318: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:319: notdir $@: non-POSIX variable name
gnome-doc-utils.make:319: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:328: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:328: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:340: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:340: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:343: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:343: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:346: patsubst %.xhtml,%.xml,$@: non-POSIX variable name
gnome-doc-utils.make:346: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:385: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:385: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:386: if $(_DOC_DSK_IN: non-POSIX variable name
gnome-doc-utils.make:386: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:387: if $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:387: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:388: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:388: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:505: patsubst C/%,%,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:505: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
cd . && /bin/bash /root/fwbackups-1.43.3rc2/missing --run autoconf
configure.ac:18: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make: *** [configure] Error 1
```I sure hope to figure out what's going on as I'd really like to try out this software.  It looks quite promising.  Thanks in advance to anyone who can help...

---

### Post by firewing1 on 2009-08-10
Hi MScapee,

If you visit the fwbackups homepage ([www.fwbackups.com](www.fwbackups.com)), you can download version 1.43.3rc3 which I released a few days ago. It's much better tested under Ubuntu and should compile easier - just do:```

./configure --prefix=/usr
make
sudo make install
```
You will need the "intltool" and "gettext" packages to install it though. If these aren't pre-installed on the LiveCD, you can easily install them via Synaptics.

---

### Post by SilverWave on 2009-08-22
Hmm when trying to download I get a Server Not Found Error:
Firefox can't find the server at 
downloads.diffingo.com.

I saw an article on the Top Ten Backup Solutions and fwbackups was top so I thought I would have a look...

Here is my present solution:

[RLB (Rsync Local Backup). An easy way to backup your system RLB This script is the result of wanting a simple backup solution. For this I needed an efficient way of running rsync for local backups.](http://ubuntuforums.org/showthread.php?t=912460)

---

### Post by BDNiner on 2009-08-29
I just compiled rc4 and am getting some errors when attempting to back
```

Aug 29 20:13:29 :: INFO : Log cleared
Aug 29 20:13:36 :: INFO : Starting automatic backup operation of set `kabalagala backup'
Aug 29 20:13:36 :: DEBUG : Destination folder `/home/bdniner/fwbackups' exists
Aug 29 20:13:36 :: DEBUG : Thread returned with retval -1
Aug 29 20:13:36 :: WARNING : There was an error while performing the backup! Enable debug messages for more information.
Aug 29 20:13:36 :: DEBUG : Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/fwbackups/__init__.py", line 121, in run
  File "/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py", line 615, in start
  File "/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py", line 112, in createPkgLists
TypeError: execute() got an unexpected keyword argument 'stdoutfd'

Aug 29 20:13:36 :: INFO : Canceling the current operation!
Aug 29 20:13:39 :: DEBUG : Parsing configuration files

```
I am going to downgrade back to rc3 since i really need to make a backup and then try rc4 again.

---

### Post by BDNiner on 2009-08-30
Actually the computer died this morning. So it will be a while before I can afford to replace the MB, CPU and RAM. I am thinking of upgrading so. Once I have everything setup again you may be on the finaly release anyways.

---

### Post by alex_time on 2009-09-04
> **BDNiner said:**
> I just compiled rc4 and am getting some errors when attempting to back
```

Aug 29 20:13:29 :: INFO : Log cleared
Aug 29 20:13:36 :: INFO : Starting automatic backup operation of set `kabalagala backup'
Aug 29 20:13:36 :: DEBUG : Destination folder `/home/bdniner/fwbackups' exists
Aug 29 20:13:36 :: DEBUG : Thread returned with retval -1
Aug 29 20:13:36 :: WARNING : There was an error while performing the backup! Enable debug messages for more information.
Aug 29 20:13:36 :: DEBUG : Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/fwbackups/__init__.py", line 121, in run
  File "/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py", line 615, in start
  File "/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py", line 112, in createPkgLists
TypeError: execute() got an unexpected keyword argument 'stdoutfd'

Aug 29 20:13:36 :: INFO : Canceling the current operation!
Aug 29 20:13:39 :: DEBUG : Parsing configuration files

```I am going to downgrade back to rc3 since i really need to make a backup and then try rc4 again.

I have the same problem....any tips?! I'm using 1.43.3rc4

---

### Post by BDNiner on 2009-09-04
I think it may have been an update that was installed. I downgraded to both rc3 and rc2 and I am getting the same error. I guess I will completely purge the installation and try again this weekend.

---

### Post by alex_time on 2009-09-04
> **BDNiner said:**
> I think it may have been an update that was installed. I downgraded to both rc3 and rc2 and I am getting the same error. I guess I will completely purge the installation and try again this weekend.

Tryed the rc3 too and got the same result like you...

---

### Post by derek.eder on 2009-09-07
Hello ... may I join the crowd? 

I have just installed fwbackups-1.43.3rc4 under Ubuntu 9.04 (AMD64).  While I can start Fwbackups, attempts to perform a backup fail with the following error messages (see below).  Note that the same thing happens when I try "One-Time Backup".

For what it is worth, running Fwbackups as root doesn't work either.

Any suggestions and help would be greatly appreciated!

 ~Derek


-- Current session's log messages --

Sep 07 17:34:39 :: DEBUG : Parsing configuration files
Sep 07 17:34:43 :: INFO : Starting automatic backup operation of set `projects'
Sep 07 17:34:43 :: DEBUG : Destination folder `/home/derek/sockeyeBackup' exists
Sep 07 17:34:43 :: DEBUG : Thread returned with retval -1
Sep 07 17:34:43 :: WARNING : There was an error while performing the backup! Enable debug messages for more information.
Sep 07 17:34:43 :: DEBUG : Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/fwbackups/__init__.py", line 121, in run
    retval = self.__functorun(*self.__args)
  File "/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py", line 615, in start
    managers = self.createPkgLists()
  File "/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py", line 99, in createPkgLists
    retval, stdout, stderr = fwbackups.execute('rpm -qa', env=self.environment, shell=True, stdoutfd=fh)
TypeError: execute() got an unexpected keyword argument 'stdoutfd'

Sep 07 17:34:43 :: INFO : Canceling the current operation!
Sep 07 17:34:50 :: DEBUG : Parsing configuration files

---

### Post by firewing1 on 2009-09-08
Hi,

The current release is 1.43.3rc4, it should be completely working in Ubuntu except for one bug which affects all Linux distros if the "print X" options are enabled in the backup. A patch (and instructions for applying it) are available at the known issues page:
[http://www.diffingo.com/oss/fwbackups/documentation/known_issues](http://www.diffingo.com/oss/fwbackups/documentation/known_issues)

Stewart

---

### Post by BDNiner on 2009-09-08
Thank you for your response firewing1. I never check your actually page for solutions. Will do from now on. I had to reinstall anyways so I will try and recompile this tonight and see how it goes.

---

### Post by mathguy1 on 2009-09-19
Thanks so much firewing1 and longtom for the great instructions! Installation and backup worked without error for me on Debian Lenny with firewing1's latest patch/workaround.

---

### Post by derek.eder on 2009-09-19
I have installed 1.43.3rc4 (unpatched) on 2 Ubuntu systems (32 and 64 bit 9.04) and Windows XP without any major problems.

(1)  One persistent problem I have on the Linux systems (does not apply to Windows) is that I am unable to make incremental backups.  The "incremental backups" option is not save to the configuration after setting it and the "old" backup file is always removed first when I run the backup set.  I see from the net that this problem was also observed on a Redhat installation.

As I want to backup a rather large set of work every day (it takes Fwbackups about 20 minutes to Gzip the 20 GB), incremental backups are more convenient.

(2)  I also tried backing up to a remove server using the SSH option, but then Fwbackups would not even let me select the "incremental backups" option (like as in Windows) - perhaps this is documented (I have not looked :).

(3)  Windows installers have to be careful where they extract one of the Python add-on zip archives to.  I don't remember any of the details, but you have to extract the files to the directory the instructions tell you to (duh) when unZip will want to put these in a new subdirectory.

(4)   Linux people who want to start a backup run and then have their computers shut down afterwards can use the advanced options -- "commands to use after backup".

For example:  "shutdown -P + 120"  (remove the quotes) will powerdown the system after 120 minutes

One caveat, you have to be root to shutdown unless you change the permission of shutdown thusly:  "sudo chmod u+s /sbin/shutdown"

---

### Post by craig.brisbane on 2009-09-27
Hi
I followed the instructions on the forum and after installing entered fwbackups at the prompt, this is the message I received-

$fwbackups
Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const

What do I need to do to get fwbackups working?

Craig

---

### Post by Morty007 on 2009-11-21
Just wanted to say that I've been trying now for 30 minutes to get this thing installed. I don't know how to compile really, but since it's not on getdeb or in synaptic I can only spend so much time.

Why can't things be simpler?

---

### Post by BDNiner on 2009-11-23
> **Morty007 said:**
> Just wanted to say that I've been trying now for 30 minutes to get this thing installed. I don't know how to compile really, but since it's not on getdeb or in synaptic I can only spend so much time.

Why can't things be simpler?

Compiling code is as simple as it can get. What error messages/ issues are you having when compiling the software? Did you read through this entire topic to make sure you have all the dependencies?

---

### Post by BDNiner on 2009-11-23
Have either of you followed the instructions from post #14 to install the application. Those are the instructions that I used to install fwbackups.

```

apt-get install intltool gnome-doc-utils python-paramiko python-notify python-gtk2
wget http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
tar xfj fwbackups-1.43.3rc2.tar.bz2
cd fwbackups-1.43.3rc2
./configure --prefix=/usr --datadir=/usr/share
make && sudo make install

```

---

### Post by Morty007 on 2009-11-23
Here is what I get when trying:


[HTML]marc@marc-laptop:~$ apt-get install intltool gnome-doc-utils python-paramiko python-notify python-gtk2
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
marc@marc-laptop:~$ wget http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
--2009-11-23 19:47:07--  http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
Resolving downloads.diffingo.com... 174.142.61.37
Connecting to downloads.diffingo.com|174.142.61.37|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 412234 (403K) [application/x-bzip2]
Saving to: `fwbackups-1.43.3rc2.tar.bz2'

100%[======================================>] 412,234      287K/s   in 1.4s    

2009-11-23 19:47:09 (287 KB/s) - `fwbackups-1.43.3rc2.tar.bz2' saved [412234/412234]

marc@marc-laptop:~$ tar xfj fwbackups-1.43.3rc2.tar.bz2
marc@marc-laptop:~$ cd fwbackups-1.43.3rc2
marc@marc-laptop:~/fwbackups-1.43.3rc2$ ./configure --prefix=/usr --datadir=/usr/share
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/operations/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE
marc@marc-laptop:~/fwbackups-1.43.3rc2$ make && sudo make install
cd . && /bin/bash /home/marc/fwbackups-1.43.3rc2/missing --run aclocal-1.10 
configure.ac:18: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
 cd . && /bin/bash /home/marc/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
gnome-doc-utils.make:74: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:74: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:77: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:77: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:110: if $(DOC_USER_FORMATS: non-POSIX variable name
gnome-doc-utils.make:110: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: if $(filter environment,$(origin LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: filter $(LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: shell xmllint --format $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: notdir $(patsubst %/$(notdir $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: if $(_ENABLE_SK: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: wildcard $(_DOC_ABS_SRCDIR: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:173: call db2omf_args,$@,$<,'docbook': non-POSIX variable name
gnome-doc-utils.make:173: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:188: call db2omf_args,$@,$<,'xhtml': non-POSIX variable name
gnome-doc-utils.make:188: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter docbook,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:206: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:206: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:210: foreach ent,$(DOC_ENTITIES: non-POSIX variable name
gnome-doc-utils.make:210: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:214: foreach inc,$(DOC_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:214: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: if $(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: foreach fig,$(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: patsubst $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:237: foreach f,						\
gnome-doc-utils.make:237: 	$(shell xsltproc --xinclude 			\
gnome-doc-utils.make:237: 	  --stringparam db.chunk.basename "$(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:237: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach inc,$(_DOC_C_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: notdir $(inc: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach doc,$(_DOC_C_HTML: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: notdir $(doc: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:274: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:274: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: patsubst C/%,$(lc: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach fig,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: patsubst C/%,%,$(fig: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:288: dir $@: non-POSIX variable name
gnome-doc-utils.make:288: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:318: dir $@: non-POSIX variable name
gnome-doc-utils.make:318: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:319: notdir $@: non-POSIX variable name
gnome-doc-utils.make:319: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:328: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:328: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:340: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:340: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:343: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:343: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:346: patsubst %.xhtml,%.xml,$@: non-POSIX variable name
gnome-doc-utils.make:346: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:385: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:385: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:386: if $(_DOC_DSK_IN: non-POSIX variable name
gnome-doc-utils.make:386: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:387: if $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:387: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:388: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:388: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:505: patsubst C/%,%,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:505: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
cd . && /bin/bash /home/marc/fwbackups-1.43.3rc2/missing --run autoconf
configure.ac:18: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make: *** [configure] Error 1
marc@marc-laptop:~/fwbackups-1.43.3rc2$ 
[/HTML]


I remember at first I was missing a dependency but got it installed.

---

### Post by BDNiner on 2009-11-23
The first command you ran needs to run as root.

Sudo apt-get install..

---

### Post by alexeix on 2010-03-16
I'm seeing a similar problem to Morty007, despite following the instructions from post #14 and using sudo with the first command.

Any suggestions, as this seems like the perfect backup utility?
If it can backup my Windows and Linux machines, life will be much easier!

Here's the output from the final command:

[HTML]make && sudo make install
cd . && /bin/bash /home/alex/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/missing --run aclocal-1.10 
/home/alex/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/missing: line 54: aclocal-1.10: command not found
WARNING: `aclocal-1.10' is missing on your system.  You should only need it if
         you modified `acinclude.m4' or `configure.ac'.  You might want
         to install the `Automake' and `Perl' packages.  Grab them from
         any GNU archive site.
 cd . && /bin/bash /home/alex/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
/home/alex/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/missing: line 54: automake-1.10: command not found
WARNING: `automake-1.10' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.ac'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
cd . && /bin/bash /home/alex/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/missing --run autoconf
configure.ac:3: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:8: error: possibly undefined macro: AM_PATH_PYTHON
configure.ac:18: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.ac:19: error: possibly undefined macro: AC_PROG_INTLTOOL
make: *** [configure] Error 1
[/HTML]

---

### Post by BDNiner on 2010-03-17
You are missing the 'Perl' and 'Automake' packages. You should install these packages first and then try complie the software again.

---

### Post by alexeix on 2010-03-17
Both packages are already installed:

Automake 1:1.11-1
Perl 5.10.0-24ubuntu4

---

### Post by BDNiner on 2010-03-18
I will take a look at the code once I return home from work. I have been meaning to package this application into a deb file for a while. I was waiting on a final release. 

So if you haven't given up, i will follow up on this thread.

---

### Post by alexeix on 2010-03-18
Nope, I've not given up.

This sounds like the perfect backup solution, if I can get it running.
:)

---

### Post by BDNiner on 2010-03-18
Have you installed build-essentiail? I would make sure build-essential, checkinstall and automake (which you have) are installed. Instead of running *make && sudo make install*. I would run *make* and then report any errors here. After that run *sudo checkinstall* which will create a DEB file (makes things a little easier to uninstall).

---

### Post by alexeix on 2010-03-18
After running 'make install', I get the following results:

[HTML]/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --prefix=/usr --datadir=/usr/share --no-create --no-recursion
./configure: line 1637: syntax error near unexpected token `dist-bzip2'
./configure: line 1637: `AM_INIT_AUTOMAKE(dist-bzip2 no-dist-gzip)'
make: *** [config.status] Error 2[/HTML]

---

### Post by BDNiner on 2010-03-22
After looking over your case. I cannot determine what dependencies you are missing. You have installed everything that I have installed inorder to compile the software successfully. Did the ./configure command run successfully? if you could post the output of ./configure.

---

### Post by alexeix on 2010-03-22
Here's the output of ./configure:

[HTML]~/fwbackups-1.43.3rc2 $ ./configure --prefix=/usr --datadir=/usr/share
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/operations/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE[/HTML]

And then the next step again:

[HTML]~/fwbackups-1.43.3rc2 $ make && sudo make install
 cd . && /bin/bash /home/alex/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
/home/alex/fwbackups-1.43.3rc2/missing: line 54: automake-1.10: command not found
WARNING: `automake-1.10' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.ac'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
cd . && /bin/bash /home/alex/fwbackups-1.43.3rc2/missing --run autoconf
configure.ac:3: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:8: error: possibly undefined macro: AM_PATH_PYTHON
configure.ac:18: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.ac:19: error: possibly undefined macro: AC_PROG_INTLTOOL
make: *** [configure] Error 1[/HTML]

I then went back to Package Manager and installed Automake 1.10 (as my version was a later one).
After repeating the steps, this is what happens at "make && sudo make install":

[HTML]~/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2 $ make && sudo make install
 cd . && /bin/bash /home/alex/fwbackups-1.43.3rc2/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
configure.ac: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.ac: You should verify that configure.ac invokes AM_INIT_AUTOMAKE,
configure.ac: that aclocal.m4 is present in the top-level directory,
configure.ac: and that aclocal.m4 was recently regenerated (using aclocal).
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
gnome-doc-utils.make:63: HAVE_GNOME_DOC_UTILS does not appear in AM_CONDITIONAL
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:133: ENABLE_SK does not appear in AM_CONDITIONAL
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:182: ENABLE_SK does not appear in AM_CONDITIONAL
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:74: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:74: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:77: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:77: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:110: if $(DOC_USER_FORMATS: non-POSIX variable name
gnome-doc-utils.make:110: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: if $(filter environment,$(origin LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: filter $(LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: shell xmllint --format $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: notdir $(patsubst %/$(notdir $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: if $(_ENABLE_SK: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: wildcard $(_DOC_ABS_SRCDIR: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:173: call db2omf_args,$@,$<,'docbook': non-POSIX variable name
gnome-doc-utils.make:173: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:188: call db2omf_args,$@,$<,'xhtml': non-POSIX variable name
gnome-doc-utils.make:188: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter docbook,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:206: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:206: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:210: foreach ent,$(DOC_ENTITIES: non-POSIX variable name
gnome-doc-utils.make:210: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:214: foreach inc,$(DOC_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:214: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: if $(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: foreach fig,$(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: patsubst $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:237: foreach f,						\
gnome-doc-utils.make:237: 	$(shell xsltproc --xinclude 					\
gnome-doc-utils.make:237: 	  --stringparam db.chunk.basename "$(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:237: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach inc,$(_DOC_C_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: notdir $(inc: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach doc,$(_DOC_C_HTML: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: notdir $(doc: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:274: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:274: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: patsubst C/%,$(lc: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach fig,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: patsubst C/%,%,$(fig: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:288: dir $@: non-POSIX variable name
gnome-doc-utils.make:288: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:318: dir $@: non-POSIX variable name
gnome-doc-utils.make:318: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:319: notdir $@: non-POSIX variable name
gnome-doc-utils.make:319: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:328: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:328: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:340: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:340: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:343: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:343: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:346: patsubst %.xhtml,%.xml,$@: non-POSIX variable name
gnome-doc-utils.make:346: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:385: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:385: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:386: if $(_DOC_DSK_IN: non-POSIX variable name
gnome-doc-utils.make:386: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:387: if $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:387: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:388: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:388: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:505: patsubst C/%,%,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:505: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
src/fwbackups/Makefile.am:1: Python sources seen but `PYTHON' is undefined
src/fwbackups/Makefile.am:1:   The usual way to define `PYTHON' is to add `AM_PATH_PYTHON'
src/fwbackups/Makefile.am:1:   to `configure.ac' and run `aclocal' and `autoconf' again.
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
src/fwbackups/operations/Makefile.am:1: Python sources seen but `PYTHON' is undefined
src/fwbackups/operations/Makefile.am:1:   The usual way to define `PYTHON' is to add `AM_PATH_PYTHON'
src/fwbackups/operations/Makefile.am:1:   to `configure.ac' and run `aclocal' and `autoconf' again.
Use of uninitialized value $line in pattern match (m//) at /usr/bin/automake-1.10 line 3788.
make: *** [Makefile.in] Error 1[/HTML]

Do I need to install exact versions of the pre-requisite applications?
I'm not really sure where to go from here.
:(

---

### Post by BDNiner on 2010-03-23
OK, can you post the versions on your machine of the following programs?
build-essential (11.4)
automake (1:1.11-1)
intltool (0.41.0-0ubuntu1)
gnome-doc-utils (0.18.0-0ubuntu1)
python-paramiko (1.7.4-0.1)
python-notify (0.1.1-2build2)
python-gtk2 (2.16.0-0ubuntu1)

I am working on packaging the software as a DEB but that make take some time. I have version listed my versions in ()s

---

### Post by alexeix on 2010-03-23
Hi,

I've listed the versions below (they're all as per your advice).

Are you in the U.S., Australia/NZ, or somewhere else?
Thanks very much for your assistance!

build-essential (11.4)
automake (1:1.11-1)
intltool (0.41.0-0ubuntu1)
gnome-doc-utils (0.18.0-0ubuntu1)
python-paramiko (1.7.4-0.1)
python-notify (0.1.1-2build2)
python-gtk2 (2.16.0-0ubuntu1)

Now, this could well be relevant and I thought I'd already mentioned it (but having checked, it seems not); I'm temporarily running Linux Mint, because Ubuntu was hanging regularly since I upgraded. 
I've now identified that the problem was actually caused by Firefox, so I will be swapping back to Ubuntu at the weekend.

I don't know if that will technically make a difference, but I suppose the only way to be certain, is to test.
Anyway, let me know what you think.
Thanks again and sorry for missing out this info.

---

### Post by BDNiner on 2010-03-23
I was wondering what kind of custom ubuntu distro you were running because I was comparing your outputs to mine and there are some differences. I even created a new VM and installed the software from scratch to see if I was missing something since I have made some modifications to my install over the years.

Linux Mint is based on Ubuntu. I don't know what the differences are between the two. I have never tried Mint. This should work, so long as /usr and /usr/share have the same use. There is one other package that I want to make sure you have "gettext". Install that and try and compile again.

I do live in the U.S.

---

### Post by alexeix on 2010-03-24
Hmmm...gettext is already installed.

Version 0.17-8ubuntu2

Looks like I'll have to try with Ubuntu or maybe Kubuntu.

---

### Post by BDNiner on 2010-03-25
That is everything that you should need to install the software in ubuntu correctly. Please do let us know when you switch to k/ubuntu if you are still having the same issues compiling the software.

---

### Post by alexeix on 2010-03-25
I've installed Kubuntu and followed all the instructions in this post, but fsbackups still doesn't work.

Has anyone got this working from a standard, default installation of Ubuntu 9.10?

I think I'll have to give up and use a different application.

---

### Post by nmyrick on 2010-08-31
firewing1 

By far, FWBackups is the best open source backup software that I have seen, however, I am having one issue with it.  I have Ubuntu 10.04, and I cannot get the 'incremental' option to save when I create a backup set.  It gives me the option to select it, then apply, but when I go back in to the options menu, it is no longer selected.  Any suggestions?

---

### Post by nmyrick on 2010-08-31
It is in the Synaptic Package Manager.  Go to System>Administration>Synaptic Package Manager, then type fwbackup in the search.  It should come up.  Then right click, and select install.

---

### Post by stormzen on 2010-10-12
I hit this problem today.  ( I wanted the version in git, as my ultimate goal is to get compressed files over a network drive, and replace them file-by-file, if they are updated.  I'm not sure how I'm going to end up doing this, and I saw that there was a directory issue with direct file copy in the packaged version... )

Anyway, this was the issue I ran into:

```

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:13: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:13: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

Googling for "configure.ac:13: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library" turned up the advice to install "libgtk2.0-dev" ( twice -- one page was in Japanese, so I couldn't really tell what was being said, just had the system output to go by ), which resulted in installing 51 new packages:

```

The following NEW packages will be installed:
  debhelper html2text intltool-debian libatk1.0-dev libcairo2-dev libdirectfb-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libice-dev libjpeg62-dev libmail-sendmail-perl libpango1.0-dev
  libpixman-1-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libsm-dev libsys-hostname-long-perl libsysfs-dev
  libx11-dev libxau-dev libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  po-debconf x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 51 newly installed, 0 to remove and 19 not upgraded.

```

I complied, just to see if it worked ( and probably because I'm tired of trying to get it to work ), and it did work.

I wonder if it is necessary to have this package installed, however, and I noted this package:

[B]
intltool-debian
[/B]

.. and wondered if that was all I had really needed to get it compiling, as it is suspiciously similar to this recommended package:

[B]
intltool (0.41.0-0ubuntu1)
[/B]

As I'm inherently lazy, I'm not going to do anything to test my curiosity, but I thought I'd post my observation in case it helped anyone...

---

### Post by stevedude on 2011-01-05
Just wanted to weigh in and say that I can confirm that disabling the "print to  text file" option is what worked for me. Once I upgraded to release 1.43.4 and disabled that option [I think it's enabled by default], I was able to perform my backup.

Thanks for the info.

---

