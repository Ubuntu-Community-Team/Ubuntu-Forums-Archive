---
title: "Using the &quot;Connect to Server&quot; GUI to access Windows shares"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by weedwacker on 2009-02-20
Hi, all!

I just want to learn how to do this. I am using Ubuntu Ibex.

I have Samba installed and can access my Windows shares using the **Places>Network** access just fine. I am accessing from both machines networked through my Linksys router on my home network.
My machine is Ubuntu and the other is Windows XP.

But I want to learn how to access my windows shares using the **Places>Connect To Server** GUI.

I found out how to FTP (using **Places>Connect To Server**)to a location that requires a password after trial and error and I am happy with my new knowledge.

To connect to my Windows share in the **Connect To Server** GUI I click on **Windows share** but I am having difficulty with the information to enter into the **Server** box.

I've tried the IP address of the machine I want to access, I've tried using **mshome** alone and in conjunction with the IP address, and also with the name of the computer I want to access: **salsnotebook**. I have tried finding this information on the net to no avail.

This is the message that pops up often:

[INDENT]Cannot display location "smb://mshome/salsnotebook/documents"

failed to mount windows share
[/INDENT]
Could someone help? :?:

---

### Post by jimmy the saint on 2009-02-20
To the best of my knowledge windows xp does not come with an ftp server for you to connect to.  If I'm right (and if I'm not someone will correct me) you will need to look into an ftp server for windows.

---

### Post by weedwacker on 2009-02-20
Thanks for the response.

However, I don't want to FTP into my Windows share.

I just want to access the Windows share that is currently accessed with Samba.

I guess I assumed that accessing from the **Connect To Server** GUI that this was using Samba also.  Not FTP.

Would my assumption be correct?

---

### Post by rustutzman on 2009-02-20
I've used it to connect to the default admin share of the drive in WinXP by putting in C$ or D$ for the folder. Nothing for the domain and using the IP of the Windows box. Username and password are for the admin credentials under Windows. Leave the rest of the boxes empty.

Russ

---

### Post by Kellemora on 2009-02-20
Hi WW

In the File Server BOX goes the phrase ```
samba, ubuntu
```

Then you will have to add your own data in the other boxes.

TTUL
Gary

---

