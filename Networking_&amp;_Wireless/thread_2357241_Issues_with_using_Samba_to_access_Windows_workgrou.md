---
title: "Issues with using Samba to access Windows workgroup -Password issue"
date: 2017-03-31
forum: Networking &amp; Wireless
---

### Post by suliman2 on 2017-03-31
Hey all, I have been trying to resolve this issue all day, and I cannot find a fix, hopefully you guys can help me out!

I am trying to use a Windows 7 desktop (Allen-Desktop, 192.168.2.2) with an external drive to share a massive amount of horded media. 
I have set up a workgroup, which works perfectly on my other windows devices. I have configured settings to not prompt for passwords, allow R/W access, etc.

However, on my Ubuntu machine (Allen-Laptop, 192.168.2.3), which I intend to use to play said media, I cannot seem to connect to the windows shared folders/drives (I have tried multiple  devices and folders).

I have spent the last several hours browsing around looking for answers. This is what I have found:


[LIST=1]
[*]Windows can access my Ubuntu shares without issue 
[*]I can see all of the shares on my network through *smbtree -N* 
[*]I can ping the target machine (Which means firewalls are not an issue... right?) 
[*]**I can see the machines with shares though nautilus, but trying to connect prompts a password, which does not exist**
[LIST]
[*]If I connect through the 'Connect to Server' option, I get *Unhandled error message: Failed to mount Windows share: Invalid argument* 
[*]I cannot get smb:// to work. Perhaps my syntax is wrong, but I've tried smb://WORKGROUP/192.168.2.2, smb://WORKGROUP/192.168.2.2, smb://192.168.2.2, and all of the previous with shares appended. 
[*]Trying various password/user combinations with all sorts of syntax has failed to produce results 
[/LIST]
      
[/LIST]

Here is the output of *smbtree -N*
```
smbtree -N
WORKGROUP
    \\ALLEN-LAPTOP           Allen-laptop server (Samba, Ubuntu)
        \\ALLEN-LAPTOP\Shared Files       
        \\ALLEN-LAPTOP\IPC$               IPC Service (Allen-laptop server (Samba, Ubuntu))
        \\ALLEN-LAPTOP\print$             Printer Drivers
    \\ALLEN-DESKTOP          
        \\ALLEN-DESKTOP\Users              
        \\ALLEN-DESKTOP\test               
        \\ALLEN-DESKTOP\Seagate 4TB        
        \\ALLEN-DESKTOP\IPC$               Remote IPC
        \\ALLEN-DESKTOP\E$                 Default share
        \\ALLEN-DESKTOP\C$                 Default share
        \\ALLEN-DESKTOP\ADMIN$             Remote Admin
```

My smb.conf is stock, with workgroup=WORKGROUP being correct, as this is the name and case of my workgroup. 

Something seems odd here. Most of the similar problems I have dug up have been due to poor windows settings, bad firewall configurations, or have to do with accessing Ubuntu shares from windows.  

Any help is greatly appreciated. I'm more than happy to show other outputs and such. I have been at a loss for 5 hours now. 

Thanks!

---

