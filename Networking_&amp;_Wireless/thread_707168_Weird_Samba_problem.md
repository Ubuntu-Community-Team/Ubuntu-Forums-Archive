---
title: "Weird Samba problem"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by johan_nl on 2008-02-25
Hello everyone,

I have Edubuntu 7.10 with LTSP running on a "server". A directory on the 
server is shared so everyone can put documents in there and edit them.
However, when user A edits an existing document, and user B opens it
he doesn't see the changes user A made, and vica versa ofcourse. Also,
if user A deletes a document in of the folders under the shared folder,
user B still sees the document there! When I browse to the actual folder
(via Nautilus for example, or Midnight Commander) the file is still there.

I have never had this problem with Samba before. Does anyone have a 
clue?

---

### Post by ewanchic on 2008-02-25
That's really strange. I would assume each smbuser is saving a file into each of their home directories.

2 cents

---

### Post by jonallport on 2008-02-25
I assume they are Windows clients.  Are 'offline files' enabled on the clients.  This sounds like the same problem as you used to get in Netware when client-side caching was enabled:
Everyone gets a cached copy of the file so if A deletes it, B just replaces it with his/her copy - v.annoying!

A look at your /etc/samba/smb.conf would be handy too

---

### Post by johan_nl on 2008-02-26
I found out what the problem was. I browsed the server and I dragged the share icon onto the desktop, selecting Copy. That seemed to have create a sort of offline-folder for each user I dragged the icon onto the desktop, so every user did have his own "network" folder.

To resolve this issue I browsed the server, right-clicked the share then selected Connect to this server and an icon was created automatically on the desktop. And that icon *does* work!

---

### Post by Iowan on 2008-02-27
Good news!  If you believe the problem is solved, mark the thread [SOLVED] (under Thread Tools).  :)

---

### Post by ewanchic on 2008-02-27
> **Iowan said:**
> Good news!  If you believe the problem is solved, mark the thread [SOLVED] (under Thread Tools).  :)

You know I was going to say that too, but I wasn't sure if I should say that in this thread, or in a private message. Thanks for demo-ing that for me. :)

---

