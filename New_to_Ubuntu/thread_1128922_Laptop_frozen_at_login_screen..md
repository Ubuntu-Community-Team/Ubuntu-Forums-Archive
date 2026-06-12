---
title: "Laptop frozen at login screen."
date: 2009-04-18
forum: New to Ubuntu
---

### Post by satipera on 2009-04-18
Online with live cd :-(  I was using a programme called powertop which suggests changing ubuntu settings to reduce laptop power consumption. It suggested that I change the disc timing for a procedure to 1500 (centiseconds) in a particular file. It was a root file in a sub directory of proc (can't remember name of sub directory) called something like dirty write and normally has a value of 500. As it was a root file I used gksudo nautilus but was was not even able to get to the file let alone open it. After searching on the net I came across a rejected bug report filed by someone who was having the same problem with another file, it was rejected as sudo does not accept redirection in certain circumstances and suggested another approach. 
       At this point I could not start a programme I wished to use so I re-logged. I was met with a message something along the lines of "the user must be the owner of their own home directory" At this point I rebooted. I get as far as the login screen but the comp is frozen. I am in way way over my head can I recover my system?
       P.S. I attempted to temporarily change the permissions to proc but not the ownership.

---

### Post by satipera on 2009-04-18
Additional info, when I look at the ownership of the home folder (using live cd) it is root. However the ownership of my home folder (previously named ian) is now owned by  "1000". I have no idea how this has happened. Do I just need to change the ownership of the file back to "ian"? if so how?

---

### Post by James_Lochhead on 2009-04-18
Hi,

To change the permissions back type the following in the terminal:

```

sudo chown -R ian:ian /path/to/home/directory

```

Path is probably /home/ian/ unless the directory name has changed. 

It is not clear whether your home directory is called 1000 or not from year post. If it is use the following command to change it back:

```

sudo mv -R /home/1000 /home/ian

```

Oh and all of this is in the terminal: Applications > Accessories > Terminal.

---

### Post by James_Lochhead on 2009-04-18
I am also assuming you have mounted your hard disk and moved into the Ubuntu root partition btw.

---

### Post by satipera on 2009-04-18
Hello james when I did as you suggested as root in the live cd I am getting ian invalid user

---

### Post by KIAaze on 2009-04-18
That's because when you boot into the Live-CD there is no user named "ian".
"1000" is almost certainly the UID (User ID) and GID (Group ID) of the user "ian".

You can check this by looking into /etc/passwd.
It should contain a line like this:
```
ian:x:1000:1000:ian:/home/ian:/bin/bash
```
cf: [http://www.itwire.com/content/view/14446/53/](http://www.itwire.com/content/view/14446/53/)

This means that you can run:
```
sudo chown -R 1000:1000 /path/to/home/directory
```
from the Live-CD instead of:
```
sudo chown -R ian:ian /path/to/home/directory
```

_The following should not be necessary, but just in case the problem is more complex:_
Another more advanced solution is to use "chroot" to change the root directory:
1)Boot into the Live-CD
2)Mount your partition
3)Run:
```
sudo chroot /mnt/yourpartition
```

Now it will be as if you had booted from your hard disk and logged in as root. So be careful. ;)
cf [http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd](http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd) for more info.

_Note:_
> I was using a programme called powertop which suggests changing ubuntu settings to reduce laptop power consumption. It suggested that I change the disc timing for a procedure to 1500 (centiseconds) in a particular file. It was a root file in a sub directory of proc (can't remember name of sub directory) called something like dirty write and normally has a value of 500. As it was a root file I used gksudo nautilus but was was not even able to get to the file let alone open it. After searching on the net I came across a rejected bug report filed by someone who was having the same problem with another file, it was rejected as sudo does not accept redirection in certain circumstances and suggested another approach.
It might help if you posted a link to the instructions you followed as well as to the bug report you found. ;)
Because right now, I have no exact idea what exactly you did to your system.

Also, it seems that "files" in /proc are not really files, but some kind of virtual files related to the hardware/kernel: [http://www.ibm.com/developerworks/linux/library/l-adfly.html](http://www.ibm.com/developerworks/linux/library/l-adfly.html)
Apparently, you should never edit them with a text editor, but use "echo" to make changes to them.
> How to make changes

First, think about how not to make changes to the kernel. There are two good reasons why you should not just jump into the /proc filesystem, open a file in your text editor, make a bunch of changes, and save the file back out again. These are:

    * Data integrity: All of these files represent the running system, and since the kernel may change any of these files at any time, if you open an editor and change some data while the system is changing it underneath you, whatever you save back is unlikely to be what the kernel is expecting.
    * Virtual files: All of these files do not actually exist. How would the saved data be synchronized, etc.?

The answer to making changes to any of these files, therefore, is not to use an editor. When making changes to anything at all in the /proc filesystem, you should use the echo command and redirect the output from the command line into your chosen files under /proc. For example:

echo "Your-New-Kernel-Value" > /proc/your/file

Similarly, if you wish to view information from /proc, you should either use a command that is designed for the purpose or use the command line cat command.


---

### Post by satipera on 2009-04-18
Hello kiazee yes in the passwd file it is as you said. The problems did start when I tried to access the proc directory but could not do so. I am still frozen at the login screen now though and unable to input any user name to log in with. Will following your chroot method enable me to log on? The bug report was rejected as it was found to be normal behaviour I do remember it saying to use another method and echo rings a bell :-) I do not think it is the powertop programme causing the trouble but the proc access.

---

### Post by satipera on 2009-04-18
I just wanted to simply restate the position after the help I have been given so far.

By ignorantly trying to access the proc files I seem to have done some damage. This damage is apparent when I reach the login screen and am unable to type anything in the username box. The mouse does not work either.The keyboard is not completely dead as some ctrl key combinations appear to be doing something but I do not know what.
     Is the system recoverable from this point?

---

### Post by satipera on 2009-04-18
I just wanted to simply restate the position after the help I have been given so far.

By ignorantly trying to access the proc files I seem to have done some damage. This damage is apparent when I reach the login screen and am unable to type anything in the username box. The mouse does not work either.The keyboard is not completely dead as some ctrl key combinations appear to be doing something but I do not know what.
Is the system recoverable from this point?

**  New info.  I changed a config file to auto log me in. After rebooting I received a message in a box in the gui that said  "your session lasted for less than 10 seconds if you did not log out yourself then there may be a system problem"**

---

### Post by KIAaze on 2009-04-18
Can you switch to a virtual terminal from the login screen? Use ctrl+alt+F1 to try it.

Otherwise, try to boot into recovery mode by selecting the recovery entry in grub.

Once you have access to a terminal, try to log in as root if you have set a root password, otherwise, try to log in with you normal account.

As for chroot: it's only a method to get root access as if you were on the real machine, not the live CD.
From there you should be able to fix almost any problem, provided you know what the problem is and how to fix it. Something which isn't clear to me right now...

Also, please check that you enough disk space left on the root partition. This can prevent logging in too (altough it usually gives you a clear message then).

edit: After some research, this is what you seem to have done:
```
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
```
[http://www.brighthub.com/environment/green-computing/articles/12468.aspx](http://www.brighthub.com/environment/green-computing/articles/12468.aspx)

On my PC, the value is set to 500.
So maybe you could try:
```
echo 500 > /proc/sys/vm/dirty_writeback_centisecs
```
once you have access to a root terminal.

But I have no idea how this could lead to a frozen login screen.

---

### Post by satipera on 2009-04-20
Thanks to all the people who offered help, I could not get past the no login problem though. My data was backed up so I reinstalled, this does mean getting it all set up again to how I want it :-(. This problem led me to investigate clonezilla live. I now have a cloned image of the latop hard drive in a safe place so hopefully I should be safe now. Btw marking threads as solved was suspended at one point can we do it again? If so please remind me how.

---

