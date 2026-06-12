---
title: "SMB/SAMBA question"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by jobsonandrew on 2008-02-27
I was wondering....
Imagine if you had a file on an SMB (or Samba) server:
\\server\share\fileA
and you used a client machine to move that file to:
\\server\share\folderA\fileA

My question is.. which machine does the work of moving the file? Does the file go from server, to client, so server... or does the server know that the source and destination are both on the server and therefore do the work itself?

Thanks

---

### Post by Iowan on 2008-02-27
Just my opinion/guess...
Because the copy instruction is issued to the client, the server only serves up the file.  The client can do with it whatever it desires - even write it back to the server.

---

### Post by dca on 2008-02-27
No, it stays on that server unless you purposely copy fileA to the client.  That's the same if you shelled in to the system and executed the 'cp' command.

---

### Post by Iowan on 2008-02-27
I'm 0/1... So much for my version of logic - thanks for "better" answer.

---

### Post by jobsonandrew on 2008-02-29
cool, I thought it must be that way!

---

