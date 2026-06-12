---
title: "SAMBA problem with SSHFS folder"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by deep-z on 2008-01-03
Hi there!

I have some remote folder on my local machine mounted as local through sshfs

Example:
```
sshfs remoteuser@remotemachine.com:/somefolder /mnt/local/remotemachinefolder
```

And I share this "/mnt/local/remotemachinefolder" on my local machine as Samba share "remotemachinefolder".

At this point I can see my new share with typing:
```
smbclient -L //mylocalmachine
```
in the sharelist.

But when I'm trying to access this share I get:
```
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```
and permissions error in my Samba logfiles.

Permissions seem to be okay, so the question is - is it supported by Samba to share SSHFS mounted filesystems.

Any ideas and suggestions would be great! Thank you all in advance...

---

### Post by jetsam on 2008-01-04
I think it is supported.

I've never done it, but the person on this blog has a clever set up where he uses a linux vm running sshfs and samba on a windows pc to make his remote shares available to the windows pc:
[http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/]("http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/")

Your situation isn't exactly the same, but it's a pretty detailed tutorial and may have the solution to your problem...  There's a part about half way through the page that begins "Now, here's the part that wasn't in most of the tutorials, but necessary to make Samba work later on..." that looks promising.

---

