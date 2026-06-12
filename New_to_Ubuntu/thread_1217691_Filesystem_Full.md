---
title: "Filesystem Full"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by naturenut on 2009-07-19
I'm very new to linux and am still on the steep part of the learning curve as far as how things are stored on partitions. I'm having problems with the filesystem filling up. I can't install/uninstall software any longer - get the following error:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '88080387' '--set-selections-file' '/tmp/tmpB0HUS2' as user root.

Unable to copy the user's Xauthorization file.

Disk Usage Analyzer shows:

/  at 100%
home at 86.7%

Tried to set it up so that the filesystem is on one partition (30GB) and home is on another (380GB), with a separate vfat partition (50GB) for windows, but apparently that didn't happen - /home and windows partitions both appear under filesystem.

Would like to know if this situation can be fixed without losing data and settings. I have a new HD on the way that I can copy data and settings onto.  Can I copy /etc and /usr to that drive before I work on the current drive so that settings and installed software won't be lost?

If further info is needed, will be glad to provide it.

---

### Post by drs305 on 2009-07-19
Please provide us with the results of:
```

df -Th 

```
This will give us the partition sizes and usage.

There is a link in my signature line for finding and recovering "lost" Disk Space, but we really aren't to that point yet unless you are looking for something to read while you wait for responses.

---

### Post by naturenut on 2009-07-19
> **drs305 said:**
> Please provide us with the results of:
```

df -Th 

```This will give us the partition sizes and usage.

There is a link in my signature line for finding and recovering "lost" Disk Space, but we really aren't to that point yet unless you are looking for something to read while you wait for responses.

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     29G   27G     0 100% /
tmpfs        tmpfs    1.7G     0  1.7G   0% /lib/init/rw
varrun       tmpfs    1.7G  348K  1.6G   1% /var/run
varlock      tmpfs    1.7G     0  1.7G   0% /var/lock
udev         tmpfs    1.7G  152K  1.6G   1% /dev
tmpfs        tmpfs    1.7G  5.3M  1.6G   1% /dev/shm
lrm          tmpfs    1.7G  2.2M  1.6G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda7     ext3    380G  145G  216G  41% /home
/dev/sda6     vfat     48G   20G   29G  41% /windows
overflow     tmpfs    1.0M 1020K  4.0K 100% /tmp

---

### Post by earthpigg on 2009-07-19
yup, your root partition (/) is full.

system -> administration -> computer janitor -> make sure you look before you remove... if you installed something not in the repos, it will show up there. 

these two commands also free up space:

> sudo apt-get autoclean
sudo apt-get clean

then do df -Th again to see where you are sitting.

if you still need to free up some space:

unplug any external hard drives -> go to applications -> accessories -> disk usage analyser -> scan filesystem -> click around a bit, see if anything seems odd to you.

dont worry about what is in /home or /windows, since those are their own partition.... 

usually a 30 gig / partition is plenty, we gotta figure out what you have going on in yours.

---

### Post by naturenut on 2009-07-20
> **earthpigg said:**
> yup, your root partition (/) is full.

system -> administration -> computer janitor -> make sure you look before you remove... if you installed something not in the repos, it will show up there. 

these two commands also free up space:

OK. My son, who built the computer (novice linux user too) and installed the OS, posted the earlier messages. I'm gonna add some details before I get to the cleanup stuff you posted.

I'm on the latest Ubuntu release (don't know how to find out the actual version/update numbers) and up-to-date on updates unless some have come out since mid-week last week.

UPDATE: Figured out how to find release info. Here it is: Release 9.04, Kernel Linux 2.6.28-13 generic, GNOME 2.26.1. The icon indicating needed updates is in the panel, but have not clicked it - want to wait til I fix the problems first...

I had been getting errors about being unable to mount (couldn't lock) my Kodak camera correctly ever since a recent update, figured that the update broke something, but I could still get pix off using F-spot, so I wasn't too concerned and figured it'd be fixed in a future update. F-spot quit working (found out shortly before the CD business below) - appears to try to load, item appears on panel, but it disappears without the app opening - generates 2 of the unable to mount errors. Not sure if that precipitated the problem or not, but figured you should know.

I found out that I had a serious problem when I attempted to find out what was on an unlabeled CD (is't one that I burned with data, probably pix). I got a message that the CD couldn't be mounted, and I couldn't get the drive to open using the eject button, so I clicked restart under the user menu. Reboot resulted in message that graphic interface couldn't be started and, after some doing, I managed to get to the prompt, but didn't know what to do.

I hunted up the install CD that my son had left with me and managed to get online. I found and followed the following, which resulted in being able to get back to the desktop.

The 2 sudo apt-get commands supplied in the posting I'm replying to
kill large files in /var/log - I killed  *.gz

That gets us to where we were when I got your posting. Here's what went down with the commands you sent.

Computer Janitor showed

libgmime2.2a-cil
libgnomepanel2.24-cil
libopal3.6.1
libpt2.6.1
libpt2.6.1-plugins-alsa
libpt2.6.1-plugins-v412
Package was installed because another package required it, but now nothing requires it anymore.


linux-image-2.6.27-11-generic
Package is no longer supported: it is no longer in the package archive. (It may also have been installed from an unofficial archive that is no longer available. In that case you may want to keep it.)

I kept the last one, because I dunno where it came from, but killed the rest.

sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

sudo apt-get clean 
No visual results, just new prompt.

I won't lie to you, I really don't understand a lot of what I'm looking at with the analyzer, so I included the items that I figure are important. If I need to look at other things, just holler and let me know what to look at.

Disk Usage Analyzer results
/    100%    166.5GB
home    86.7%    144.4GB
    user    100%    144.4GB (actual user dir, not usr)
usr    1.4%    2.4GB
    lib    46%    1.1GB
    share    40.3%    973.9MB
lib/modules    87.9%    269.1MB
opt/kde3    75%    12KB
    share    66.7%    8KB

Result of df -Th 

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     29G   27G     0 100% /
tmpfs        tmpfs    1.7G     0  1.7G   0% /lib/init/rw
varrun       tmpfs    1.7G  344K  1.6G   1% /var/run
varlock      tmpfs    1.7G     0  1.7G   0% /var/lock
udev         tmpfs    1.7G  152K  1.6G   1% /dev
tmpfs        tmpfs    1.7G  300K  1.6G   1% /dev/shm
lrm          tmpfs    1.7G  2.2M  1.6G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda7     ext3    380G  145G  216G  41% /home
/dev/sda6     vfat     48G   20G   29G  41% /windows
overflow     tmpfs    1.0M 1020K  4.0K 100% /tmp

FYI, I'm a long time DOS and OS/2 user (since the mid-80s) - finally got convinced to drop OS/2 for linux because of a lack of hardware support in OS/2 and my refusal to support MS. I like linux a lot, but much is foreign to me. I'm self-taught, and learning linux on my own as well, so any explanation of procedures done would be appreciated.

---

### Post by naturenut on 2009-07-20
> **drs305 said:**
> 
There is a link in my signature line for finding and recovering "lost" Disk Space, but we really aren't to that point yet unless you are looking for something to read while you wait for responses.

Just for jollies, I decided to look at the link. It has helped me a bit in understanding the output of Disk Usage Analyzer. Still got more to read, but...

I *think* I may have found a problem. I went to terminal and looked at the /var directory - in that directory is a backup directory with a bunch of backups in it. I can ls with sudo, but can't cd into the directory. Backups appear to be desktop (filenames are 2009-07-20_07.35.15.821086.XXX-desktop.ful, where XXX is username) and appear to be added daily with 9 iterations (23.7GB). Dunno why so many iterations, I've never kept over 5, usually 3 on backups - mebbe a setting somewhere?

Can I kill these files without problems? If so, any special info on permissions?

Maybe can move the backup directory to the /home partition (at least until my new HD arrives and is installed)? No worry there about 9 iterations...

---

### Post by philinux on 2009-07-20
Yes use 

```
gksu nautilus 
```

to explore var and move/delete file.

Sounds like backups gone haywire.

Be careful with the above command as its the file browser with full admin, or root, privileges.

---

### Post by naturenut on 2009-07-20
> **philinux said:**
> Yes use 

```
gksu nautilus 
```to explore var and move/delete file.

Sounds like backups gone haywire.

Be careful with the above command as its the file browser with full admin, or root, privileges.

Thanks for the warning. I understand the implications of working as admin. Never had to worry about permissions til now (other than write-protect - all actions were as admin), but understand the concept. Am also comfortable with the command line - wasn't any desktop when I got started <G>.

Before I do anything, I'd like to ask a question or two.

Since the latest backup appears to have been done today, the problem will just recur if I don't fix the cause. Can you tell me where to find the offending app?

Is it possible to have the backups saved to another partition - like /home. I realize that /home isn't a good location, but it'll do until I can get my new drive and get it set up - should be this coming weekend. A new system *should* last that long without problems ;->

---

### Post by philinux on 2009-07-20
It could be rsync thats been set. Use system>admin>system monitor. See drs305's link it mentions this specifically.

The processes tab, should look slightly familiar. Has you son set something up?

---

### Post by naturenut on 2009-07-20
> **philinux said:**
> It could be rsync thats been set. Use system>admin>system monitor. See drs305's link it mentions this specifically.

The processes tab, should look slightly familiar. Has you son set something up?

Don't see rsync in system monitor. Will read more of the link shortly - it's been an interesting read so far.

I dunno what all he set up - I was working outdoors and when I came in, he had it all done. All he asked me for was a username, password and keyring password. I wanted to be around and study up on installation and setup, but other things had to be done - such is life...

I've added a bunch of apps for my personal use (it's my home box), but I don't recall seeing anything about backups.

Mebbe I should look at cron?

Will also look through the list of apps under system to see if I find anything about backups.

UPDATE: I moved the backups to /home and now I have 20+GB free on /, so that seems to be the problem. Went into System>Administration>Simple Backup Config and found that it had been set up to backup the desktop. It appears that the default and recommended settings were used - which put backups in /var and also uses a logarithmic method backing up, which explains the number of iterations. I changed the settings to use a directory in /home, temporarily.

I'd like to thank everyone for their help. And a special thanks to drs305 for posting the webpage about freeing up space - that's what pointed me to the /var directory, dunno how long it would have taken to figure it out otherwise...

Now, where should I post a question about recursive scripting....

---

### Post by drs305 on 2009-07-20
> **naturenut said:**
> 
Now, where should I post a question about recursive scripting....

Glad you found the guide helpful. 

I'd post the the question in the General section - it's a bid beyond Absolute Beginners. You can take a look at the available forums by clicking on "Ubuntu Forums" at the very top left of this page, but unless it deals with a very specific aspect of Ubuntu the General section will probably do very well.

---

