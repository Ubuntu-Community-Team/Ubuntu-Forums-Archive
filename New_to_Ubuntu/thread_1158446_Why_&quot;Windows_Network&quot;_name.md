---
title: "Why &quot;Windows Network&quot; name?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by robnoyes on 2009-05-13
Ok...I'll cast the first vote for dumbest newbie question ever on my own post...but here goes...

When I click Places/Network, a window pops with an icon reading 'Windows Network.' Why?

Is it because I originally started the network from an MSWindows machine? Is because my wife's machine (Vista) is on and it somehow took ownership of the network? It still appears when hers is off...? Is it because the router was possibly named 'Windows Network?'

Since her machine is basically for her internet surfing never doing any filesharing or retrieving within the network, can I change the network from 'Windows Network' to something else? If so, where?

Will changing any of this make it easier for my Vaio laptop to access the Dell desktop I'm using as a server?

Hope to hear from you soon.

Thanks, RN

---

### Post by MontelEdwards on 2009-05-13
It's because when you click the Network icon, i believe Samba searches for Windows networks. That does not mean she took "ownership" of the network, it is just that she is ON the network, and it is the goodness of Ubuntu that recognizes it on the network. The reason is so that you are your wife or whatever can share files between your computers. There is no way of changing the Windows Network thing i think, it just lets you separate the Windows Network from the other Ubuntu computers or Linux computers. You can change the Windows Workgroup name, but that is done on Windows, and i cant help you there

---

### Post by Iowan on 2009-05-13
It almost seems like a concession that there will probably be a Windows network attached.  
The Dell desktop... another Ubuntu box? How do you plan to share files - FTP, SSH, NFS, Samba?

---

### Post by CatKiller on 2009-05-14
It's there even if you aren't connected to a Windows network. It's just a shortcut to get Samba to look for Windows shares.

---

