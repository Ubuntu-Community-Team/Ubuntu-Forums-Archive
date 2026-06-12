---
title: "Active FTP in Nautilus?"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by MonkeyBoy on 2007-04-25
It's been asked before in the distant past I know but I can't find any answers.

My ISP requires me to use active rather than pasv mode to connect to my webspace there.  I have connected via fireftp with no probs but I wondered whether anyone knows how to use active mode when connecting with Nautilus?

---

### Post by psusi on 2007-04-25
I think you got that backwards... normally active mode is used... you must need to use passive mode, for which there is no option in nautilus.

---

### Post by MonkeyBoy on 2007-04-26
OK thanks.

I will have to stick with fireftp 'til Nautilus gets that option.

---

### Post by BluewookieJim on 2007-06-24
I'm pretty sure passive mode is being used by default.

I just converted to ubuntu recently, and I was trying to get some files of my XP based server. I could not connect through nautilus or gftp initially. I installed Filezilla, and set it to active and it connected right away.

The interface in the port of Filezilla is awful, so I kept looking for a solution. Today I found it. In gFtp, under FTP --> OPTIONS, there is a tab for FTP. On that tab I de-selected the "Passive file transfers" box at the bottom, applied it, and was able to connect normally.

---

### Post by Spartakan on 2007-07-24
I'm pretty sure it's passive by default too. I look after one site that needs active FTP, and that's the one I can't connect to using Nautilus.

It'd be nice if Nautilus allowed editing of network options once a Place had been set up

Back to gFTP for me, for that site at least.

---

### Post by fjpos on 2008-06-18
> **Spartakan said:**
> I'm pretty sure it's passive by default too. I look after one site that needs active FTP, and that's the one I can't connect to using Nautilus.

It'd be nice if Nautilus allowed editing of network options once a Place had been set up

Back to gFTP for me, for that site at least.

Hi basically for me fireftp does not negotiate active ftp properly when you deselect the  passive ftp optionwhereas filezilla does

---

### Post by netwiz101 on 2008-07-02
*bump*

I would like to spark some interest in this significant deficiency in the built in FTP capabilities of Ubuntu (and I guess anything else using Nautilus).

It is very common for passive FTP connections to fail, and they are also insecure by their very nature.

An active FTP option is welcomed. This is one of only 3 or 4 glitches that causes me to periodically switch back to windows. I would much rather work in the integrated Nautilus environment, if I could properly mount FTP locations.

---

