---
title: "Using Live Disk to copy files, Permission Issues"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by barabaskid on 2009-06-01
Hello all. Newbie here. I seem to have done something to my 8.10 install of ubuntu that prevents me from loading into the OS. As such, I intend to use the 9.04 Live Disk to simply wipe the hd and install 9.04. Before I do that, though, there are some files in my home folder on the existing installation that I would like to save. As I am unable to boot into the install, I am trying to use the live disk to navigate to the folder on my HD and copy them on to an external hd. When I do so, though, I am unable to copy the files as I do not have the permissions to do so.

When I log in to the live disk, I do so as "ubuntu" in the default manner. I have tried copying the files with "sudo nautilus", but am still unable to do so. I of course know my user name and psw for the corrupted install, but cannot figure out how to use it.

Any help in getting these files copied would be much appreciated. Thanks all!

---

### Post by t0p on 2009-06-01
First of all, it's recommend that you use **gksudo nautilus** to get a file manager with admin privileges rather than "sudo nautilus".  That aside, if you still can't copy files from your hard drive then I would suspect the file system has become corrupted and mounted itself read-only (which is a dumb thing corrupted file systems do sometimes to "protect" themselves).  You can check if it's become read-only by looking under the "Permissions" tab.

As for a fix: I did a little googling for you and found a couple of possible solutions.  [This guy]("http://www.cyberciti.biz/tips/linux-filesytem-goes-read-only.html") suggests using the command

```
mount -o remount /
```

while [this other person]("http://www.linuxforums.org/forum/debian-linux-help/15124-read-only-file-system.html") says to use the command **fsck**.  The command "fsck" is "to check and repair a Linux file system" - I'm not very familiar with it I'm afraid, so you'll have to check the man page or hope someone else will come along to your rescue.  But I *can* tell you that you should only use the command *on an unmounted file system*.

Other than that, all I can suggest is you do a little googling for yourself.  Using any error message you get as a search term can be most helpful.

---

### Post by antmenj on 2009-06-02
I find puppy linux very good for that type of job.

---

### Post by nothingspecial on 2009-06-02
Never mind not read your initial post properly

sorry

---

