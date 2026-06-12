---
title: "CIFS mounted NAS, waking every 15 minutes after 19.10 upgrade"
date: 2019-11-05
forum: Networking &amp; Wireless
---

### Post by various-artists on 2019-11-05
Hi! First post, so hopefully I'm posting in the right place.

I've got a Western Digital NAS drive mounted to a server running Ubuntu 19.10, which i've recently upgraded from 19.04.

The NAS drive runs a standard desktop hard drive (rather than anything rated for 24/7 run time), and because of this, is factory set to go into standby after 10 minutes of inactivity.

This worked fine in 19.04 Cosmic (and 18.10 Disco), and would only spin up when I wanted to access something on the drive.

Since the upgrade, my NAS drive wakes up every 15 minutes, and I can't seem to figure out why that is.

Drive is mounted using in fstab;

```
//192.168.1.150/Drive /home/user/drive cifs username=username,password=username,_netdev,uid=user,vers=2.0 0 0
```

I turned the Samba debug level up, and took this from the NAS log;

```
[2019/11/03 17:06:59.026977,  1] smbd/server.c:300(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2019/11/03 17:06:59.035727,  2] auth/auth.c:309(check_ntlm_password)
  check_ntlm_password:  authentication for user [user] -> [user] -> [user] succeeded
[2019/11/03 17:06:59.040943,  1] smbd/service.c:1081(make_connection_snum)
   (192.168.1.150) connect to service Drive initially as user user (uid=1000, gid=1000) (pid 27187)
[2019/11/03 17:07:19.038045,  1] smbd/server.c:272(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2019/11/03 17:21:59.665149,  2] smbd/process.c:2455(deadtime_fn)
  Closing idle connection
[2019/11/03 17:21:59.665862,  1] smbd/service.c:1345(close_cnum)
   (192.168.1.150) closed connection to service Drive
[2019/11/03 17:21:59.676456,  1] smbd/server.c:300(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2019/11/03 17:21:59.684930,  2] auth/auth.c:309(check_ntlm_password)
  check_ntlm_password:  authentication for user [user] -> [user] -> [user] succeeded
[2019/11/03 17:21:59.690076,  1] smbd/service.c:1081(make_connection_snum)
   (192.168.1.150) connect to service Drive initially as user user (uid=1000, gid=1000) (pid 27838)
[2019/11/03 17:22:19.687294,  1] smbd/server.c:272(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2019/11/03 17:30:52.213688,  1] smbd/service.c:1345(close_cnum)
   (192.168.1.150) closed connection to service Drive

```

And the thing just constantly repeats. Drive sleeps after 10 minutes of inactivity, then after 5 minutes wakes back up. Thinking it's going to eventually kill the drive.

I tried this with clean installs of 19.04 and 19.10, and it's the same. No issue at all with 19.04, but waking every 15 minutes on 19.10. As soon as the "closed connection to service," log notification comes up, it attempts to remount instantly, spinning up the drive.

Not sure if it matters, but the NAS runs a pretty old version of Samba, so SMB2 is the highest supported.

Wondered if some default has changed in the way Eoan mounts, and that I need to add an additional option to the fstab entry, to stop it remounting every 15 minutes?

Grasping at straws, I also tried to downgrade the, "Mount" package to an older version from 19.04, but then it wouldn't boot.... Not an ideal solution, even if it worked.

Is there a log file for what the samba client is doing? I had a browse though the syslog, but nothing stood out as relevant for this.

Thought i'd run it past you guys, before I start to rebuild everything on a clean LTS release... Which i'd rather avoid doing. :p Cheers!

---

### Post by TheFu on 2019-11-05
Use **autofs**, not the fstab to mount USB and network storage.  This way, it will only be mounted when actually used.

If you really want to troubleshoot what is scanning the disks every 15 minutes, use lsof to see which process is accessing directories on it when it starts up.  Something like:
```
sudo lsof |grep  /media/path/to/cifs
```

But autofs will work better.  Another option is to use NFS, if that is available, instead of CIFS.

---

### Post by various-artists on 2019-11-05
Thanks TheFu. I'll look into autofs; it's not something i've used before.

When I run the lsof command, nothing comes up, even just after the drive has just woken up, and a samba log line has been written on the NAS server. Guess I should be running this multiple times, and outputting to a log?

The NAS does support NFS, which I mounted using fstab again, but noticed the speeds where much slower than CIFS when testing using dd, even when using the "async" option. (Around 20 MB/s, where as with CIFS its up to 40 MB/s. Again, it's a pretty old NAS, and only supports up to NFSv3.)

---

