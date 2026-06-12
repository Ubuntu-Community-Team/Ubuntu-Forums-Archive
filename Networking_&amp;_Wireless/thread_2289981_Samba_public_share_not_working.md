---
title: "Samba public share not working"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by villermen on 2015-08-08
After following a lot of guides and tweaking everything for hours on end I decided to ask your help. I'm trying to get the simplest samba public share to work, but it is just not visible to other computers on the network. I've installed samba and edited /etc/samba/smb.conf to this:
```

[global]
workgroup = HOME
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
dns proxy = no


[public]
path = /home/villermen/public
browsable = yes
writable = yes
guest ok = yes
read only = no

```

I've been through a lot of different settings, but this is the most basic one that should be working according to every resource on the internet. The directory is set up as follows:
```

ls /home/villermen/public -lahtotal 8.0K
drwxr-xr-x 2 nobody    nogroup   4.0K Aug  7 16:34 .
drwxrwxrwx 9 villermen villermen 4.0K Aug  7 16:34 ..

```

Trying to manually connect to \\(server's ip) will give me a no-access message from both my Windows 8.1 pc and Windows 10 laptop.

sudo smbstatus reads:

```

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine
-------------------------------------------------------------------


Service      pid     machine       Connected at
-------------------------------------------------------


No locked files

```

The samba version I'm using is 4.1.6-Ubuntu, on Ubuntu 14.04.3 LTS.

Removing both logfiles (/var/log/samba/log.smbd and /var/log/samba/log.nmbd) and restarting both services will fill them with:

log.nmbd
```

[2015/08/08 15:06:24,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/08 15:06:47,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****


  Samba name server UBUNTU is now a local master browser for workgroup HOME on subnet (server's ip)


  *****

```

log.smbd
```

2015/08/08 15:06:27,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/08 15:06:27.095017,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/08/08 15:06:27.101181,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/08/08 15:06:27.101358,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

```

I've pretty much exhausted all solved threads about issues similar to this one to no avail. What am I missing?

Gr.Viller

EDIT: I forgot to mention that Windows sometimes requests a username and password twice when trying to open \\(server's ip), before showing the no-access error.

EDIT: My Windows 10 laptop now decided it can actually see the server and it works as expected. Windows 8.1 still asks for password twice and then decides to give up.

---

### Post by villermen on 2015-08-09
I got browsing to the server using it's name or ip working (\\ubuntu) by turning the network authentication method of my adapter to "Microsoft: Smart Card or other certificate". It was set to PEAP for whatever reason and I found out through brute forcing all options that this setting was the right one. I still can't seem to get the server to show up in Network Places though...

---

