---
title: "DFS shares"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by shoofy on 2006-08-11
I managed to get Ubuntu to mount a Windows Server 2003 R2 Distributed File System share and also to access it with smb:// in Nautilus, but both ways give me the same problem. For every folder in the DFS, when I open it it just contains the same contents as the root of the DFS share. You have to go three levels in before getting to the files you want. For example, what in Windows would be displayed at \\server\DFS\folder is displayed in Ubuntu at \\server\DFS\folder\folder\folder and Ubuntu's \\server\DFS\folder shows the same as Windows' \\server\DFS. When I try to create a file, it only allows it to be created in this third level directory. If I create it anywhere higher up, it creates it as a directory and it just shows up as a corrupt file on Windows.

Is this just an incompatibility with DFS and Linux? Is there anything I can do on the Windows or Linux sides to make this work better?

---

### Post by shoofy on 2006-08-11
I solved it myself. I installed File Services for Macintosh from Add/Remove Windows Components on the DFS servers and everything seems to be working fine now.

---

### Post by andrewmyth on 2008-02-06
You can think of a DFS root as a centralized virtual file share structure. It is a hierarchy of shares across your network that is collectively brought together for easy access and administration. Each share in your DFS root that represents a share located somewhere on your network is referred to as a link. Much like a website contains links to other pages, a DFS root contains links to shared folders across your network. These shares do not even need to be Windows shares; they can be UNIX or Netware volumes, too! If your network is a hybrid of different operating systems, DFS can be a great tool to implement.
for more detail [read full article]("http://www.informit.com/articles/article.aspx?p=345783")

---

