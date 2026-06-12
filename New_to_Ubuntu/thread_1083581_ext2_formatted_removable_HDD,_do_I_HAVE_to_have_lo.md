---
title: "ext2 formatted removable HDD, do I HAVE to have lost+found?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by tnek on 2009-03-01
Hi, I bought a removable HDD which uses USB 2.0 to connect. It was formatted with FAT32 which I didn't want, I choose to reformat it using ext2 by: ```
sudo mkfs -t ext2 /dev/sdb1
```

The directory lost+found with privileges only for root was automatically created on the drive. I know it's used if I have a HDD problem and that in such a case (partial) files which are found during recovery will be placed there.

Still, it's annoying to have a directory in the root which isn't hidden and can't be used. What happens if I remove it?

---

### Post by bumanie on 2009-03-01
As far as I know it is quite safe to remove the lost& found directory. You have already stated the consequences of it not being there re if a major crash occurs there will be no-where for your anything recovered to go to.

---

### Post by Kellemora on 2009-03-01
Hi Tnek

This might help you, maybe?

We create a NEW FOLDER the place for EVERYTHING ELSE on each hard drive and only SHARE that particular folder.  That way no one but you sees the inner workings and can't mess with them.

Even our Data File Server, the only SHARED FOLDER is the one named File_Server and inside of that folder are all the hierarchical folders for EVERYTHING non-system related.

If I look at the Root directory, I see all the other folders no one else has any business getting into.  A mirror of our accounting data is in Root first, then in a password protected folder in the File_Server folder too.
Also Folders like Client Fonts and/or images, that are proprietary to that client, etc.  I only move them to the File_Server folder on an as needed basis.

If you're coming from Windows, you can think of Root as Drive C and your MAIN FOLDER as Drive D if that helps any.  And NO ONE except YOU has access to Drive C..........

TTUL
Gary

---

### Post by tnek on 2009-03-03
> **bumanie said:**
> As far as I know it is quite safe to remove the lost& found directory. You have already stated the consequences of it not being there re if a major crash occurs there will be no-where for your anything recovered to go to.

What I don't understand is why the tool can't just create this directory if a crash should occur? So the consequence of not having it is that I won't be able to recover any files? It won't create the directory or ask me if I want to create it?

> **Kellemora said:**
> Hi Tnek

This might help you, maybe?

We create a NEW FOLDER the place for EVERYTHING ELSE on each hard drive and only SHARE that particular folder.  That way no one but you sees the inner workings and can't mess with them.

Even our Data File Server, the only SHARED FOLDER is the one named File_Server and inside of that folder are all the hierarchical folders for EVERYTHING non-system related.

If I look at the Root directory, I see all the other folders no one else has any business getting into.  A mirror of our accounting data is in Root first, then in a password protected folder in the File_Server folder too.
Also Folders like Client Fonts and/or images, that are proprietary to that client, etc.  I only move them to the File_Server folder on an as needed basis.

If you're coming from Windows, you can think of Root as Drive C and your MAIN FOLDER as Drive D if that helps any.  And NO ONE except YOU has access to Drive C..........

TTUL
Gary

I'm the lone user of this device and I only use it for backups. It's not a big problem having a lost+found, as you say. I could just create a directory and pretend that is my root directory. I just find it ugly having to have a directory which is not even hidden, for the rare case that I need to recover a file.

---

