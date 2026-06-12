---
title: "tftpd-hpa write not working Ubuntu 20.04"
date: 2022-10-11
forum: Networking &amp; Wireless
---

### Post by stefan.hulting on 2022-10-11
Hi 

Cannot get tftpd-hpa to enable write on newly updated Ubuntu 20.04.

if i do a "get test.txt" it works, it does not work when "put othertest.txt"

Error message "Transfer timed out." usually the file gets created but is 0 (null/empty).

Locally everything works, not from same network, or other network.

Setting:

/etc/default/tftpd-hpa
```

# /etc/default/tftpd-hpa


TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/tftp"
TFTP_ADDRESS=":69"
TFTP_OPTIONS="--secure --create"

```

netstat -anpu | grep 69
```

udp        0      0 0.0.0.0:69              0.0.0.0:*                           361977/in.tftpd
udp6       0      0 :::69                   :::*                                361977/in.tftpd

```

ls -la /srv/tftp
```

total 8
drwxrwxrwx 2 tftp nogroup 4096 Oct 11 09:11 .
drwxrwxrwx 3 tftp nogroup 4096 Oct 11 09:10 ..
-rwxrwxrwx 1 tftp nogroup    0 Oct 11 09:26 test.txt

```

---

### Post by The Cog on 2022-10-11
If I recall correctly, the tftp server has a security requirement that the file you want to upload to it must already exist and be world-writable. So you have to know what filename you expect, touch (or otherwise create) that file, set it world readable, then do the actual transfer. It's because tftp is un-authenticated so otherwise, anyone could put any old malware there.

---

### Post by stefan.hulting on 2022-10-11
Hi

Thanks for the update :-)

Even though i followed the guide to enable write in the TFTP_OPTIONS ( --create ), and made the folder "chmod -R 777" ( for troubleshooting ).

What works:
- "get" and "put" locally on the machine
- "get" from machine in the same subnet

Doesnt work:
- "put" from machine in the same subnet
- "get" and "put" from any other network ( Yes, network connectivity has been verified for 69/udp )

---

### Post by The Cog on 2022-10-11
I don't know about put from other machines - that may well be a restriction built into the tftp program. 

But I strongly suspect that your access from other networks is being restricted by firewall rules. tftp is unusual that only the first packet uses port 69 - the connection moves away from port 69 to using a different and random udp port number at each end. It is quite possible that a firewall somewhere is not tracking this. Only a network analyser such as tcpdump will really show this up.

---

### Post by stefan.hulting on 2022-10-13
SOLVED!

I did NOT expect that...

I moved the tftpd server to a VMWare machine, and it started working :-)

Seems the fault was related to a patch for Hyper-v (which the tftpd server resided) released in Juli 2022.

[COLOR=#555555][FONT=&quot]KB5015807 @ [https://support.microsoft.com/en-us/help/5015807](https://support.microsoft.com/en-us/help/5015807) for Windows 10, Windows Server 2016[/FONT][/COLOR]
[COLOR=#555555][FONT=&quot]KB5015808 @ [https://support.microsoft.com/en-us/help/5015808](https://support.microsoft.com/en-us/help/5015808) for Windows 10, Windows Server 2016[/FONT][/COLOR]
[COLOR=#555555][FONT=&quot]KB5015811 @ [https://support.microsoft.com/en-us/help/5015811](https://support.microsoft.com/en-us/help/5015811) for Windows Server 2019

The resolution for us was to update the Hyper-v to the latest update. 

Conclusion: tftpd server worked before the Juli patch, after the Juli patch you get the error, Updated to the latest Windows Server CU update yesterday tftpd server started working again.[/FONT][/COLOR]

---

### Post by mIk3_08 on 2022-10-13
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by The Cog on 2022-10-15
Wow! Thanks for posting that solution - As you say, completely unexpected.

---

