---
title: "Samba lost my network"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by Kralizec on 2008-08-22
The problem is this: recently (possibly after a samba update, though I'm not sure), I lost the capability to view my networked Windows machine and its shared printer using samba. I can still ping the computer, can connect to it as a windows share server using Places -> Connect to Server, but I cannot browse it using nautilus and cannot connect to the printer, which is the real problem. The strange thing about all of this is that it just recently occurred after working fine for months. I have tried purging and reinstalling Samba and all of its pieces to no avail. I've experienced this problem once before, and only resolved the issue after a fresh install; I would like to avoid this solution, if possible. Please assist!

---

### Post by Kralizec on 2008-08-31
Bump. This problem is really very annoying.

---

### Post by cariboo on 2008-08-31
First you don't need samba to connect to a windows computer, that is handled by smbclient. Can you manually mount one of your shares using smbfs, to do this in a terminal:

```
sudo mount //windows_computer/windows_share /media/windows_share

```
One final thing are you sure the changes didn't happen on your windows computer.

Jim

---

### Post by bab1 on 2008-08-31
I believe that the OP was asking how to *[COLOR="Green"]browse[/COLOR]* shares rather than [COLOR="Blue"]mount[/COLOR] a smb share.  The Samba client for browsing is [COLOR="Green"]"smbfs"[/COLOR]  See:

[http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs]("http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs")

---

### Post by Kralizec on 2008-08-31
Thank you for the response. I am able to mount windows shares using the 'mount' command and smbfs. My problem lies in connecting to a shared windows printer without being able to view my Windows file shares in nautilus or the print shares in the cups manager.

---

### Post by bab1 on 2008-08-31
What do you mean by: > I am able to mount windows shares using the 'mount' command and smbfs. If you are using smbfs you should be able to "see" the Windows file shares via the browse mechanism.  If you are indeed mounting the SMB file share, that is something else.

---

### Post by Kralizec on 2008-08-31
By using the command cariboo posted earlier, I can access the shared folders. However, I cannot browse them by going to Places -> Network; they have to be manually mounted. Again, I must stress that my main concern is using the shared printer, not so much viewing the file shares.

---

