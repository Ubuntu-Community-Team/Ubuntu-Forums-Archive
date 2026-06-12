---
title: "kernel backtrace in nfs_idmap_legacy_upcall"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by doesntcount on 2014-01-11
I'm running ubuntu for arm on a beaglebone black. Since upgrading recently, after a few minutes after boot, and mostly randomly, it stops responding to tcp connections (can't ssh, etc). I can still ping, but that's it.

Took a look in syslog and found this:

```
Jan  7 21:27:01 beaglebone kernel: [ 7092.758620] ------------[ cut here ]------------
Jan  7 21:27:01 beaglebone kernel: [ 7092.758675] WARNING: at fs/nfs/idmap.c:663 nfs_idmap_legacy_upcall+0xf4/0x174()
Jan  7 21:27:01 beaglebone kernel: [ 7092.758686] Modules linked in: tun g_multi libcomposite autofs4 nfsd exportfs
Jan  7 21:27:01 beaglebone kernel: [ 7092.758757] [<c0013558>] (unwind_backtrace+0x0/0xe0) from [<c003b54c>] (warn_slowpath_common+0x4c/0x64)
Jan  7 21:27:01 beaglebone kernel: [ 7092.758778] [<c003b54c>] (warn_slowpath_common+0x4c/0x64) from [<c003b57c>] (warn_slowpath_null+0x18/0x1c)
Jan  7 21:27:01 beaglebone kernel: [ 7092.758799] [<c003b57c>] (warn_slowpath_null+0x18/0x1c) from [<c0204304>] (nfs_idmap_legacy_upcall+0xf4/0x174)
Jan  7 21:27:01 beaglebone kernel: [ 7092.758828] [<c0204304>] (nfs_idmap_legacy_upcall+0xf4/0x174) from [<c02c4910>] (request_key_and_link+0x340/0x3ec)
Jan  7 21:27:01 beaglebone kernel: [ 7092.758851] [<c02c4910>] (request_key_and_link+0x340/0x3ec) from [<c02c4a20>] (request_key_with_auxdata+0x20/0x54)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759559] [<c02c4a20>] (request_key_with_auxdata+0x20/0x54) from [<c02040dc>] (nfs_idmap_request_key+0xac/0x180)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759609] [<c02040dc>] (nfs_idmap_request_key+0xac/0x180) from [<c0204964>] (nfs_idmap_lookup_id+0x80/0xc4)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759631] [<c0204964>] (nfs_idmap_lookup_id+0x80/0xc4) from [<c0204d30>] (nfs_map_group_to_gid+0x4c/0x58)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759787] [<c0204d30>] (nfs_map_group_to_gid+0x4c/0x58) from [<c01f99fc>] (decode_getfattr_attrs+0x6a4/0xc28)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759819] [<c01f99fc>] (decode_getfattr_attrs+0x6a4/0xc28) from [<c01fd6dc>] (decode_getfattr_generic.constprop.63+0x84/0xa4)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759924] [<c01fd6dc>] (decode_getfattr_generic.constprop.63+0x84/0xa4) from [<c01fee00>] (nfs4_xdr_dec_getattr+0x58/0x60)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759950] [<c01fee00>] (nfs4_xdr_dec_getattr+0x58/0x60) from [<c05f013c>] (rpcauth_unwrap_resp+0x58/0x60)
Jan  7 21:27:01 beaglebone kernel: [ 7092.759976] [<c05f013c>] (rpcauth_unwrap_resp+0x58/0x60) from [<c05e7350>] (call_decode+0x2b8/0x324)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760026] [<c05e7350>] (call_decode+0x2b8/0x324) from [<c05eeee0>] (__rpc_execute+0xb4/0x310)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760130] [<c05eeee0>] (__rpc_execute+0xb4/0x310) from [<c05e897c>] (rpc_run_task+0x98/0xa4)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760152] [<c05e897c>] (rpc_run_task+0x98/0xa4) from [<c05e8af0>] (rpc_call_sync+0x90/0xb4)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760183] [<c05e8af0>] (rpc_call_sync+0x90/0xb4) from [<c01f0158>] (nfs4_call_sync+0x4c/0x50)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760207] [<c01f0158>] (nfs4_call_sync+0x4c/0x50) from [<c01f0834>] (_nfs4_proc_getattr+0x9c/0xa8)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760229] [<c01f0834>] (_nfs4_proc_getattr+0x9c/0xa8) from [<c01f4a18>] (nfs4_proc_getattr+0x38/0x5c)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760365] [<c01f4a18>] (nfs4_proc_getattr+0x38/0x5c) from [<c01e0fb4>] (__nfs_revalidate_inode+0x88/0x114)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760388] [<c01e0fb4>] (__nfs_revalidate_inode+0x88/0x114) from [<c01e12d8>] (nfs_getattr+0x94/0xd8)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760420] [<c01e12d8>] (nfs_getattr+0x94/0xd8) from [<c00f9680>] (vfs_getattr+0x40/0x5c)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760442] [<c00f9680>] (vfs_getattr+0x40/0x5c) from [<c00f96f0>] (vfs_fstatat+0x54/0x8c)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760652] [<c00f96f0>] (vfs_fstatat+0x54/0x8c) from [<c00f994c>] (sys_stat64+0x14/0x30)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760683] [<c00f994c>] (sys_stat64+0x14/0x30) from [<c000d880>] (ret_fast_syscall+0x0/0x30)
Jan  7 21:27:01 beaglebone kernel: [ 7092.760697] ---[ end trace 0fdab910246c5b09 ]---
Jan  7 21:35:44 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 21:45:48 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 21:49:43 beaglebone kernel: [ 8454.915483] omap_i2c 44e0b000.i2c: controller timed out
Jan  7 21:49:43 beaglebone kernel: [ 8454.926170] dummy 0-0034: Error -110 reading from cec:0xfe
Jan  7 21:55:48 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 22:05:49 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 22:11:40 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'doesntcount' not found in domain 'localdomain'
Jan  7 22:15:02 beaglebone CRON[2727]: (*****) CMD (/usr/local/bin/flexget --cron -c /home/*****/.flexget/config.yml > /dev/null 2>&1)
Jan  7 22:15:56 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 22:17:02 beaglebone CRON[2769]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  7 22:24:29 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'doesntcount' not found in domain 'localdomain'
Jan  7 22:26:32 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 22:36:36 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 22:54:58 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 23:00:24 beaglebone ovpn-Netherlands[789]: read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Jan  7 23:05:08 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 23:15:02 beaglebone CRON[3112]: (*****)CMD (/usr/local/bin/flexget --cron -c /home/*****/.flexget/config.yml > /dev/null 2>&1)
Jan  7 23:15:21 beaglebone rpc.idmapd[388]: nss_getpwnam: name 'nobody' does not map into domain 'localdomain'
Jan  7 23:17:02 beaglebone CRON[3150]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

My best hunch is that NFS kernel warning is causing the death of my tcp stack. Can anybody suggestion some ways to debug this? Should I be filing a bug report for this? Anybody have any ideas on workarounds?

Appreciate the help here.

---

