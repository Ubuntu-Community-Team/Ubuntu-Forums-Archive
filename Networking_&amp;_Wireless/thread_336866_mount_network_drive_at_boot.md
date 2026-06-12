---
title: "mount network drive at boot"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by wessel_k on 2007-01-12
Hi,

I'm using Ubuntu for a year now and very satisfied with it, won't go back to windows, for that matter. 
But I have a small issue, about which I can't find anything on the forums. All other problems could easily be solved by searching the forums. Thanks for that also. ;) 

I'm using Edgy and I've add an extra line in my fstab to mount a directory on the server running Ubuntu Breezy, setup with Samba. This normally works, but when my pc boots and starts checking a drive he doesn't mount the network drive. 
Does anybody have a clue why this happens and/or how to solve this, besides running (sudo) mount -a?
I hope I've posted enough information here, if necessary don't hesitate to ask for more.

Hope anybody can help me out here.

Regards,

Wessel

---

### Post by dmizer on 2007-01-12
yes.  it is because of this bug: [https://launchpad.net/ubuntu/+source/hal/+bug/44874](https://launchpad.net/ubuntu/+source/hal/+bug/44874)

you can get around this one of two ways:
1) enable wins.  first part of the howto i have linked in my sig.  (this does not always work)
2) add the "mount -a" command to /etc/rc.local like so:

```
sudo nano /etc/rc.local
```
you'll see a file that looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```
add the words: [COLOR="Red"]mount -a[/COLOR] just before the "exit 0" line. so it will look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount -a
exit 0
```

save the file with a ctrl + x and type 'y' to save the modified buffer and hit enter.  reboot, and your share will be mounted.

---

### Post by wessel_k on 2007-01-12
Thanks already for your quick reply. I've already thought about adding to the boot script. I'll look into your suggested solutions this weekend and I'll post a follow up later on.

Regards,

Wessel

---

### Post by dmizer on 2007-01-12
adding to rc.local is probably your quickest, most painless, and doubt free fix for your problem.

the bug occurs in edgy because fstab does it's mounts prior to loading network modules, and the hal daemon doesn't work well with mounts pointed to ip addresses for some reason.

---

### Post by wessel_k on 2007-01-17
Yes, I agree that using rc.local is probably the best solution. But when I upgrade, you'll probably loose that change. 
For now I'm testing if using the computer-name instead of IP works. I'll keep you posted.

---

### Post by dmizer on 2007-01-17
i've had that setting in my rc.local since i first installed dapper on my machine at work.  it's gone through several kernel updates without affecting rc.local.

so, while i can't argue that rc.local will not change (because it does sometimes), for me ... it's rare enough that i don't consider it to be a problem.

how'd you fare on the name resolution?

---

### Post by wessel_k on 2007-01-17
Well for the moment I'm doing well with the name resolution. But when it slips I'm surely going to use the rc.local. 
Thanks for pointing out that you have such good experience with the file not changing on upgrades. It again shows that Ubuntu/Linux isn't as variable as some people assume it is. :D

---

### Post by wessel_k on 2007-01-31
Hi,

It's been a few weeks already since I changed the setting to using the computer/server name, but since it's working as a charme. I'm sure glad you pointed this out to me. If it goes wrong in the near future I'll start looking into using rc.local. But for now I'll stick to this solution. 
Thanks for the effort.

Regards,

Wessel

I shouldn't have posted this reply. It didn't solve the problem. ;-) I'm going to use the rc.local now.

---

### Post by Buck2348 on 2007-02-05
[http://www.ubuntuforums.org/showthread.php?t=103274](http://www.ubuntuforums.org/showthread.php?t=103274)

---

### Post by dmizer on 2007-02-05
> **wessel_k said:**
> I shouldn't have posted this reply. It didn't solve the problem. ;-) I'm going to use the rc.local now.

heh ... i believe that's the exact same experience i had.

here's a less simplistic but equally functional work around: [http://www.ubuntuforums.org/showthread.php?t=337482&page=6](http://www.ubuntuforums.org/showthread.php?t=337482&page=6) this could be used in a situation where you had to log in to ubuntu before you could get connected to the internet (in the case of a wep encrypted password entry).

---

### Post by dmizer on 2007-02-10
wouldn't you know it ... the last kernel update requires a re-edit of the /etc/rc.local file :oops:

---

### Post by wessel_k on 2007-02-12
That's funny.

I probably changed the rc.local after the latest upgrade. :guitar: 

It's working like a charm.

Thanks for your effort.

Regards,

Wessel

---

