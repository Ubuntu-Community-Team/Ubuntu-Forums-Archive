---
title: "How do i network linux only computers?"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by glenn69 on 2007-02-25
I have 2 ubuntu computers that I would like to connect by a network.  I would also like to share the printer on the desktop computer.

How do I do this?

I've searched, but everybody seems to respond to these type of question as though everybody already knows network terms.  I don't.

I've seen answers about Samba, but isn't that mainly to connect a Windows computer with a linux?

Thanks for any help available

---

### Post by simonn on 2007-02-25
You need to be a bit more precise about "would like to connect by a network."

Do you want to share files? Is ftp or ssh enough or do you want to share a whole directory tree? Is it only one way? Maybe an http server might be the better option? Are you trying to share an internet connection? Do you require remote access? etc etc

> everybody seems to respond to these type of question as though everybody already knows network terms. I don't.

Perhaps you should learn? Would you sit in a car and expect it to just drive?

> I've seen answers about Samba, but isn't that mainly to connect a Windows computer with a linux?

No. The smb/cifs protocol (MS's file sharing protocol) is a file sharing protocol. Any computer that has software to enable it connect to an smb server on another computer can use it. For instance, I do not have a windows PC at home (however I do have a couple of virtual machines) but I use samba to share home directories on my linux box so that they can be connected to from my iBook.

---

### Post by gradedcheese on 2007-02-25
In System->Applications->Shared Folders, you can make NFS shares.  This is the normal Linux way to share files.  You have other options too, like enabling an SFTP server.  To do that, install openssh:

```

sudo apt-get install openssh-server

```

(or use Synaptic to install it) and then browse "Network Servers" from the Places menu from another Ubuntu PC to see the SFTP service(s)

---

### Post by Jose Catre-Vandis on 2007-02-25
As others have said, the default sharing protocol for linux is NFS. This is simple to set up and rock solid in use. You can also access these shares from windows machines if you install the nfs services (XP is a download, Vista Ultimate its in features). There is an excellent howto on the forum, here: [http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889), that should get you going. ftp and ssh are also useful ways of accessing files on remote machines.

To share your printer among linux boxes you can use cups, but to share with windows you will need samba. [https://wiki.ubuntu.com/PrinterSharing](https://wiki.ubuntu.com/PrinterSharing).

simonn must be cross because England kept winning the one day cricket matches!

---

### Post by simonn on 2007-02-25
One gotcha with NFS, which is why I went samba, is that it uses numeric uids and gids rather than user and group names for permissions. This can be very annoying if you have mismatches. 

What this means is that in unix user and group names are just there to make things easier. It is the numeric value that these map to which is the important thing.

For example:

```

$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
....

```

The third field is the uid i.e. root maps to a uid of 0 and daemon to 1 etc. On your two ubuntu boxes you may have a user called user1, but user1 may have different uid values on each box.

Still, NFS is possibly easier to set up. Samba can be annoying!

> **Jose Catre-Vandis said:**
> simonn must be cross because England kept winning the one day cricket matches!

But I am an Australian/English dual national... (who does not care much about cricket anyway, although I do support Oz vss the UK). I am happer about having a higher GDP/captia, good weather, nice beaches, cheaper most things (in real terms), less of a police state etc etc... :).

Sorry if I came across as "cross" in my post. This was not my intention. My intention was more to educate.

---

### Post by Lux9698 on 2007-02-27
Thanks,
 that's are some helpful thoughts.

:)

---

