---
title: "Strange issue: I can only see XP  partition if XP is runnung"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Piero00100 on 2007-08-13
Hi everybody,

I have a network with 2 pc's. One with ubuntu/xp and the other one with kubuntu/xp. I've installed samba and I can share my files/directories between ubuntu's partitions. 

I can see locally my NTFS partition but if, for example, I want to see a shared XP's directory on the other computer, I can't connect. It says that the directory doesn't exist. I have to turn on XP and then I can share it.

Anyone can help?

Thanks in advance.

Piero

---

### Post by noob12 on 2007-08-13
Two suggestions for things to check:

Make sure you've shared the folders in Ubuntu: System | Administration | Shared Folders.

Select a consistent workgroup name on both hosts in the System | Administration | Shared Folders | General Properties tab.

---

### Post by Jeckler on 2007-08-13
I'm a complete newb at this, but it sounds to me like you need to configure Samba to read and share your NTFS partition on the other machine so that it's accessible while in ubuntu/kuuntu. Not that I have any idea how, but does that sound about right?

---

