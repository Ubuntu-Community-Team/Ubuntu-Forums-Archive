---
title: "How to Connect Shared Windows Drives from ubuntu?"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by tam3105 on 2011-07-30
Hi,

Initially I used Gnome in ubuntu 10.10 and can access the Shared Windows Drives using the menu option given below,

Places --> Connect To Server 

(Windows server IP, Shared Drive Name, user name, password details needed to access the windows server)

Recently I have installed LXDE in ubuntu 10.10 to improve the performance. But I could not find the option to connect the Windows Shared Drive as like in GNOME.

Could anyone help me to connect windows server?

Thanks in Advance..

---

### Post by lmarmisa on 2011-07-30
I suppose that you are using the SMB/CIFS protocol for connecting to the shared folders of the Windows servers.

If so, open the File Manager and type **smb://** (see the attached image). If the servers are located on your LAN, you will be able to see the workgropus, file servers and shared folders of your network.

If the server is not located on your LAN, you will have to type the reference to the folder you want to access. These are two examples:

```

smb://remoteserver/sharedresource
smb://192.168.1.122/TEMP

```

A last comment: you can add to bookmarks the shared folder that you are seeing. Simply select **Bookmarks -> Add To Bookmarks**.

---

### Post by tam3105 on 2011-08-01
Hi [lmarmisa]("http://ubuntuforums.org/member.php?u=955260"),

It worked for me. Thanks a lot for quick reply and solution.

---

### Post by lmarmisa on 2011-08-01
> **tam3105 said:**
> Hi [lmarmisa]("http://ubuntuforums.org/member.php?u=955260"),

It worked for me. Thanks a lot for quick reply and solution.

Great!!!. :D

Please, mark the thread as SOLVED (look at Threard Tools -> Mark as solved).

Best regards,

Luis

---

