---
title: "Help reinstalling mpd, and possibly on getting it to work"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by misternu on 2011-01-28
I am pretty dumb. I've installed and configured a lot of stuff before, and I have gotten in the habit of just saying "piff" when I am told to backup a .conf file. This happened today while I was installing mpd and I went to change the conf. I decided that I wanted to start over, so I reinstalled the program. For some reason, the changes to the conf file did not go away. So I deleted it. I tried to reinstall and now I get errors even trying to do that.

I have learned the first part of the lesson, I will now back up conf files from now on.

The second part of the lesson is, how does one get the conf back? Not just the one I deleted, I know how to do that. The default one.

Once again, I realize that I'm really really really dumb. Please help, thank you!

~misternu

---

### Post by tgalati4 on 2011-01-28
Open a terminal:

sudo apt-get clean
sudo apt-get purge mpd
sudo apt-get install mpd

---

### Post by misternu on 2011-01-28
So far my attempts have been similar to your suggestion. Some information: I originally installed it with ubuntu software center, here is the output from the first two commands.

book@book:~$ sudo apt-get clean
[sudo] password for book: 
book@book:~$ sudo apt-get purge mpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mpd*
0 upgraded, 0 newly installed, 1 to remove and 42 not upgraded.
1 not fully installed or removed.
After this operation, 520kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 254963 files and directories currently installed.)
Removing mpd ...
 * /etc/mpd.conf must have pid_file set; cannot stop daemon.
invoke-rc.d: initscript mpd, action "stop" failed.
dpkg: error processing mpd (--purge):
 subprocess installed pre-removal script returned error exit status 1
action: abort-remove not supported
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by misternu on 2011-02-03
Um, I still don't understand how to repair my package system. The errors above happen each time, and I really don't know how to fix this. So this post is like a "bump" or something.

---

### Post by misternu on 2011-02-04
This is what I ended up doing to fix the error. I found it in a variety of forum posts. I don't understand why it worked, but at least my package system is fixed and I can try to configure mpd again.

sudo rm /var/lib/dpkg/info/mpd.*

---

