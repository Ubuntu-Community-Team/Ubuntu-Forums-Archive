---
title: "could not launch application"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by aam-aadmi on 2009-08-07
Hi All,

Recently I upgraded from Ubuntu 8.04 to 8.10 and then to 9.04. Now, with the new version of Ubuntu I am having occasional problems launching applications. Here is a typical problem I faced: I tried to open the terminal and got the following error message

[HTML]Could not launch application
Falied to execute child process "gnome-terminal" (input output error)
[/HTML]
Then I tried to restart the machine but was unsuccessful. It showed several messages, most notable being:

I/O error, dev sda, sector ...

After repeating the above message several times, the message on the screen was: 

[HTML]Stopping anac(h)ronistic cron anacron.
[/HTML]
At this point the machine froze (I gave it couple of minutes but nothing happened). I had to force a shutdown by pressing down the power button.

Any suggestions about how to fix this problem? 

Aam-aadmi

---

### Post by Jazzy_Jeff on 2009-08-07
My suggestion to you is to back up all your important information and do a clean install. You can boot into a live cd to back up your things if needed.

---

### Post by Rocket2DMn on 2009-08-07
This could be a sign that your hard drive is acting up, and possibly dying.  To be safe, I would make sure you have all of your data backed up in case your hard drive gives out.  You can check in /var/log/messages for other errors that might be related.  I would also recommend running fsck on your root partition.  You can do this by running
```
touch /forcefsck
```
then rebooting.  During the boot sequence, fsck will run.

---

### Post by aam-aadmi on 2009-08-08
Thanks for the suggestion to backup all the data and go in for a fresh install. I will do that but I need one suggestion: I use Thunderbird as my e-mail client and I want to back up all the information in Thunderbird (mails, address book, etc.). How do I do that so that I can then access all this information (mails, address book, etc.) in the new installation? 

Aam-aadmi

---

### Post by Rocket2DMn on 2009-08-08
All your thunderbird settings are in the .mozilla-thunderbird folder in your home directory.  Because the folder name begins with a ., it is hidden, so hit CTRL+H in nautilus to view hidden files.

However, I don't think a clean install is the way to go right now.  If this is a hardware problem, then it needs to be diagnosed, and a fresh install won't fix it.  Have you tried running fsck like I suggested?  It can also be done from a LiveCD rather than during bootup if you want.

---

### Post by aam-aadmi on 2009-08-09
I ran fsck exactly like you suggested: 

[HTML]sudo touch /forcefsck[/HTML]

and then I rebooted.

I could see that the booting process was interrupted in the middel and fsck was run, but there were no error messages or messages showing that errors had been fixed. Does this mean that the hard drive is OK? Do I need to take any subsequent steps?

Aam-aadmi

---

### Post by Rocket2DMn on 2009-08-09
Are you still getting the errors?  If so, please post the output of
```
dmesg
```


Also, we should probably run fsck from the LiveCD to see in more detail what is happening.  From a live cd, run
```
sudo fsck /dev/sda1
```
where /dev/sda1 is your root partition.  You can check what your partitions are by running
```
sudo fdisk -l
```

---

### Post by aam-aadmi on 2009-08-09
I have not got the errors again. I will run fsck from the liveCD and also post the output of "dmesg" if I encounter the error again.

---

