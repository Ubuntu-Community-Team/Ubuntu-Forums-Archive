---
title: "Problem with network folder access using SSH"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by 50words on 2008-09-30
I am having trouble getting my network to work properly, and could use some help.

I have two computers in my office. One is a file server/workstation, the other just a workstation.

On the server, I have all business files in an unprivileged 'dummy' user. All files in the directory are set to 660 for one of two users, 'admin' and 'everyone' set to 1110 and 1111 (not the real numbers, but you get the idea).

On the server/workstation, I also have my own user account. Not an admin, but with all other permissions. I am a member of 'admin' and 'everyone' and can access all the files in the business files directory, create folders, modify them, etc.

On the workstation, I have the same user set up for myself with the same user ID number, and as a member of the same groups, 1110 and 1111. However, when I use SSH to access the server from the workstation, I can access the directories and files, but they all have the X emblem, and I cannot modify them, delete them, or create new files or folders. Keep in mind, everything is chmodded to 660.

---

