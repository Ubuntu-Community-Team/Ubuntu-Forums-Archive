---
title: "Nautilus can't browse samba network hosts"
date: 2018-06-09
forum: Networking &amp; Wireless
---

### Post by s-byczkowski on 2018-06-09
Is it a gnome problem after upgrade to samba 4.7?
 If I do 
```
 
killall gvfsd-smb-browse && GVFS_DEBUG=1 /usr/lib/gvfs/gvfsd-smb-browse 
``` 
and click Windows Network in Nautilus, I can see one 
"send_reply(0x55c9be346150), failed=1 (Operation not supported by the processing engine)" message which,I think, is the culprit behind not working gnome samba browser - gvfsd-smb-browse. SO, clearly something is not working as it should.
```
 
smb-network: Queued new job 0x55c9be3461e0 (GVfsJobQueryFsInfo) 
smb-network: send_reply(0x55c9be3461e0), failed=0 () 
smb-network: backend_dbus_handler org.gtk.vfs.Mount:QueryInfo (pid=14663) 
smb-network: Queued new job 0x55c9be30e5f0 (GVfsJobQueryInfo) smb-network: send_reply(0x55c9be30e5f0), failed=0 () 
smb-network: backend_dbus_handler org.gtk.vfs.Mount:QueryInfo (pid=14663) 
smb-network: Queued new job 0x55c9be30e550 (GVfsJobQueryInfo) 
smb-network: send_reply(0x55c9be30e550), failed=0 () 
smb-network: backend_dbus_handler org.gtk.vfs.Mount:CreateDirectoryMonitor (pid=14663) 
smb-network: Queued new job 0x55c9be346150 (GVfsJobCreateMonitor) 
smb-network: [COLOR=#ff0000]send_reply(0x55c9be346150), failed=1 (Operation not supported by the processing engine)[/COLOR] 
smb-network: backend_dbus_handler org.gtk.vfs.Mount:QueryFilesystemInfo (pid=14663) 
smb-network: Queued new job 0x55c9be329f00 (GVfsJobQueryFsInfo) 
smb-network: send_reply(0x55c9be329f00), failed=0 () 
smb-network: backend_dbus_handler org.gtk.vfs.Mount:Enumerate (pid=14663) 
smb-network: Queued new job 0x55c9be322380 (GVfsJobEnumerate) 
smb-network: update_cache - updating... 
smb-network: looking up cached server '192.168.1.1'\'IPC$', user 'WORKGROUP';'seba' 
smb-network:   returning 0x7fc52400df30 
smb-network: update_cache - done. 
smb-network: send_reply(0x55c9be322380), failed=0 () 

```

---

### Post by Morbius1 on 2018-06-09
Edit /etc/samba/smb.conf.

If you don't have an smb.conf install smbclient: sudo apt install smbclient

Right below the workgroup = WORKGROUP line add this line:
```
client max protocol = NT1
```

Does it work now? If it does remember:

Good News: You should be able to browse again for samba / smb hosts.
Bad News: Even though you will be able to see it you will not be able to access any host that has disabled SMB1 - like Win10.

---

