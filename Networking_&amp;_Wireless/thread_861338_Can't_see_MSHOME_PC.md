---
title: "Can't see MSHOME PC"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by iainv on 2008-07-16
I'm trying to copy my files from my Vista laptop to my 7.10 desktop, so that I can eradicate Vista once and for all.

For reasons I won't bore you with i'm going to wait to upgrade to 8.04 on the desktop until after i've got the laptop stable.

I've connected the two PCs with a crossover cable, setup SAMBA and sharing and can see the desktop in vista, access my shared folders, and read and write to it.

The desktop can see "Windows Networks" but the folder is empty.
I presume the problem is at the laptop end (which is yet another bloody reason I want rid of Vista), but for the life of me I can't work it out.

I've turned the network onto "private" so that it's discoverable, set all the sharing options I can find to "on" and turned off all the password ones.

smbtree gives:
```
iain@iain-desktop:~$ smbtree 
Password:  
WORKGROUP 
        \\IAIN-PC         
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine IAIN-PC.  Error was NT_STATUS_ACCESS_DENIED 
MSHOME 
        \\IAIN-DESKTOP                  iain-desktop server (Samba, Ubuntu) 
                \\IAIN-DESKTOP\Unknown          HP Laserjet 
                \\IAIN-DESKTOP\PDFgenerator     PDFgenerator 
                \\IAIN-DESKTOP\print$           Printer Drivers 
                \\IAIN-DESKTOP\Ubuntu shared   
                \\IAIN-DESKTOP\IPC$             IPC Service (iain-desktop server (Samba, Ubuntu)) 
iain@iain-desktop:~$  
```

Anyone have any ideas?

Iain

---

### Post by Neobuntu on 2008-07-16
My idea is that it's faster to pop in a Flash drive, and move your stuff that way.

Don't blame "Linux". networking requires planetary alignment in order to work. It's usually overlooked firewall settings.

---

