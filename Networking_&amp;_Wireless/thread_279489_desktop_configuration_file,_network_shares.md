---
title: "desktop configuration file, network shares"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-10-18
okay ... this has been bugging me to no end.

in ubuntu, you can go to: places > network servers and browse the network domain.  you can see computers connected to your network.  when you try to browse the shares on a particular computer (linux or windows), i get this message:
> The filename "IPC10512" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

how to i rename the file to the correct extension?

all the howto's i've read suggest mounting the samba share.  i don't want to mount it manually because i only have to browse to this share once every month or two.  this means that every time i want to mount this folder, i have to go looking for how to structure the command so i can make it work.

if i right click on the folder and select properties, the location shows as:
```
smb://i%26f
```

which makes me realize what my problem is.  this network has been named (by someone in all their wisdom) "i&f", which doesn't register correctly because of the "&" symbol.

so my question is ... how do i "rename the file to the correct extension for 'x-directory/smb-share' ..." where 'x-directory' is i&f rather than i%26f?

---

