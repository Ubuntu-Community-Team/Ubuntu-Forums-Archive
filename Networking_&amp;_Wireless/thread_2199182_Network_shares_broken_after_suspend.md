---
title: "Network shares broken after suspend"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by erik070 on 2014-01-12
I've edited /etc/fstab so my smb shares mount automaticly (Windows 7 shares). It all works, but when my laptop resumes from suspend the networks shares aren't working anymore. I can still see them mounted in Nautilus, but when I try to access them nothing seems to happen for a while and then this error appears: 
"Unhandled error message: Error when getting information for file '/media/data3': Resource temporarily unavailable"

If I logout and login again after this happens, it will all work again.

I dont't know if I did something wrong in my fstab file or if there is something else going wrong. Could not find similar cases, only thing I could find that it maybe has something to do with the network shares not unmounting when going into suspend mode.

This what my fstab file looks like (I replaced my username and password with XXXX):

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=3adecac0-856f-4380-be74-c39eb1d08b13 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
//192.168.1.5/episodes  /media/episodes  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
//192.168.1.5/data3  /media/data3  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
//192.168.1.5/download  /media/download  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
//192.168.1.5/data2  /media/data2  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
//192.168.1.5/data  /media/data  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
//192.168.1.5/movies  /media/movies  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
//192.168.1.5/data4  /media/data4  cifs  username=XXXX,password=XXXX,uid=1000,iocharset=utf8,sec=ntlm  0  0
```

---

### Post by tomearp on 2014-01-12
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404917") on Launchpad that sounds very similar to your issue. It has not been active for some time until recently. It may be worth making yourself known on there to re-raise the issue.

---

### Post by erik070 on 2014-01-13
I don know if it's the same bug. I'm getting other messages than he is. I also don't really know what he is asking in the lastest post on lauchpad (still very newby to Linux/Ubuntu). I'm afraid to mess up my system by updating the kernel etc. like he asked.

The "funny" thing is, I'm getting a different error today: 
Unable to access &#8220;data3&#8221;
mount: only root can mount //192.168.1.5/episodes on /media/data3

Also, loging out and in again did not fix it this time. Only after a reboot it worked again.

---

### Post by erik070 on 2014-01-26
Haven't changed anything the last week. But problem seems to be less frequent, now most of the times it works.

So for now problem is kinda solved for me.

---

