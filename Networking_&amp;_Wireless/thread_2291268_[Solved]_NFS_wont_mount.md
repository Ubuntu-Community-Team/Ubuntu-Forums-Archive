---
title: "[Solved] NFS wont mount"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by darren2 on 2015-08-18
**Server Side:**
  /etc/exports
  ```
[INDENT] /media/drseuss/1400 192.168.1.*client*(rw,nohide,insecure,no_subtree_check,async)

 [/INDENT]

```  /etc/hosts.deny
  ```
[INDENT] rpcbind mountd nfsd statd lockd rquotad : ALL

 [/INDENT]

```  /etc/hosts.allow
  ```
[INDENT] rpcbind mountd nfsd statd lockd rquotad : 192.168.1.*client* 192.168.1.*server*

 [/INDENT]

```  [HR][/HR]  **Client:**
  ```
[INDENT] showmount -e 192.168.1.*server*  

 [/INDENT]

```  gives  
  ```
[INDENT] Export list for 192.168.1.*server*:
/media/drseuss/1400 192.168.1.*client*

 [/INDENT]

```  ----------------and-----------------------
  ```
[INDENT] sudo mount -t nfs -v 192.168.1.*server*:/media/drseuss/1400 /media/htpc/1400

 [/INDENT]

```  gives
  ```
[INDENT] mount.nfs: timeout set for Tue Aug 18 18:52:36 2015
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.*server*,clientaddr=192.168.1.*client*'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.*server*:/media/drseuss/1400  

 [/INDENT]

```

I found out that kodi can access the share, but the mount command stilll cannot.
What gives, why wont this mount?
  Thanks in advance.

---

### Post by SeijiSensei on 2015-08-19
Try adding "no_root_squash" to the list of options in /etc/exports.

---

### Post by darren2 on 2015-08-19
That looks like it did it, thank you very much.

---

