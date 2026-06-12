---
title: "Inheriting Directory Permissions"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Napoleon Dynamite on 2008-09-20
I am struggling with setting permissions on a file server. 

I have a Hardy Heron File Server with a shared directory. I have eight windows users who all have acces to the shared directory.
The shared directory belongs to a group that all the users belong to (staff) and has been given 777 permissions.
There are five sub-directories each of which are owned by a user and belong to the same group (ie user1 user1).
I have then added some other users to the group so they also have access (ie I added manager, office-manager to the group user1). These directories have 770 permissions.

My problem is that if one of the other users (ie manager) places a file in one of these directories the owner and group of the new file is manager manager.

How do I get the directories/files to inherit permissions from the parent directory?

BTW I have been running tests with setgid but it does not quite do what I want.
Also I am very new to this so I may need to ask some very rudimentary questions before I get it :)

---

