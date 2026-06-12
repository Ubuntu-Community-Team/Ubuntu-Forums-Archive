---
title: "Home directories on a server"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by IT_NERD on 2009-02-05
Hi,

I was wondering if there are any way to direct all users' home directories onto an openSolaris server without any user intervention?

---

### Post by xopher_mc on 2009-02-05
you want to set up a nis with automount.

---

### Post by ibutho on 2009-02-05
> **xopher_mc said:**
> you want to set up a nis with automount.
Did you mean NFS? I am sure its NFS that enables exporting of directories to other machines.

---

### Post by xopher_mc on 2009-02-05
> **ibutho said:**
> Did you mean NFS? I am sure its NFS that enables exporting of directories to other machines.

Yes you need to export the files with nfs share for it to work. 


i think this might be a how to

[http://wiki.ubuntu.org.cn/index.php?title=Quick_HOWTO_:_Ch30_:_Configuring_NIS&variant=zh-hant](http://wiki.ubuntu.org.cn/index.php?title=Quick_HOWTO_:_Ch30_:_Configuring_NIS&variant=zh-hant)

---

