---
title: "Problem with permissions gutsy client/gutsy server"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by OiPenguin on 2007-11-06
I've set up a server with a share /home/felles For this share I've set 777 felles:felles Permissions and owner:group are confirmed with 'sudo mc'.

I've added two users to the group 'felles' and terminal ssh to the server works as expected. I've managed to connect the client and the server via places --> connect to server --> SSH. I can view documents on server, however I'm unable to edit documents on the server. When I right click and view permissions for folders and files in Nautilus it says read/write for owner/group/others, however owner:group is unknown:unknown, rather than felles:felles.

What have I done wrong? How do I investigate/solve this problem?

Sidenote: I've tried to access documents on server with Bluefish. The mounted shares showes, however I can't open it. When I choose '/home/felles' nothing happens, nor do I get an errormessage.

---

