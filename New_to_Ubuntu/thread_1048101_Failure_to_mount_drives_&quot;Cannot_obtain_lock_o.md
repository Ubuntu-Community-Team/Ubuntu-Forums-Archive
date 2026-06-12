---
title: "Failure to mount drives &quot;Cannot obtain lock on /media/.hal-mtab"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by tolle6 on 2009-01-23
Hi,

I've been running Ubuntu on my aspire one since I got it 6 months ago. It's been quite good to my even though I have t be considered a linux newbie. A couple of weeks ago I bought two sd-cards to expand storage capacity. I popped them in and they worked just fine. 
Today, on the other hand, they failed to mount.

Upon opening them I got this error message: 
"Unable to mount the volume"
"Cannot obtain lock on /media/.hal-mtab"

I've also tried mounting them as root by typing "sudo mount /disk". This generates the following error message:
" can't find /disk in /etc/fstab or /etc/mtab"

The same problem occurs if I try to mount a usb pen drive.

I found [http://www.linuxquestions.org/questions/showthread.php?t=694621&highlight=obtain+lock](http://www.linuxquestions.org/questions/showthread.php?t=694621&highlight=obtain+lock) this post and thought it might be related. Here's what happened when I tried:


tolle@one:/$ sudo rm /var/run/dbus/pid
tolle@one:/$ sudo dpkg-reconfigure hal
* Stopping Hardware abstraction layer hald [ OK ] 
* Reloading system message bus config... [ OK ] 
* Starting Hardware abstraction layer hald invoke-rc.d: initscript hal, action "start" failed.





Setup: Acer Aspire One
Ubuntu 8.10


I hope I've provided you with enough information and thank you in advance for the much needed help :)

---

### Post by nareshpunia on 2009-05-05
try this one

sudo mv /media/.hal-mtab /media/.hal-mtab.anything

reboot system and enjoy

---

### Post by MeanStreak on 2009-05-31
> **nareshpunia said:**
> try this one

sudo mv /media/.hal-mtab /media/.hal-mtab.anything

reboot system and enjoy

Thanks - could you perhaps include context around what this command does and what in effect it might fix?

---

### Post by Wangberg on 2009-07-14
> **nareshpunia] 	
Re: Failure to mount drives "Cannot obtain lock on /media/.hal-mtab
try this one

sudo mv /media/.hal-mtab /media/.hal-mtab.anything

reboot system and enjoy [/quote]

[QUOTE=MeanStreak said:**
> Thanks - could you perhaps include context around what this command does and what in effect it might fix?

I think what nareshpunia is trying to explain is if you rename the .hal-mtab file, it will recreate itself after reboot.

google .hal-mtab for more info on its functions.

---

### Post by jack5964 on 2010-02-08
I have had the same error message for days now and just solved it.  

for me the problem was basically a conflict with autofs.  

In auto.master i reference my /media folder as a mount point.  I think what was happenning is that autofs manages folders in its mount points and was preventing other programs (whatever process handles mounting usb devices) from accessing or writting to the media directory. hence /media/.hal-mtab could not be changed, and hence the error message.

my solution was to simply change the mount point to point to another folder. 

the mount point was:

/media    /etc/auto.nas --timeout=60 --ghost 

i changed it to 

/net    /etc/auto.nas --timeout=60 --ghost 

hope this helps someone 

cheers

---

### Post by *Boots* on 2010-02-22
I fixed my usb mounting blues by downloading a program from the software center and installing it. The program is called 'Mount Manager' . It worked for me!!!

Boots

---

### Post by *Boots* on 2010-03-03
I spoke too soon. My usb system is shot. Its an intermittent usb problem.

This is a bonafide bug in the system and needs to be fixed.  Please report your bugs. You'll find it in the launchpad under the following bug number: 
**#445160**

The URL to report the bug is: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/445160]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445160")

Boots

---

