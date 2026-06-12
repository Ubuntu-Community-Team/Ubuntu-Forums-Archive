---
title: "SMB Networking is seriously failing"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by rbrown3 on 2008-04-17
Greetings:

   I have a pre- existing SMB- based network that I am trying to add an Ubuntu- based machine to. This network includes several machines, including some Vista, Macintosh, and some machines with other Linux distributions.

   The machines on this network are in the same "workgroup". These other machines can share files and folders with each other.

   The Ubuntu machine, however, is unable to even browse through the workgroup -- despite the fact that it is a member of that workgroup! When I attempt to browse to reach the list of the machines in the workgroup, I get the following (extremely useless) message:

The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Windows Network: workgroup".

Does anyone have a clue as to why this is happening? I have been looking through all the samba "documentation" and have found nothing.

---

### Post by dstew on 2008-04-17
Samba can have problems with share names, directory names and file names that have unusual characters in them, such as spaces. I once had a directory that would not display its contents using the smbclient commands. The problem was that one of the files in the directory had a trademark character in its file name. It threw off the whole directory listing.

---

### Post by Iowan on 2008-04-17
No guarantees, but try the "Connect to Server" option.

---

