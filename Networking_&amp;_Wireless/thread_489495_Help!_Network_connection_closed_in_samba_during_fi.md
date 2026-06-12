---
title: "Help! Network connection closed in samba during file transfers"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by steve457 on 2007-07-01
I'm having an issue with my wired network connection.  I have setup a folder share in Samba and am able to browse the folder from my Windows machine.  When I am copying files from the Windows machine to my Ubuntu box the connection will randomly close during the transfer.  On the windows machine an error comes up  saying that the network share is no longer available.  Here are some of the entries from the samba log files.


```
[2007/07/01 08:28:22, 0] lib/util_sock.c:get_peer_addr(1229)
  getpeername failed. Error was Transport endpoint is not connected
[2007/07/01 08:28:22, 0] lib/util_sock.c:get_peer_addr(1229)
  getpeername failed. Error was Transport endpoint is not connected
[2007/07/01 08:54:27, 0] smbd/server.c:main(847)
  smbd version 3.0.24 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/07/01 08:54:27, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/07/01 08:54:27, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!


[2007/07/01 08:28:22, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2007/07/01 08:28:22, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)

```

I was able to transfer around 33GB without a disconnect yesterday once, but after that even transferring around 20GB of data would usually involve a disconnect somewhere before the transfer completes.  I've tried copying from both Vista and XP and both result in random disconnects.

Also, once this disconnect happens I no longer have a network connection in Ubuntu.  The network icon says I am connected, but I am unable to browse any websites.  The only way I found to resolve this is to reboot the Ubuntu machine.  I'm also fairly new at administering Linux.  I'm sure there is way to fix the connection without the reboot, but I have no idea how to do that.  

Any ideas on what I can do to try and pinpoint the problem?

---

### Post by steve457 on 2007-07-01
Ok, the disconnect happened again.  I found this in the log.nmbd file at the same time the disconnect occurred.  

```

[2007/07/01 09:40:43, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server SNOOPY is now a local master browser for workgroup SYDNEY on
 subnet 192.168.1.168

```

Could this somehow be causing the disconnect and loss of network connection?  Also, how can I reset the network connection once it fails without rebooting my ubuntu machine?

---

### Post by jjohns63 on 2007-10-10
Have you been able to find a solution? I am having this very same problem and it is very frustrating. The box running Ubuntu Feisty completely loses all network connectivity and the only way for me to correct this is to manually reboot, since it is being administrated via SSH.

My logs show:
```
[2007/10/10 08:34:12, 0] lib/util_sock.c:read_data(534)
  read_data: read failure for 22194 bytes to client 130.126.xxx.xxx. Error = No r$
[2007/10/10 08:34:12, 1] smbd/service.c:close_cnum(1150)
  6wqn9b1 (130.126.71.77) closed connection to service Movies
[2007/10/10 08:34:12, 1] smbd/service.c:close_cnum(1150)
  6wqn9b1 (130.126.71.77) closed connection to service Music
```

6wqn9b1 is the name of my Windows computer. Also, I am using Windows Vista, I will try to test using XP later today.

---

### Post by vashwood on 2008-05-29
Has any of you guys found the solution?  This is happening to me too.  Although, I'm still able to try to retransfer w/o a reboot.

---

