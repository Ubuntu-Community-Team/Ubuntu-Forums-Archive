---
title: "uploading in a network??"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2008-11-16
can any one out there tell me if there is a way to upload files and directory's to a remote computer using a terminal i have a network of computers at my office and i am always using SSH SFTP SCP do get things from the other boxes but i am more and more finding need to send files and directory's to remote boxes and would that reaffic also be done on port 22.


thanks for your help and i f**king love linux 2 years strong and still working hard in the shell.

---

### Post by Iowan on 2008-11-16
> **Red-Shield said:**
>  i am always using SSH SFTP SCP do get things from the other boxes but i am more and more finding need to send files and directory's to remote boxes and would that [COLOR="Red"]reaffic[/COLOR] also be done on port 22. That li'l typo(?) is a bit confusing (traffic?), but if I read the **man** page for **scp** correctly, you should be able to do what you want>  Copies between two remote hosts are permitted.

---

### Post by Red-Shield on 2008-11-16
but i thought i could copy from him and him from me i want to send to him in a terminal outside the network

---

### Post by Red-Shield on 2008-11-20
i think you cant do recursive in i cant send directories using sftp are there any other programs that i can use the recursive option

---

### Post by jonobr on 2008-11-20
hello

try investigating rsync, its useful for file transfers and passing files to and fro, and even fro and to.

How a google around see what you find, if it sounds like something of interest, lots of peeps here can help if you need setup assistnace

---

