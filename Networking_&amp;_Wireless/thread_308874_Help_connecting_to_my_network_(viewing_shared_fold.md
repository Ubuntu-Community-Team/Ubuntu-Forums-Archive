---
title: "Help connecting to my network (viewing shared folders and printing)"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by mpfeif101 on 2006-11-28
Hi there,

There are 4 computers in my house and all are wired.  The rest of the computers are Windows XP and I am trying to connect this Ubuntu Edgy machine to the windows network so I can share folders and print to the network printer.  I looked through the samba docs but just can't get it to work.  Here is my very simple samba conf file:

```
[global]
workgroup = @HOME
netbios name = mattcomp
```

So I go into places->network servers.  I go into Windows Network.  I then double click to go into the @home folder (the name of the workgroup).  It says:
[b]Couldn't display "smb:///%40home"
The location is not a folder.[/b]

After I hit cancel, however, it changes icons, and i double click it again and it lets me in.  I can now see all the computers in my workgroup (yay).  However, when i double click on any it says:
[b]Cannot open FAMILYROOM
The filename "FAMILYROOM" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system[/b]

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

Trying to double click again does the same thing.  Any ideas?

---

### Post by Iowan on 2006-11-28
> When defining groups in the SAMBA configuration file, /etc/samba/smb.conf the recognized syntax is to preface the group name with an "@" symbol. For example, if you wished to define a group named sysadmin in a certain section of the /etc/samba/smb.conf, you would do so by entering the group name as @sysadmin. 

Your workgroup name may be confusing Samba - which thinks @HOME is a group.

---

### Post by mpfeif101 on 2006-11-28
Thank you so much for your help Iowan!  I can now get inside the other computers in my work group (I changed the name of the workgroup from @HOME to PFEIFHOME).  :) 

There's now one more little problem which isn't a big deal, just kinda annoying.  When I first Double click PFEIFHOME or any of the computers in my network it does not recognize them as folders, I have to keep clicking until eventually it recognizes them as folders and lets me in.  Any clues on how to just have it work as a folder right away?

Now on to my next problem.  Printing.  On one of the other computers a printer is installed and shared over the network.  How can I access it?  I went to the add printer wizard and selected Windows Printer (smb).  In the host field is **smb**, the printer field is **/PFEIFHOME/MOMCOMP/hppsc130**, and the username and password fields are blank.  Yet when I try to print something, it never prints (just continues to say "Printing").  Any ideas?

Thanks again for your help, you guys are awesome.

 - Matt

---

