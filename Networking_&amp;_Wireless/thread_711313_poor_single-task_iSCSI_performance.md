---
title: "poor single-task iSCSI performance"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by davidleelambert on 2008-02-29
We have some Gentoo and Windows boxes running iSCSI across a gigabit Ethernet switch to a NetApp filer.  I just set up an Ubuntu Gutsy host connected to the same SAN and installed the [open-iscsi ]("http://packages.ubuntu.com/gutsy/net/open-iscsi") package, and I'm getting terrible read performance ... but only under certain conditions.

(This host will be used for backups,  and it has a tape autochanger attached.  We would like to take snapshots on the filer, mount those, and copy them to tape.)

If I read files or a single large file from the LUN with a single process, I get 4 MB/s.

If I read files or a single large file from the LUN using two processes running in parallel,  I get about 50 MB/s together.  That is,  if I run a command like

```

dd if=/mnt/lun0p1/some-large-file of=/dev/null & \
  dd if=/mnt/lun0p2/another-copy-of-some-large-file of=/dev/null & \
  sleep 60

```

one process reports 22 MB/s and the other reports 30 MB/s.  (I get similar results with "time tar" on two trees of files).  

When copying a large file to local disk from another host with SSH I get 22 MB/s; copying the same file to a partition on the LUN with SSH,  16 MB/s.

On a Gentoo box (not quite the same hardware, either), I get 64 MB/s read speed for a single process and 48 MB/s per process if I run two processes in parallel.

Now,  for writing to tape we expect to have a single process reading from the SAN,  so for this host single-process read speed really matters.  Has anyone else seen this kind of problem?  Any ideas on what to do to fix it?

--
DLL

---

