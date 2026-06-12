---
title: "Updating problem!"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-08-17
Had no problems updating previously then this time I receive this message when attempting to update.

Failed to lock the package manager

Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.

Detail:  The package indexes are currently changed by apt-get.

Anyone know how to correct this problem.

---

### Post by Rex Bouwense on 2011-08-17
There is more than one way to update or install software.  You had something running that was updating or attempting to update.  Just go to terminal and run 
sudo apt-get update
sudo apt-get upgrade
It will ask you for your password so enter it and hit enter.  You will not see any response as you enter the password..  This will get updates for you.  Make sure that you are not running Synaptic Package Manager or Ubuntu Software Center at the same time.

---

### Post by Mccfuzz on 2011-08-17
Thanks I'll give that a go.

Re: Synaptic Package Manager or Ubuntu Software Center at the same time.

How do I check if these are running?  What is the equivalent of Windows 'Task Manager' ?

---

### Post by Mccfuzz on 2011-08-17
Still  a problem somewhere.  The suggested option came up with:-

kevles@kevles-desktop:~$ sudo apt-get update
[sudo] password for kevles: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
kevles@kevles-desktop:~$

---

### Post by Rex Bouwense on 2011-08-17
They will not be open and running unless you start them.  What probably happened when you tried to update is the update manager was already checking for updates.  It is screwy I know, but if you try again it will more than likely be OK.

Make sure your caps lock is not on.  Linux is case sensitive.

---

### Post by seawolf167 on 2011-08-17
Do you have either open? If you look to where your windows minimize, is either the Synaptic package manager or the Ubuntu software center open and running?

You could always reboot and it would work, but an easier way (if they for sure are not running) is just to remove the lock holding it open

```
sudo rm /var/lib/apt/lists/lock
```

then do your updates

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by drs305 on 2011-08-17
There appear to be at least two APT-related programs running. You can check what 'root' owned apps are running with:
```
ps -u root
```
and if you find any you could force them to close with:
```
sudo killall <appname>
```
Perhaps a better solution would just be to reboot. During the shutdown process the system should safely terminate any running packages and hopefully remove the lock.

---

### Post by b0b138 on 2011-08-17
Goto system->administration->system monitor then the processes tab

And yes, synaptic and software center at the same time.

If you don't notice anything stuck open in system monitor, just reboot. It will probably be easier and quicker

---

### Post by Mccfuzz on 2011-08-20
You were quite right.  After a reboot Ubuntu updated correctly.  Thanks..........:popcorn:

---

