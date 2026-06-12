---
title: "SAMBA problem -- perhaps I erred"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by BadAstronaut on 2008-05-01
Earlier this week I [posted in the Absolute Beginners forum]("http://ubuntuforums.org/showthread.php?t=773056") about my problem with my new Ubuntu server hanging on large SMB transfers.

I guess that due to the traffic over there in the wake of the new release, I never really had a chance.

Would this be a better venue?  (I **am** an absolute beginner, but completely comfortable poking around under the hood if someone can tell me what it is I might be looking for.)

---

### Post by SpaceTeddy on 2008-05-02
mhm - does your samba or your syslog give you any errors once the system is unresponsive ? please check that in your /var/log/syslog and the directory /var/log/samba. 
that might contain a hint to what is happening.

also is this a problem concerning the 4GB filesize (i.e. files that are larger than 32-bit in filesize) ? or does this occur randomly (i.e. being able to copy one file, and then on the next attempt not being able to copy it).

sorry to say that my ideas are very limited at the moment towards this question - i am just trying to get some information to i might start getting ideas.

and yes, i have read the other post :)

---

### Post by BadAstronaut on 2008-05-03
Yes, it does appear that files under 4GB make it through fine.  And yesterday I tried *pulling* a file (over 4GB) from my XP machine with smbclient, and that completed without complaint as well.  (I saw someone mention this in their own troubleshooting efforts elsewhere.)  I have also noticed that I still get a ping response from the server even after everything else seems to have locked up completely.

On to the logs.  If you see anything interesting here, let me know:

**syslog**

```

May  2 23:15:45 moria xinetd[5049]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
May  2 23:15:45 moria xinetd[5049]: Started working: 1 available service
May  2 23:15:46 moria /usr/sbin/cron[5129]: (CRON) INFO (pidfile fd = 3)
May  2 23:15:46 moria /usr/sbin/cron[5130]: (CRON) STARTUP (fork ok)
May  2 23:15:46 moria /usr/sbin/cron[5130]: (CRON) INFO (Running @reboot jobs)
May  2 23:17:01 moria /USR/SBIN/CRON[5240]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  2 23:19:47 moria ntpd[3794]: synchronized to 91.189.94.4, stratum 2
May  2 23:19:47 moria ntpd[3794]: time reset -1.000927 s
May  2 23:19:47 moria ntpd[3794]: kernel time sync status change 0001
May  2 23:24:15 moria modprobe: WARNING: Not loading blacklisted module ipv6
May  2 23:24:19 moria last message repeated 2 times
May  2 23:26:40 moria ntpd[3794]: synchronized to 129.174.93.11, stratum 2
May  2 23:28:32 moria kernel: [  851.648179] Clocksource tsc unstable (delta = 14061298724 ns)
May  2 23:28:32 moria kernel: [  851.652143] Time: acpi_pm clocksource has been installed.
May  2 23:32:00 moria ntpd[3794]: synchronized to 67.207.133.173, stratum 2
May  2 23:36:28 moria ntpd[3794]: synchronized to 129.174.93.11, stratum 2
May  2 23:40:01 moria ntpd[3794]: synchronized to 67.207.133.173, stratum 2
May  2 23:53:32 moria ntpd[3794]: no servers reachable
May  3 00:02:05 moria ntpd[3794]: synchronized to 129.174.93.11, stratum 2
May  3 00:02:05 moria ntpd[3794]: time correction of 1537 seconds exceeds sanity limit (1000); set clock manually to the correct UTC time.
May  3 00:15:34 moria -- MARK --
May  3 00:17:02 moria /USR/SBIN/CRON[5678]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

**samba.log**

```
[2008/05/01 23:52:05, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:52:15, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:52:25, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:52:35, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:52:45, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:52:55, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:53:05, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:53:15, 0] nmbd/nmbd_serverlistdb.c:write_browse_list(350)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/05/01 23:53:25, 0] nmbd/nmbd_sendannounce.c:browse_sync_remote(549)
  browse_sync_remote: Cannot find workgroup WORKGROUP on subnet 192.168.2.98

```

I believe that those nmbd errors are new since upgrading to Hardy (my workgroup is **not** named WORKGROUP) but I'm presuming these entries are unrelated to my problem & not worth talking about.

From the client-specific logfile:

```
[2008/05/02 23:52:21, 1] smbd/service.c:make_connection_snum(1033)
isengard (192.168.2.44) connect to service video initially as user tom (uid=0, gid=1000) (pid 5524)
[2008/05/02 23:52:21, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 192.168.2.44. Error Broken pipe
[2008/05/02 23:52:21, 0] lib/util_sock.c:send_smb(769)
  Error writing 51 bytes to client. -1. (Broken pipe)
[2008/05/02 23:52:21, 1] smbd/service.c:close_cnum(1230)
  isengard (192.168.2.44) closed connection to service video

```

Thanks for any input you can offer.  I appreciate it.

---

### Post by wedge2k on 2008-05-03
I have the same exact problem.  I'm using the same smb.conf i've used for some time now, only now once i've updated to hardy am i getting this problem.  I can connect to a windows box from the same machine.  Just not my ubuntu box. Same errors as previous post.  My windows box asks for username and password, it shouldn't  its setup to accept guest logins.  My xbox can connect to the shares just fine.

---

### Post by BadAstronaut on 2008-05-03
> **wedge2k said:**
> Same errors as previous post.  My windows box asks for username and password, it shouldn't  its setup to accept guest logins.  My xbox can connect to the shares just fine.

The "same errors" you're referring to are the ones from my samba.log, the client-specific log, or both?

I'm inclined to think that the "cannot find my workgroup WORKGROUP" errors I was experiencing was the result of tinkering I had done in an attempt to solve my bigger problem.  Once I restarted smbd (through the SWAT interface) these "cannot find my workgroup WORKGROUP" errors disappeared.

The "broken pipe" stuff persists, unfortunately.

---

### Post by SpaceTeddy on 2008-05-04
sorry for not answering for such a long time.

I have been searching via google about this for a while, but could not come up with a solution. If the theory about the 4 GB size is right, then this is either a bug in samba (some overflow of a 32-bit int that occures), or an error in your filesystem which is not able to write past the 4GB barrier on your destination drive. 

why this came now, i don't know. I am also no expert on samba. The strange thing is that it just happened with hardy - so i would expect this to be a bug in samba (i know samba can handle files bigger thatn 4Gbyte on my server - version 3.0.24-6etch9 on debian etch). 
So, make sure the underlaying filesystem takes +4Gbyte files (i.e. anything but fat and fat32 i think) and run a couple of tests if this only occurs when a transfer hits the 4GByte barrier.
Also, try to install samba from a different source (this is ugly !) and see if the problem persists (after you have checked the filesystem).

no other ideas - sorry guys... :(

---

### Post by BadAstronaut on 2008-05-04
Thanks for all your effort, Ted.

Just to clarify...

I was actually running Gutsy on this machine for a couple of weeks before the Hardy release, and was having the same problem.

The filesystem of the destination is XFS, so that's not likely the cause of the (apparent) 4GB barrier.  (I **have** been able to sporadically complete a transfer of over 4GB ... but have never had a problem with ones under 4GB.  So far.)

Is there somewhere I can look to see what's happening at a higher level, perhaps with xinetd?  What really intrigues me is the loss of SMB, SSH, and HTTP connectivity while the machine still responds to pings like a pro.

And on a related topic: I often see people reporting their transfer rates between machines, but have yet to discover any way to clock my throughput.  Is there something easy I'm missing?

I think I'll take your advice and reinstall SAMBA (compiled from source if I have to) and see whether that has any (positive) effect.  Either that, or I'll just get FTP up & running and admit defeat.  :???:

---

### Post by SpaceTeddy on 2008-05-04
for simple network stats on devices, i use iptraf.
that is small, has a nice frontend and displayes pretty much anything one needs...

as for loggin the traffic - either do that via iptables LOG destination, or via tcpdump for a certain interface.

i don't really have time right now - i'll explain later about the dumping of transmission data (if no one else does it beforehand :) )

cheers

---

### Post by BadAstronaut on 2008-05-29
I'm back, and I now think I may have mis-characterized my problem.

It occurred to me that all of my failures have been in transferring large files to a SMB share on an XFS volume.  So I've tried copying over the same files to a share on an EXT3 volume and have had _no hangs thus far_.

(Background:  Both volumes exist on a 3-disk software RAID 5 array with LVM on top.)

After wading through a bunch of Google results, I'm intrigued by the possibility that increasing /sys/block/md2/md/stripe_cache_size to 1024 (or greater) might be a step in the right direction, but I'm not sure how to do this.  (And I suppose this is now the wrong forum category to be asking ... perhaps I should take it to Server Platforms instead?)

**Update:** Taking a wild guess, I added my stripe_cache_size value override to rc.local and rebooted.  First test (with an 8.5GB file) completed successfully, but the second didn't complete & hung the system again.

I've seen [postings elsewhere]("http://kerneltrap.org/mailarchive/linux-kernel/2007/11/4/384680") that imply a kernel patch by Neil Brown resolved such issues a few kernel revisions ago, but that stuff is (currently) way over my head, so I'm unsure what it all means.

---

### Post by dando80 on 2008-10-24
Hi BadAstronaut,

I was wondering if you could provide the details of how you added the stripe_cache_size change to your startup scripts?

I am using intrepid and cannot see an "stripe_cache_size" file in /sys/block/mdX/md

where X is any of my 3 arrays.

Thanks a lot...

---

### Post by BadAstronaut on 2008-10-26
Dando,

I simply edited rc.local (with nano from the command line) and added the line

```
echo 16384 > /sys/block/md2/md/stripe_cache_size
```

You may need to create the empty stripe_cache_size file before attempting to echo to it.  (??  Just a guess.  I don't recall if I had one there before making this change.)

---

