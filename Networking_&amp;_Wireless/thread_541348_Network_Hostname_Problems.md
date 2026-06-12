---
title: "Network Hostname Problems"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by fatsheep on 2007-09-02
I just set up a samba network with [this helpful topic](http://ubuntuforums.org/showthread.php?t=202605) between this Ubuntu 7.04 machine and a Windows 2000 machine.  However, it has problems:

1.  **Domain names are not working.**  I have disabled Zone Alarm on Windows but neither domain name can be pinged from either machine.  I cannot even ping this machine when I am on it unless I use *fatsheep-desktop.WORKGROUP* as the hostname (the hostname is fatsheep-desktop).  However pinging the other computer as *dell2000.WORKGROUP* doesn't work.

2.  **Network printer** (setup on the Windows 2000 machine) **won't work from this machine** (Ubuntu).  I have set it up with System > Administration > Printing.  I have tried using "DELL2000" as the hostname and I have tried using the IP address of the Windows 2000 machine, neither have worked.  In the properties of the printer on Ubuntu, this error message is displayed: 

> Ready: Unable to connect to CIFS host, will retry in 60 seconds...

Here is the output of smbtree:

```
smfatsheep:~$ smbtree
Password: 
WORKGROUP
        \\DELL2000       
                \\DELL2000\C$                   Default share
                \\DELL2000\ADMIN$               Remote Admin
                \\DELL2000\moo                  hp deskjet 845c series
                \\DELL2000\print$               Printer Drivers
                \\DELL2000\IPC$                 Remote IPC
        \\ALEX-DESKTOP   
timeout connecting to 192.168.0.5:445
timeout connecting to 192.168.0.5:139
Error connecting to 192.168.0.5 (Operation already in progress)
cli_start_connection: failed to connect to ALEX-DESKTOP<20> (192.168.0.5)

```




Any help on either problem would be most helpful.  Thanks,

- sheep

---

### Post by fatsheep on 2007-09-04
Any ideas?

---

