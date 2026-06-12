---
title: "upgrades to 9.1 -- almost"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by mathias j sagartz on 2010-04-22
Last weekend I decided to do an upgradeathon using the upgrade manager.  
8.04 to 8.1 OK
8.1 to 9.04 OK
9.04 to 9.1 almost

I started the last upgrade but had to leave for a couple of hours just before it finished.  When I came back I though everything had gone OK but when I tried to restart -- no go.  I get the first Ubuntu screen with the little rectangle going back and forth but then the screen blanks and the system hangs. If I hit return, I get dumped into a shell. lsb_release -a tells me I have 9.1 installed.

On reboot I can select a maintenance version which also puts me into a 
shell.  From there I can cd and ls my way around the file system and stuff
seems to be there although I can't look at many of my old text files because I don't have permission. With a maintenance reboot, the last several lines on the screen before I get put into the shell are as follows:

Begin: Running /scripts/init-bottom .....
Done.
init: unreadahead main process (2485) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2485) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@linuxmachine:~#

I have a 9.1 install CD that I can boot the system with. This works and 
I can see and move about in my file system and in the windows partition.  I'm afraid to go any further and select install for fear that I'll loose all the stuff in my home folder (which, of course, I do not have backed up) and my windows partition.  I just haven't done anything like this before.

From the shell started by the maintenance restart or when I boot with the 
install disc I can't -- or don't know how -- to save the stuff in my home directory to a thumb drive or even the windows partition. 

So where can I go from here?  I have no experience with reinstallations.
Can it be done from a 9.1 CD install disc?  Will I loose all of my old stuff in the process or can I save it?  How are reinstallations normally done anyway? Is there a way that I can backup my home folder at this late date before I do anything risky?

Thanks for the help.

(tech level -- fairly low)

---

### Post by cariboo on 2010-04-23
Boot from your Live CD, once at the desktop open a terminal and type:

```
sudo fsck -y /dev/sda1
```

Substitute the partition Ubuntu is installed on for the example above.

---

### Post by mathias j sagartz on 2010-04-24
Tried fsck but still no go.  However I was able to recover most of the important files by emailing them to myself while booted from the LiveCD.

If I now just do an install from a LiveCD will I be able to preserve my Windows partition?

---

