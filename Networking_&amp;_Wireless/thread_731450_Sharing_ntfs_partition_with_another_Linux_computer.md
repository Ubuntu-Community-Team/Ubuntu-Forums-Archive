---
title: "Sharing ntfs partition with another Linux computer"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by aroth87 on 2008-03-21
I promise, I tried really hard to solve this on my own and read any thread I thought might be relevant, so posting this is my last resort.

My desktop is dual booting XP and Gutsy. All of my music is stored on the XP partition, which is NTFS. I also have a laptop that is Gutsy only. I would like to be able to share the music that is on the NTFS XP partition with my Gutsy laptop via my router.

I was able to get NFS working and share the contents of my home partition on my desktop with my laptop, but it seems that the NTFS filesystem isn't supported by NFS (no real surprise there once I thought about it) and I still can't access my music.

Is there anyway that is as quick and easy as NFS that will allow me to share the XP partition while still having both computers booted in Ubuntu? I should also mention that I have little to no experience with networks but am really good at doing what I'm told :).

Thanks,
Adam

---

### Post by Eiríkr on 2008-03-22
One thought is to try the [font=courier]sftp[/font] route.  Make sure the [font=courier]ssh[/font] package is installed on both Ubuntu machines.  Then open your file browser, go to the location bar (usually hidden by default in Nautilus, but displayable by either hitting Ctrl+L or clicking View -> Location Bar), and type in [font=courier]sftp://IP.ADD.RE.SS[/font]. replacing the caps with the IP address of the other machine.  You should then be prompted for a username and password for the destination machine, and then you're in.  I haven't been able to test this with any NTFS partitions, but at least in theory, it should work.  

HTH,

Eiríkr

---

### Post by drdos2006 on 2008-03-22
That sounds very complicated, to me.

Is the Ubuntu box able to share via NTFS partition/drive through Administration -> Shared Folders ? 
If so, then the desktop machine with the shared NTFS folder needs to have the laptop user  name added to desktop Users and Groups for the laptop to connect, doesn't it ?

regards

---

### Post by aroth87 on 2008-03-22
Thanks to you both of you. I have it working now. I don't think I had ssh installed on both of them last night but now using Nautilus I can connect to the desktop and browse all of the files.

Adam

---

### Post by Eiríkr on 2008-03-22
Glad something worked!  :D

Cheers,

Eiríkr

---

