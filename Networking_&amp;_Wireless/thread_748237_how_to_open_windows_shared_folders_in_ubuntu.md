---
title: "how to open windows shared folders in ubuntu"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by lodhi on 2008-04-07
hi.....
i want to open windows files in ubuntu .i have installed samba but dont further,...
 if anyone please help me out......

---

### Post by Eiríkr on 2008-04-07
If the files are on a Windows machine, you don't need to install the **samba** package -- that's only needed when the files are on an Ubuntu machine and you need to access them from a Windows machine.  

If the files are indeed on a Windows machine and you have already configured the Windows folder for sharing, go to your Ubuntu machine, open your Nautilus file browser, click on the location bar (hit Ctrl+L or click View -> Location Bar to display it if it's hidden), and type:
```
smb://IP.ADD.RE.SS
```
Replace the caps with the IP address of the Windows machine.

Cheers,

Eiríkr

---

