---
title: "Windows Share; Major Problem"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by GJS on 2008-01-18
A few days ago, my Ubuntu 7.1 machine become unable to browse shared folders on Windows XP and 2000 machines on my LAN.  I do not know of anything I have done to stop it working.  Searching through threads on this forum there are a few poeple with the same problem but no definitive fix that works for me.

The error when I try to browse the network (double click on the workgroup name) is:

The Folder Contents Could Not Be Displayed
Sorry, couldn't display all the contents of "Windows Network: [workgroup_name]".

Diggging a bit deeper, using smb4k, the returned error message is:  
Could not connect to server IS~HOME-AUTO
Conection failed: NT_STATUS_DUPLICATE_NAME 

HOME-AUTO is the name of the W2k machine, I don't know where the IS~ bit has come from.

The network printer, shared from the w2k machine that it is directly connected to still works fine from the Ubuntu machine.

If I can't find the problem soon I'm going to have to re-install Ubuntu so I'd be very grateful for any help.

Thanks.

---

### Post by GJS on 2008-01-18
In case it helps anyone else, I changed the Windows Workgroup name on all the machines and now it's working.  Seems like this is a bug.

---

