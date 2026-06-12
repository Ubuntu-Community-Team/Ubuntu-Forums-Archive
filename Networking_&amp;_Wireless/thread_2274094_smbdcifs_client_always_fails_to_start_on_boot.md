---
title: "smbd/cifs client always fails to start on boot"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by Legeril on 2015-04-17
Hi guys,

I'm running Samba/smbd to connect to my windows network at work, and CUPS to help me print. 
smbd never manages to load on boot, I've included the last entry from the /var/log/log/smbd

```
[2015/04/18 09:28:55,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/04/18 09:28:55.259829,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/04/18 09:28:55.353599,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/04/18 09:28:55.353932,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL


```

Seems to be not connecting to CUPS but, why would it need that to load?

---

### Post by bab1 on 2015-04-17
> **Legeril said:**
> Hi guys,

I'm running Samba/smbd to connect to my windows network at work, and CUPS to help me print. 
smbd never manages to load on boot, I've included the last entry from the /var/log/log/smbd

```
[[COLOR="#FF0000"]2015/04/18 09:28:55,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu ***_started_***.[/COLOR]
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/04/18 09:28:55.259829,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/04/18 09:28:55.353599,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/04/18 09:28:55.353932,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL


```

Seems to be not connecting to CUPS but, why would it need that to load?

The smbd daemon has loaded, see above in red.  

I don't use Samba to talk to CUPS so my output looks the same as yours.  I use IP networked HP printers.

---

