---
title: "Port Opening / Port Forward"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by LetsLinux on 2006-11-18
Hi,

I've tried searching around both in this forum and on google - and I can't seem to find the right solution for my problem, so now I'll try writing a new thread.

Is there a way to open ports within Ubuntu? I've seen around, that typing a certain command makes a list over ports being "listened" to. However I'm using different kinds of p2p programs etc. and whish to open ports for these - especially LinuxDC++.

Is there a way to do this? I have already forwarded the porst on my router (which is Linksys WRT54G - I think - and it works in Windows)

I hope that any of you can help me!

Thanks

Jonas

---

### Post by PilotJLR on 2006-11-18
In order to see what ports your computer is listening on, try this:
```
netstat -l --protocol=ip
```

---

### Post by LetsLinux on 2006-11-19
Hi, 

I get this:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:9601                  *:*                     LISTEN
tcp        0      0 localhost:40709         *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:56684                 *:*                     LISTEN
tcp        0      0 *:46188                 *:*                     LISTEN
tcp        0      0 localhost:40751         *:*                     LISTEN
tcp        0      0 *:30864                 *:*                     LISTEN
tcp        0      0 *:11411                 *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 localhost:9050          *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp        0      0 *:34527                 *:*                     LISTEN

```

Do you know what to do next?

---

### Post by johnny9794 on 2006-11-19
> **LetsLinux said:**
> Hi,

I've tried searching around both in this forum and on google - and I can't seem to find the right solution for my problem, so now I'll try writing a new thread.

Is there a way to open ports within Ubuntu? I've seen around, that typing a certain command makes a list over ports being "listened" to. However I'm using different kinds of p2p programs etc. and whish to open ports for these - especially LinuxDC++.

Is there a way to do this? I have already forwarded the porst on my router (which is Linksys WRT54G - I think - and it works in Windows)

I hope that any of you can help me!

Thanks

Jonas

If i am correct, try using firestarter ```
sudo apt-get install firestarter
``` if not installed already.

Then fire up firestarter 
For dapper 6.06.1 it will be under Apps/Internet/firestarter

For edgy 6.10 it is under System/Admin/Firestarter

Once firestarter is up, navigate to policy tab and insert the service and port number you want to allow and hit apply.

then you should be set, worked for my amsn transer port and proftpd port.

---

