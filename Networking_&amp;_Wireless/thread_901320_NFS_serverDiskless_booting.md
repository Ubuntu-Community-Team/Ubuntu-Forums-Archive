---
title: "NFS server/Diskless booting"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by prats84 on 2008-08-26
Hi, 
 I want to enable Diskless booting. 
  
  My NFS server (tftp also) ip is 192.168.11.13
  My server (dhcp,Dns,etc) is 192.168.11.3
  some clients 
All connected to a switch.
  I am using vmlinuz-2.6.24-19-server 
 None of the clients are able to boot using PXE. i hve enabled PXE boot from the Bios.
**NFS server Configs **
I mounted the filesystem on NFSserver using
  ```
sudo mount -tnfs -onolock 192.168.11.13:/nfsroot /mnt 
```

Now, when i try to copy the file system on a NFS mount i.e /mnt i get File Name too long... with command 
     ```
 cp -ax /. /mnt/. 
     cp -ax /dev/. /mnt/dev/.

```

[B]
Server config[/B] :
  My dhcpd.conf  i have added 
   ```
   allow booting;
      allow bootp;
```
   
  and 
    ```
 
     next-server 192.168.11.13;
     filename "pxelinux.0"
```

Please help me why am i not able to boot the clients. 
Thank You
Pratik

---

### Post by prats84 on 2008-08-26
Now my Client machine boots up showing the Dhcp addess and its Ip... 
but gives an error 

PXE-E32 : TFTP open timeout.. 
 i tried to google it and found regarding /etc/inetd.conf

which i have updated as 

```
tftp  dgram  udp  wait  root  /usr/bin/in.tftpd -s /tftpboot
```

---

