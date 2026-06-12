---
title: "Ubuntu Server 14.10 doesn't mount NFS at startup anymore"
date: 2014-10-24
forum: Networking &amp; Wireless
---

### Post by marco-mattei on 2014-10-24
Hello

I just updated my server to version 14.10 and I noticed a strange thing:

My NFS Network Shares do not mount anymore at startup. I have 3 shares, that are mounted to /media/... for example /media/serien

So if I cd in that folder after a restart I get:
```
marco@server:~$ cd /media/serien
marco@server:/media/serien$ ll
insgesamt 8
drwxr-xr-x 2 root root 4096 Okt 17 15:50 ./
drwxr-xr-x 6 root root 4096 Okt 17 16:02 ../

```

But when I do sudo mount -a
the shares get mounted (so obviously it works)

When I then cd back to the folder and ll, everyhing is there as it should be.

So what is wrong with the mount@startup feature in 14.10? I need to have that, does someone have a solution?

Thanks

---

### Post by davidjo on 2014-10-24
Yes, I am suffering from the same issue.  This time upgrading from 14.04 to 14.10 of Kubuntu via muon-up.  My /etc/fstab file includs a mount to my local Synology NAS box, but I need to type "mount -a" for it to be mounted after start-up.

---

### Post by Jedimaniac on 2014-10-25
Just logged in to report that I am having the exact same problem with 14.10 desktop version.

Ubuntu will not see my QNAP box until i do a manual mount -a

Everything worked fine on 14.04

---

### Post by fredrik.floren on 2014-10-25
Same here. Worked beautifully on 14.04. With 14.10 it seems the network connection is up when at the login screen (at least directly after boot) but the connection is lost when logging in.

---

### Post by lacibaci on 2014-10-25
Same here. Worked fine in 14.04. Now it does not automount on boot. It will mount fine when I execute "mount -a"

---

### Post by lexius-java on 2014-10-25
Same here. Boot mount not working anymore with my QNAP NAS.

---

### Post by david12 on 2014-10-25
I'm having the same difficulty in 14.10.  Everything mounts with mount -a but nothing goes at startup.  I'm going to a Synology NAS. 

I would add that I had difficulty running a backup using *both* 'rsync' and 'Backups' over NFS in 14.04.  Rsync would start, run for a time, then it would just stop.  No error message, nothing, it just stopped well short of completion.  'Backups' returned "back up failed." I did have Synology tech support check out the NAS.  They found nothng wrong.

  I've not tried either 'rsync' or 'Backups' in 14.10 yet.

---

### Post by Mitchell_Taylor on 2014-10-25
I too am having troubles with a fresh installation of 14.10. I have a few nfs exports that are being served by a debian installation on my NAS that don't mount automatically via fstab on boot. They will mount if I run the command mount -a however.

---

### Post by Jedimaniac on 2014-10-26
have created a bug here if you wish to add any log files etc....

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1385846](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1385846)

---

### Post by davidjo on 2014-10-28
Until this is fixed, I've managed to get around the problem by adding this line to my cron list:

@reboot sleep 20 && mount -a

This is added via the "sudo crontab -e" command.  The delay is in seconds and is required otherwise it won't mount at all (which is probably the problem with the 14.10 install).

---

### Post by marco-mattei on 2014-10-29
Thanks, this helps. It was really awkward to have to mount them manually every time. And when I forgot, everyone in the house would complain because stuff didn't work. 

I mean, of course it's not ideal, but it's better than nothing. And I'm glad, I'm not the only person with this bug, so I'm sure now it's not a configuration issue (also because it happened with a fresh install.)

So I still hope this issue can be resolved somewhen, and I also hope they take it seriously. I just wonder what has changed from 14.04 to 14.10 to affect the nfs mount at startup.
And aparently there aren't so many people who use NFS mounts in 14.10, because then I'd guess this thread had more replys.

---

### Post by Mies on 2014-10-30
Similar issues on desktop version of Ubuntu 14.10 64bit.

---

### Post by P-I H on 2014-10-31
@[**[COLOR=#000000]davidjo[/COLOR]**]("http://ubuntuforums.org/member.php?u=1523443"), thanks
This workaround fixed the problem for me on the desktop version.
> Until this is fixed, I've managed to get around the problem by adding this line to my cron list:

@reboot sleep 20 && mount -a

This is added via the "sudo crontab -e" command.  The delay is in  seconds and is required otherwise it won't mount at all (which is  probably the problem with the 14.10 install).                 

---

### Post by marco-mattei on 2014-11-07
Yeah, it works that way, but it's not ideal. Because it seems like the cronjob mount -a is performed only after some programs start up (from the autostart).

That is not ideal, because when I reboot my server and look at the logs of said programs, I have multiple errors that sound like "Cannot create directory under /media/NFS" or "Unable to locate directory /media/NFS" and so on... And for some programs that's especially bad when they want to perform an operation in that exact moment, because they pause it and wait for me to say continue.

---

### Post by marco-mk-computing on 2014-11-11
Hello, just registered because, I've encountered the same issue with not mounting nfs. It seems to me, that nfs is intended to be mounted before network manager started the network. Up to 14.04 i used fixed network setup in /etc/network/interfaces. But with clean installation of 14.10 i decided to use NM to manage the network. 

Can someone support this observation?

--Edit--
Fix:
I replaced upstart with systemd and everything is working.

---

### Post by rowol2 on 2015-10-11
I just upgraded from 12.04 to 14.04...   I find the same issue with 14.04, NFS shares that used to automount during boot don't anymore.   (Some people had said it worked on 14.04... if it did, it doesn't seem to anymore.)

---

