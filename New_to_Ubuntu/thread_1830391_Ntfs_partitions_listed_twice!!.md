---
title: "Ntfs partitions listed twice!!"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by rj7 on 2011-08-21
Hi,
   I recently install ntfs-config and ntfs-3g to automount my other partitions. After using this i found i could not unmount  the partions. Just out of curiosity to know what actually happened i unistalled ntfs-config and ntfs-3g packages.
   Still i had that problem. So i installed pysdm(storage device manager). Then i had new problem. My partitions are listed twice in places and in side pane. 
   Could someone pls help me remove it...
   I have attached the screen shot..

---

### Post by coffeecat on 2011-08-21
First thing - you wouldn't have installed ntfs-3g. It would have been installed already - it comes as default. You need to reinstall it; it provides the driver for reading and writing to NTFS fileystems. Without it you will not be able to use your NTFS partitions. I suggest you reinstall that package.

And now to ntfs-config and pysdm, two packages unmaintained for years and which sometimes do more harm than good. Uninstall pysdm and then run this terminal command:

```
cat /etc/fstab
```

Highlight the output with the mouse, right-click and select copy. Then paste it into your post between [noparse]```
 and 
```[/noparse] tags for readability. We can then see what those two apps have done to your /etc/fstab and undo the damage. Unfortunately pysdm also mucks about with udev rules and we might need to look as those as well. But let's start with your /etc/fstab first.

---

### Post by rj7 on 2011-08-22
Thanks for replying
Can i delete my post if i had posted wrongly.. I can edit but couldnt delete...

---

### Post by rj7 on 2011-08-22
And by the way thanks for replying coffeecat... 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc               proc  nodev,noexec,nosuid                0  0  
#Entry for /dev/sda9 :
UUID=1780f923-3682-4867-841a-dcc0975afb6a  /                   ext4  errors=remount-ro                  0  1  
#Entry for /dev/sda7 :
UUID=588ACD678ACD41EC                      /media/IMPORTANT!!  ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda5 :
UUID=1CA2CE40A2CE1E60                      /media/Media        ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda2 :
UUID=863C1AC43C1AAEE5                      /media/RECOVERY     ntfs  nls=utf8,ro,noauto,umask=0222      0  0  
#Entry for /dev/sda6 :
UUID=50C2A213C2A1FCFA                      /media/Study        ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda3 :
UUID=40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda1 :
UUID=07DA-071B                             /media/sda1         vfat  noauto                             0  0  
UUID=28d37f3b-98f9-42dc-ae1e-b2a2dfb42246  none                swap  sw                                 0  0  
#Entry for /dev/sda8 :
UUID=ec1b57bd-79fd-47d3-a98b-e4ddf9fdfa31  /media/sda8         swap  defaults                           0  0  


```

---

### Post by oldfred on 2011-08-22
If you mount in /media or /home Nautilus often mounts it again. You can mount elsewhere and link into /home or this work around.

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

Your swap does not look corect:
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")

This is my swap entry:
```
# swap was on /dev/sdc10 during installation
UUID=09367687-86d1-4fd0-9b81-2787d3196159 none            swap    sw              0       0

```

---

### Post by rj7 on 2011-08-22
Sorry I could understand much of this... Can you pls help me... They have posted something like this..

Instead of using LABEL=xx, specify disk with /dev/disk/by-label/xx
For UUID=xx it is /dev/disk/by-uuid/xx
 This works great and it solves my reported problem, so this bug report may be invalid now.
However since /etc/fstab supports specifying disks by LABEL=xx or  UUID=xx and various howto show this method, I think that this should  still be supporte

---

### Post by rj7 on 2011-08-22
Sorry man i got the problem fixed...
But can i just know what i actually did...
Just to understand things better!!!!!
By the way thanks for helping....

---

### Post by coffeecat on 2011-08-22
> **rj7 said:**
> Sorry man i got the problem fixed...

Would you like to share what you did? Others search the forum for problems similar to their own and get very frustrated when the OP says that it is fixed without explaining how.

> **rj7 said:**
> But can i just know what i actually did...

Only you know what you actually did, if you don't tell us.

Do you need any more help or can I unsubscribe from this thread?

---

### Post by rj7 on 2011-08-23
I thought i was the one who could nt understand from that 
What i did was replaced this
```

UUID=40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0222,user  0  0

```with
```

/dev/disk/by-uuid/40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0222,user  0  0 

```
for every entry in my /etc/fstab

---

