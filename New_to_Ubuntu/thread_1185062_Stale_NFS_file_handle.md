---
title: "Stale NFS file handle?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Oded on 2009-06-11
Hi,
I have a problem with one of the folders in my home partition giving the following error:```
ls: cannot access themes: Stale NFS file handle

```
I've searched for a solution on various sites but haven't had success, could anyone help?

Thanks

---

### Post by Cypher on 2009-06-12
That folder seems to be a something that's mounted from a remote server through NFS. For performance sake, NFS doesn't do file locking, which means your view of the remote filesystem is OK as long as you are the only one changing it through the NFS mount. Should something change on the remote system, without the NFS locking in place, you get out of sync. This will usually trigger the "Stale NFS file handle" message when accessing a particular file.

The quick solution is to unmount and remound the remote location to reset NFS..

---

