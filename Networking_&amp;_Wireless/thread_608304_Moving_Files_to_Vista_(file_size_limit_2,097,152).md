---
title: "Moving Files to Vista (file size limit 2,097,152???)"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Mithrilhall on 2007-11-09
I'm trying to move some files over to a computer running Vista (don't ask). The files  I'm moving are images of DVDs and they seem to die at 2,097,152KB (2GB).  :confused:

The Konqueror error I get is

> 
The process for the file protocol died unexpectedly."


---

### Post by HermanAB on 2007-11-10
Many FTP servers and clients have a 2GB bug.  The Microsoft SMB protocol also used to have a 2GB bug.

So, split the file in sub 2GB pieces, and concatenate them at the other side.  On Linux, there is a utility called split.  On Windoze, you can copy them together using copy /b.

Cheers,

Herman

---

### Post by kevdog on 2007-11-10
Herman, can you tell me where you exactly found this info regarding the 2gb bug in samba.  I ran into this problem a long time ago when trying to use unison to synchronize my machines.  File transfers would consistently get stuck around 2gb (I guess now I know why).  If I use the ssh protocol rather than smb, to copy files between windows and ubuntu, is there this limitation??

---

### Post by Mithrilhall on 2007-11-10
From what I've read elsewhere, it's Konqueror and/or Samba not being configured with large file support. If that is the case, I'm extremely disappointed. With the size of hard drives today, high definition video files and other large files; large file support should be mandatory.

---

### Post by HermanAB on 2007-11-10
The 2GB bug was fixed in Samba around 2002.  Some FTP servers still have this bug, for example Filezilla.  Microsoft may still have it in some versions of Windows, since they are not very good at fixing things.  I don't think that rsync has this problem and I have never used unison, so I can't comment on that one.

Cheers,

Herman

---

