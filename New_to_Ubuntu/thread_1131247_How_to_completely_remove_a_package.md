---
title: "How to completely remove a package"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by gregorywwalter on 2009-04-20
I installed, and somehow screwed up, the program net responsibility.  I've tried uninstalling it get apt remove, but it gives me this error message:

greg@greg-laptop:~$ sudo apt-get autoremove accpal-0.1.1.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package netresponsibility needs to be reinstalled, but I can't find an archive for it.


Given this, is there a way I can remove all the files from this package, and get rid of them?  Ubuntu won't let me install any upgrades to the system while this is in the way.

By the way, I'm a complete linux noob, don't know anything about programming.

Thanks!

---

### Post by steve101101 on 2009-04-20
if you use synaptic you can mark it for complete removal then click apply.

---

### Post by unutbu on 2009-04-20
If you installed netresponsibility from a .deb, then try
```

sudo dpkg -r netresponsibility
```

---

### Post by steve101101 on 2009-04-20
> **unutbu said:**
> If you installed netresponsibility from a .deb, then try
```

sudo dpkg -r netresponsibility
```

yeah try this. i read your message wrong. i don't think synaptic will be helpful to you here.

---

### Post by juancarlospaco on 2009-04-20
**sudo apt-get purge *packagename***

---

### Post by gregorywwalter on 2009-04-20
thanks, everyone.  I tried this, but here's what happened:

greg@greg-laptop:~$ sudo dpkg -r netresponsibility
[sudo] password for greg: 
dpkg: error processing netresponsibility (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 netresponsibility



also tried this, with no results:

greg@greg-laptop:~$ sudo apt-get purge netresponsibility
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package netresponsibility needs to be reinstalled, but I can't find an archive for it.


any more advice?  I'm starting to wonder whether I just need to reformat my system.

---

### Post by ugm6hr on 2009-04-20
Tell us how you installed it, and we might be able to help uninstall.

Perhaps the best solution is to take apt's advice: reinstall, and then remove.

---

### Post by gregorywwalter on 2009-04-20
I installed it using a .deb file I downloaded from here [http://sourceforge.net/project/platformdownload.php?group_id=205710](http://sourceforge.net/project/platformdownload.php?group_id=205710)

I used the Package Installer to install it, just double clicked on the .deb file and followed the instructions.

The issue, I think, came up when I tried to uninstall it using these instrucitons

First, do this:

greg@greg-laptop:~$ sudo killall net-responsibility-daemon
net-responsibility-daemon: no process killed

No luck there, so I went on to try deleting the files:


greg@greg-laptop:~$ sudo rm -r /etc/init.d/net-responsibility-daemon /usr/share/net-responsibility
rm: cannot remove `/etc/init.d/net-responsibility-daemon': No such file or directory

But that didn't work either.  Somewhere, I managed to mangle it just enough to give me trouble, but not enough to get rid of it.

I also tried reinstalling with the same software I originally downloaded (and again after that with another copy I downloaded again) and got this error box in the Package Installer:

Could not open 'netresponsibility-0.5.0.deb
The package might be corrupted or you are not allowed to open the file.  Check the permissions of the file.

Thanks for your patience, I really appreciate everyone helping out.

---

### Post by unutbu on 2009-04-20
How about open a terminal and type
```

sudo dpkg -i netresponsibility-0.5.0.deb
```

If that works, then try
```

sudo dpkg -r netresponsibility
```

again.

If it doesn't work, please post the terminal output.

---

### Post by gregorywwalter on 2009-04-20
greg@greg-laptop:~$ sudo dpkg -i netresponsibility-0.5.0.deb
[sudo] password for greg: 
dpkg: error processing netresponsibility-0.5.0.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 netresponsibility-0.5.0.deb


greg@greg-laptop:~$ sudo dpkg -r netresponsibility
dpkg: error processing netresponsibility (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 netresponsibility

---

### Post by steve101101 on 2009-04-20
did you try to reinstall it like it said?

---

### Post by unutbu on 2009-04-20
> "cannot access archive: No such file or directory"

This error message means dpkg could not find netresponsibility-0.5.0.deb. It apparently is not in the top-level directory of your home account. Perhaps you downloaded it to you Desktop? In that case you would type 
```

sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
```

But that's just a guess. If you don't know the directory where netresponsibility-0.5.0.deb is located, try typing
```

locate netresponsibility-0.5.0.deb
```

and if that does not work, try
```

find . -name "netresponsibility-0.5.0.deb" -print
```

and if that does not work, try
```

sudo find / -name "netresponsibility-0.5.0.deb" -print
```

One of these commands will show you the full path to the .deb.
Then run
```

sudo dpkg -i /path/to/netresponsibility-0.5.0.deb
```

(changing /path/to/netresponsibility-0.5.0.deb to the correct path.)

---

### Post by gregorywwalter on 2009-04-21
Tried all of the above, with no luck:

greg@greg-laptop:~$ locate netresponsibility-0.5.0.deb
greg@greg-laptop:~$ find . -name "netresponsibility-0.5.0.deb" -print
greg@greg-laptop:~$ sudo find / -name "netresponsibility-0.5.0.deb" -print
[sudo] password for greg: 
greg@greg-laptop:~$ 

I also tried reinstalling the software, but got an error message that I quoted earlier in this thread.

---

### Post by unutbu on 2009-04-21
Okay, it appears you do not have a file called netresponsibility-0.5.0.deb on your system.
So let's try this:
```

wget http://voxel.dl.sourceforge.net/sourceforge/responsibility/netresponsibility-0.5.0.deb -O ~/Desktop/netresponsibility-0.5.0.deb 

sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
```

Please post the entire output. The command is quite long, so cutting and pasting the command into the terminal might help.
Tip: If you select the text in the web page, and middle-click in the terminal, the text will be pasted. If you have a 2-button mouse, you can middle click by clicking both the left and right buttons simultaneously. If you have a wheel-mouse, click the wheel to middle-click. Apologies if you already knew all this.

---

### Post by gregorywwalter on 2009-04-21
Here's what I got:

```
greg@greg-laptop:~$ wget http://voxel.dl.sourceforge.net/sourceforge/responsibility/netresponsibility-0.5.0.deb -O ~/Desktop/netresponsibility-0.5.0.deb 
--2009-04-21 23:14:07--  http://voxel.dl.sourceforge.net/sourceforge/responsibility/netresponsibility-0.5.0.deb
Resolving voxel.dl.sourceforge.net... 72.26.194.82
Connecting to voxel.dl.sourceforge.net|72.26.194.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 212936 (208K) [application/octet-stream]
Saving to: `/home/greg/Desktop/netresponsibility-0.5.0.deb'

100%[======================================>] 212,936      332K/s   in 0.6s    

2009-04-21 23:14:12 (332 KB/s) - `/home/greg/Desktop/netresponsibility-0.5.0.deb' saved [212936/212936]

greg@greg-laptop:~$ 
greg@greg-laptop:~$ sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
[sudo] password for greg: 
Selecting previously deselected package netresponsibility.
(Reading database ... 126538 files and directories currently installed.)
Preparing to replace netresponsibility 0.5.0 (using .../netresponsibility-0.5.0.deb) ...
/var/lib/dpkg/info/netresponsibility.prerm: 3: /etc/init.d/net-responsibility-daemon: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /etc/init.d/net-responsibility-daemon: not found
dpkg: error processing /home/greg/Desktop/netresponsibility-0.5.0.deb (--install):
 subprocess new pre-removal script returned error exit status 127
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
update-rc.d: /etc/init.d/net-responsibility-daemon: file does not exist
/var/lib/dpkg/info/netresponsibility.postinst: 6: /etc/init.d/net-responsibility-daemon: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /home/greg/Desktop/netresponsibility-0.5.0.deb

```

In case you're wondering why I care so much about this little program, it's because the Update Manager won't let me install any updates since I messed up netresponsibility, so it sort of has my computer hijacked for the time being.

And no, I didn't know that about middle clicking, so thanks for the tip!

---

### Post by unutbu on 2009-04-22
Your system believes netresponsibility is installed.
So when we run "sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb" it apparently tries to remove /etc/init.d/net-responsibility-daemon before reinstalling itself. Note this error:
```

/etc/init.d/net-responsibility-daemon: not found
```

So let's try to force dpkg to install netresponsibility despite the error:
```

sudo dpkg -i --force-all ~/Desktop/netresponsibility-0.5.0.deb

```
Please post the output.

---

### Post by gregorywwalter on 2009-04-22
```
greg@greg-laptop:~$ sudo dpkg -i --force-all ~/Desktop/netresponsibility-0.5.0.deb
[sudo] password for greg: 
(Reading database ... 126538 files and directories currently installed.)
Preparing to replace netresponsibility 0.5.0 (using .../netresponsibility-0.5.0.deb) ...
/var/lib/dpkg/info/netresponsibility.prerm: 3: /etc/init.d/net-responsibility-daemon: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /etc/init.d/net-responsibility-daemon: not found
dpkg: error processing /home/greg/Desktop/netresponsibility-0.5.0.deb (--install):
 subprocess new pre-removal script returned error exit status 127
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
update-rc.d: /etc/init.d/net-responsibility-daemon: file does not exist
/var/lib/dpkg/info/netresponsibility.postinst: 6: /etc/init.d/net-responsibility-daemon: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /home/greg/Desktop/netresponsibility-0.5.0.deb
greg@greg-laptop:~$ 

```

---

### Post by unutbu on 2009-04-22
Well, that didn't work. Sorry, my mistake. Let's try this:
```
sudo touch /etc/init.d/net-responsibility-daemon
sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb

```
Please post the output.

---

### Post by gregorywwalter on 2009-04-22
Here's what I got:
```
greg@greg-laptop:~$ sudo touch /etc/init.d/net-responsibility-daemon
greg@greg-laptop:~$ sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
(Reading database ... 126538 files and directories currently installed.)
Preparing to replace netresponsibility 0.5.0 (using .../netresponsibility-0.5.0.deb) ...
/var/lib/dpkg/info/netresponsibility.prerm: 3: /etc/init.d/net-responsibility-daemon: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /etc/init.d/net-responsibility-daemon: Permission denied
dpkg: error processing /home/greg/Desktop/netresponsibility-0.5.0.deb (--install):
 subprocess new pre-removal script returned error exit status 126
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
/var/lib/dpkg/info/netresponsibility.postinst: 6: /etc/init.d/net-responsibility-daemon: Permission denied
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 126
Errors were encountered while processing:
 /home/greg/Desktop/netresponsibility-0.5.0.deb

```

---

### Post by unutbu on 2009-04-22
I've extracted the control files from this deb and looked at the postinst, postrm and prerm scripts which are throwing errors. I think I understand what's wrong: these scripts call /etc/init.d/net-responsibility-daemon. 

So we need the actual file to install and/or uninstall.

The following installs net-responsibility-daemon, and then once again attempts to install then purge netresponsibility:


```
sudo dpkg --extract ~/Desktop/netresponsibility-0.5.0.deb  ~/Desktop/tmp
sudo cp ~/Desktop/tmp/etc/init.d/net-responsibility-daemon /etc/init.d/net-responsibility-daemon
sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
sudo dpkg --purge netresponsibility

```

---

### Post by gregorywwalter on 2009-04-22
Wow, I don't know what to say, nothing seems to do it.  Thanks for sticking with me.

```
greg@greg-laptop:~$ sudo dpkg --extract ~/Desktop/netresponsibility-0.5.0.deb  ~/Desktop/tmp
[sudo] password for greg: 
greg@greg-laptop:~$ sudo dpkg --extract ~/Desktop/netresponsibility-0.5.0.deb  ~/Desktop/tmp
greg@greg-laptop:~$ sudo cp ~/Desktop/tmp/etc/init.d/net-responsibility-daemon /etc/init.d/net-responsibility-daemon
greg@greg-laptop:~$ sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
(Reading database ... 126538 files and directories currently installed.)
Preparing to replace netresponsibility 0.5.0 (using .../netresponsibility-0.5.0.deb) ...
/var/lib/dpkg/info/netresponsibility.prerm: 3: /etc/init.d/net-responsibility-daemon: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /etc/init.d/net-responsibility-daemon: Permission denied
dpkg: error processing /home/greg/Desktop/netresponsibility-0.5.0.deb (--install):
 subprocess new pre-removal script returned error exit status 126
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
/var/lib/dpkg/info/netresponsibility.postinst: 6: /etc/init.d/net-responsibility-daemon: Permission denied
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 126
Errors were encountered while processing:
 /home/greg/Desktop/netresponsibility-0.5.0.deb
greg@greg-laptop:~$ sudo dpkg --purge netresponsibility
dpkg: error processing netresponsibility (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 netresponsibility

```

---

### Post by unutbu on 2009-04-22
We are going to crack this.
Please post the output of
```

ls -l /etc/init.d/net-responsibility-daemon
```

---

### Post by gregorywwalter on 2009-04-22
Here it is:
```
greg@greg-laptop:~$ ls -l /etc/init.d/net-responsibility-daemon
-rw-r--r-- 1 root root 2503 2009-04-22 19:59 /etc/init.d/net-responsibility-daemon

```

---

### Post by unutbu on 2009-04-22
Ah. I had neglected to make net-responsibility-daemon executable.
```
sudo chmod 755 /etc/init.d/net-responsibility-daemon
sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
sudo dpkg --purge netresponsibility

```

---

### Post by gregorywwalter on 2009-04-23
```
greg@greg-laptop:~$ sudo chmod 755 /etc/init.d/net-responsibility-daemon
[sudo] password for greg: 
greg@greg-laptop:~$ sudo chmod 755 /etc/init.d/net-responsibility-daemon
greg@greg-laptop:~$ sudo dpkg -i ~/Desktop/netresponsibility-0.5.0.deb
Selecting previously deselected package netresponsibility.
(Reading database ... 126538 files and directories currently installed.)
Preparing to replace netresponsibility 0.5.0 (using .../netresponsibility-0.5.0.deb) ...
 * Stopping the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Stopping net-responsibility-daemon
                                                                         [ OK ]
Unpacking replacement netresponsibility ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
Setting up netresponsibility (0.5.0) ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
 * Starting the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
                                                                         [ OK ]

greg@greg-laptop:~$ sudo dpkg --purge netresponsibility
(Reading database ... 126537 files and directories currently installed.)
Removing netresponsibility ...
 * Stopping the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Stopping net-responsibility-daemon
                                                                         [ OK ]
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
Purging configuration files for netresponsibility ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
dpkg - warning: while removing netresponsibility, directory `/usr/local' not empty so not removed.

```

---

### Post by gregorywwalter on 2009-04-23
wow.  that's incredible!  you fixed it.  thank you so much, i can't tell you how much i appreciate this.  is there anything i can do to thank you?

---

### Post by unutbu on 2009-04-23
Your thanks is very gratifying. Glad I could help :)

---

