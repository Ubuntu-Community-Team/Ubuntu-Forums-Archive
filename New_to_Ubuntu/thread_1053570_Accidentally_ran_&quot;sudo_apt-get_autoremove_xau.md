---
title: "Accidentally ran &quot;sudo apt-get autoremove xauth&quot; on my server  -- HELP!"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by TMcKSmith on 2009-01-28
To make a long story short, I ran "sudo apt-get autoremove xauth" on my server.  Obviously this wasn't good, and it seemed to delete a ton of things.  When I reboot my server it just goes to a command-line rather than the Xubuntu login screen for my desktop. 

How can I get back to normal?

I tried "sudo apt-get install xauth" but it didn't work.  Any help would be appreciated.

---

### Post by TMcKSmith on 2009-01-28
In fact, I'm unable to "sudo apt-get" ANYTHING

it can't resolve any URLS

please help




thanks!

---

### Post by cardinals_fan on 2009-01-28
Why are you running X or a desktop on a server?

Anyway, can you post the most recent entries from /var/log/dpkg.log so we can see just what packages got removed?

---

### Post by TMcKSmith on 2009-01-28
well how would I be able to access such a file?

Why wouldn't it let me install any packages?

Says it can't resolve URL...

---

### Post by TMcKSmith on 2009-01-28
I didn't mean how would I access it...I mean how would I be able to access it and post it here?  

Even if I did get the info about the packages I uninstalled...I wouldnt be able to reinstall as far as I can tell

If anyone has any ideas I'd greatly appreciate this..this is such a disaster

---

### Post by TMcKSmith on 2009-01-28
when I type "ifconfig"
it only shows "lo"

no "eth0" or "eth1"...why would this have happened?  why is this no longer on the network?  this is why I can't download packages...please help

---

### Post by elvinatom on 2009-01-28
> **TMcKSmith said:**
> In fact, I'm unable to "sudo apt-get" ANYTHING

it can't resolve any URLS

please help




thanks!

Probably removed apt along with it.  Do you still have dpkg?

---

### Post by TMcKSmith on 2009-01-28
> **elvinatom said:**
> Probably removed apt along with it.  Do you still have dpkg?

I don't think that's the case...I can still execute the command, but it just can't download anything because I'm no longer on the network for some strange reason.  See my previous post for additional info.

---

### Post by ramsam on 2009-01-29
Did you happen to check
the interfaces file in the /etc/network dir 
and did you check the dmesg ? anything unusual?

---

### Post by TMcKSmith on 2009-01-29
I checked the interfaces file, everything is as normal.

What is dmseg?

---

### Post by elvinatom on 2009-01-29
> **TMcKSmith said:**
> I don't think that's the case...I can still execute the command, but it just can't download anything because I'm no longer on the network for some strange reason.  See my previous post for additional info.

Gotcha, in that case you can still get the packages from your cd by editing the /etc/apt/sources.list.  Add a # before every line and remove the # in the 2nd line (or whatever contains your installation media).  Might get some version issues though.

---

### Post by TMcKSmith on 2009-01-29
udevL  renamed network interface eth0 to eth1
tg3:  eth1:  Link is up at 100 Mbps, full duplex
tg3:  eth1:  Flow control is on for TX and on for RX
ADDRCONF (NETDEV_CHANGE):  eth1:  link becomes ready
eth1:  no IPv6 routers present

---

### Post by TMcKSmith on 2009-01-29
> **elvinatom said:**
> Gotcha, in that case you can still get the packages from your cd by editing the /etc/apt/sources.list.  Add a # before every line and remove the # in the 2nd line (or whatever contains your installation media).  Might get some version issues though.

nice suggestion...however I notice it's not even recognizing my cdrom  now...

when I enter the BIOS, it says none of my boot devices are present except for the hard drive

ahhhhhhhh

---

### Post by elvinatom on 2009-01-29
Are you sure you interpred that correctly?  This would mean that you accidentally removed half your os and by random chance your physical cd-drive died at the same time.
Just stick in a cd a do:
```
ls /media/cdrom0
```

or if it doesn't mount automatically:
```
sudo mount /media/cdrom0
ls /media/cdrom0
```

---

### Post by elvinatom on 2009-01-29
In any event - just to patch it up you can go into your interfaces and temporarly change all 'eth0' to 'eth1', just to get you machine online again.  I forgot where the file resides that declares the NICs.
```
sudo nano /etc/network/interfaces
```

---

### Post by TMcKSmith on 2009-01-29
> **elvinatom said:**
> Are you sure you interpred that correctly?  This would mean that you accidentally removed half your os and by random chance your physical cd-drive died at the same time.
Just stick in a cd a do:
```
ls /media/cdrom0
```

or if it doesn't mount automatically:
```
sudo mount /media/cdrom0
ls /media/cdrom0
```

I'll give this a shot when I get home tonight.  Thanks.

---

### Post by cardinals_fan on 2009-01-29
> **TMcKSmith said:**
> well how would I be able to access such a file?

Why wouldn't it let me install any packages?

Says it can't resolve URL...
You would use "cat /var/log/dpkg.log"

Your network is down.  This may be because it was being configured by a tool that has been removed.  

It sounds like you have a really serious problem.  You should never use the "autoremove" flag without careful thought.  Ubuntu uses some pretty hefty metapackages, and removing xauth probably knocked out xubuntu-desktop and the majority of the packages on your machine.  Reinstallation may be your only option.

---

### Post by TMcKSmith on 2009-01-30
Well, I hit "Alt + F" in the BIOS and it restored it to factory settings, which made the cdrom re-appear.  I ended up just re-installing though (but kept my /home partition).  Thanks for the help.

---

