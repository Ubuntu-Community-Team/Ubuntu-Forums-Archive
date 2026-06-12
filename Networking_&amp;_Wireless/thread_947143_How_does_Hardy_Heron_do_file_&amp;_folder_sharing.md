---
title: "How does Hardy Heron do file &amp; folder sharing?"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by lands.wilmoth on 2008-10-14
I have 8.04 installed with all updates applied. My smb.conf file is virtually empty with only user homes and printers shared.

After I right-click a folder, select "Sharing Options", tick the "Share this folder" box, enter a name, and click "Create Share", the folder is indeed shared across my network. That is, I can see it from my Windows XP box. But when I examine the smb.conf file, there is no change. My folder is not listed.

So this begs the question: How does Ubuntu / Nautilus maintain folder sharing if it clearly does not use Samba?

Thanks in advance.

James

---

### Post by superprash2003 on 2008-10-14
thats wierd.. are you opening the smb.conf file at /etc/samba/smb.conf

---

### Post by Iowan on 2008-10-14
I remember seeing this before - but don't remember specifics. My Hardy Xubuntu box has a **/var/run/samba/smb.conf** file.

---

### Post by bab1 on 2008-10-14
> How does Ubuntu / Nautilus maintain folder sharing if it clearly does not use Samba?

It does use Samba.  The Samba configuration using the GUI is stored using the gvfs libs (virtual filesystem).  The configuration files are stored at:```
/var/lib/samba
```

The directory looks like this:```
bruce@malibu:~>ls -l /var/lib/samba
total 72K
-rw------- 1 root root 4.0K 2008-05-17 10:08 account_policy.tdb
-rw------- 1 root root 4.0K 2008-05-17 10:08 group_mapping.tdb
-rw------- 1 root root 4.0K 2008-05-17 10:08 ntdrivers.tdb
-rw------- 1 root root  696 2008-05-17 10:08 ntforms.tdb
-rw------- 1 root root 8.0K 2008-09-03 15:35 ntprinters.tdb
-rw------- 1 root root  12K 2008-05-17 10:08 passdb.tdb
drwxr-xr-x 2 root root 4.0K 2008-05-17 10:08 perfmon
drwxr-xr-x 4 root root 4.0K 2008-05-17 10:08 printers
-rw------- 1 root root  16K 2008-10-14 19:27 registry.tdb
-rw------- 1 root root 8.0K 2008-05-17 10:08 secrets.tdb
-rw------- 1 root root 4.0K 2008-05-17 11:08 share_info.tdb

```

---

### Post by lands.wilmoth on 2008-10-15
> **bab1 said:**
> It does use Samba.  The Samba configuration using the GUI is stored using the gvfs libs (virtual filesystem).  The configuration files are stored at:```
/var/lib/samba
```

The directory looks like this:```
bruce@malibu:~>ls -l /var/lib/samba
total 72K
-rw------- 1 root root 4.0K 2008-05-17 10:08 account_policy.tdb
-rw------- 1 root root 4.0K 2008-05-17 10:08 group_mapping.tdb
-rw------- 1 root root 4.0K 2008-05-17 10:08 ntdrivers.tdb
-rw------- 1 root root  696 2008-05-17 10:08 ntforms.tdb
-rw------- 1 root root 8.0K 2008-09-03 15:35 ntprinters.tdb
-rw------- 1 root root  12K 2008-05-17 10:08 passdb.tdb
drwxr-xr-x 2 root root 4.0K 2008-05-17 10:08 perfmon
drwxr-xr-x 4 root root 4.0K 2008-05-17 10:08 printers
-rw------- 1 root root  16K 2008-10-14 19:27 registry.tdb
-rw------- 1 root root 8.0K 2008-05-17 10:08 secrets.tdb
-rw------- 1 root root 4.0K 2008-05-17 11:08 share_info.tdb

```

Ahhhh...! My /var/lib/samba folder also contains a sub-folder by the name of usershares. And in that sub-folder are individual files that contain specifics regarding those phantom shares! Now I suppose I could ask *why* nautilus uses this method of sharing folders instead of the /etc/samba/smb.conf method... :)

And I thought we were all working towards a unified world! :) Got to admit it...  I just love Linux!

Thanks all for your help!

Lands

---

### Post by bab1 on 2008-10-15
> Now I suppose I could ask why nautilus uses this method of sharing folders instead of the /etc/samba/smb.conf method..

I believe **all** the GUI configuration is under /var/lib.  Samba is only one of many things the GUI configures.  The shared libraries of code were not built with Samba specifically in mind.  Look in the directory: ```
/var/lib
``` to see all that the GUI is responsible for.

> And I thought we were all working towards a unified world! I kinda disagree with this.  The whole *nix world has really never agreed on common ground.  It is its weakness and and strength.

---

### Post by jimav on 2009-10-09
OK, so can sombody explain *how* samba finds out about the shares defined in /var/lib/samba?    How exactly does this information get injected into smbd?

Thanks in advance...

---

### Post by Iowan on 2009-10-10
As I remember, those are the shares set up by Nautilus.

---

### Post by jimav on 2009-10-10
Nautulus can not, by itself, cause files to be shared.  Somehow it must tell Samba (smbd, presumably) to create the shares.   But how?

The smbd man page says smbd finds out about shares by reading
/etc/samba/smb.conf, but clearly there must be some other (undocumented) interface...

---

