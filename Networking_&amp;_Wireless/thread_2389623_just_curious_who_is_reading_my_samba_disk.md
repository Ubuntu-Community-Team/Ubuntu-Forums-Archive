---
title: "just curious: who is reading my samba disk?"
date: 2018-04-19
forum: Networking &amp; Wireless
---

### Post by lvm on 2018-04-19
On March 25th these records started to appear in my log.smbd 

```
[2018/03/25 09:02:55.669983,  0] ../source3/smbd/process.c:339(read_packet_remainder)
  read_fd_with_timeout failed for client 127.0.0.1 read error = NT_STATUS_END_OF_FILE.
```

So some local process is sniffing my samba. Frequency varies: some, but not many, days pass without these messages, on some days there may about a hundred of them. Samba was upgraded to 4.3.11 on March 15th and the server was rebooted on March 24th - may be related. With samba logging wound up to level 10 it looks like this:

```
[2018/04/19 12:27:02.394513,  3] ../source3/lib/access.c:338(allow_access)
  Allowed connection from 127.0.0.1 (127.0.0.1)
[2018/04/19 12:27:02.394888,  3] ../source3/param/loadparm.c:3754(lp_load_ex)
  lp_load_ex: refreshing parameters
[2018/04/19 12:27:02.395091,  3] ../source3/param/loadparm.c:548(init_globals)
  Initialising global parameters
[2018/04/19 12:27:02.395677,  3] ../source3/param/loadparm.c:2683(lp_do_section)
  Processing section "[global]"
[2018/04/19 12:27:02.396265,  2] ../source3/param/loadparm.c:2700(lp_do_section)
  Processing section "[u]"
[2018/04/19 12:27:02.396464,  2] ../source3/param/loadparm.c:2700(lp_do_section)
  Processing section "[htpc]"
[2018/04/19 12:27:02.396647,  2] ../source3/param/loadparm.c:2700(lp_do_section)
  Processing section "[backup]"
[2018/04/19 12:27:02.396898,  3] ../source3/param/loadparm.c:1600(lp_add_ipc)
  adding IPC service
[2018/04/19 12:27:02.397241,  2] ../source3/lib/interface.c:341(add_interface)
  added interface eth2 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
[2018/04/19 12:27:02.397411,  3] ../source3/smbd/oplock.c:1310(init_oplocks)
  init_oplocks: initializing messages.
[2018/04/19 12:27:32.391894,  0] ../source3/smbd/process.c:339(read_packet_remainder)
  read_fd_with_timeout failed for client 127.0.0.1 read error = NT_STATUS_END_OF_FILE.
[2018/04/19 12:27:32.392569,  3] ../source3/smbd/server_exit.c:252(exit_server_common)
  Server exit (failed to receive smb request)
[2018/04/19 12:31:32.815377,  2] ../source3/smbd/server.c:467(remove_child_pid)
  Could not find child 4423 -- ignoring
```

I see nothing helpful here. Running smbstatus while this is going on as 'tail -n 0 -f log.smbd|(while read f; do echo $f; smbstatus; done)' shows no connections. Any ideas how to catch the culprit?

---

### Post by kerry_s on 2018-04-19
never mind didn't read clearly.

your trying to figure out what process.
you say every few days, so it has to be some kind of cron job.

---

### Post by lvm on 2018-04-19
no, sometimes many times a day, sometimes - none. As far as I can see it happens when I am using this computer locally.

---

### Post by kerry_s on 2018-04-19
i'm thinking some kind of indexing for changes, updatedb maybe?

---

### Post by lvm on 2018-04-20
Turned out, it is seamonkey. It shouldn't do it - profile is local, no web pages are opened from samba. Curiouser and curiouser...

```
smbd       4261     root   35u  IPv4 2612048      0t0  TCP localhost:445->localhost:44414 (ESTABLISHED)
seamonkey 32169      lvm   80u  IPv4 2616552      0t0  TCP localhost:44414->localhost:445 (ESTABLISHED)
```

---

