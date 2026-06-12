---
title: "cifs version"
date: 2019-09-26
forum: Networking &amp; Wireless
---

### Post by vishnumrao on 2019-09-26
Background info: I have a SSD connected to my RT-AC1900P router. I use it as a NAS drive and is backed up to a second USB connected HDD. I primarily use the NAS drive to store pics & videos clicked on our phones and SLR. 

Problem statement: transfer speeds from my Ubuntu 18.04 machine to the NAS drive are super slow. about 1-1.5 MBps. I have a dual boot. Windows 10 gives me about 25-32 MBps. 

I am trying to figure out the best mount options to enable higher transfer speeds.

My current fstab entry is as below:

```
//192.168.1.1/OCZ1920GB_0 /media/SharedOnRouter cifs vers=1.0,username=myname,password=mypass,iocharset=utf8,sec=ntlm 0 0

```

This works to mount and do transfers. But terrible speeds. 

My router supports SMBv1 & SMBv2. See attached file for router menu screenshot. 

Any recommendations on the right mount settings to enable a connection at SMBv2?

Note: I am using Ubuntu 18.04. Not 10.04. I have not been very active on the forum of late. Hence the old disto shown.

---

### Post by Morbius1 on 2019-09-26
> //192.168.1.1/OCZ1920GB_0 /media/SharedOnRouter cifs [highlight]vers=1.0[/highlight],username=myname,password=mypass,iocharset=utf8,sec=ntlm 0 0
[highlight]vers=1.0[/highlight] refers to SMBv1 so to change it to SMBv2 change the vers number to 2.0  - [COLOR=#0000cd]**vers=2.0**[/COLOR]. You should also remove the [COLOR=#0000cd]**sec=ntlm**[/COLOR] option as well to be consistent with SMBv2.

You will see an increase but I seriously doubt it will increase 25 fold to match a Windows machine.

---

### Post by vishnumrao on 2019-09-26
Thanks Moribus1. your recommendation helped me mount the NAS share. But I somehow seem to have lost write privileges to the share. So I can't test write speeds. Any additional params that I need to add to the mount options?

---

### Post by Morbius1 on 2019-09-27
Take possession of the mounted share. So if you are now using this:
[highlight]//192.168.1.1/OCZ1920GB_0 /media/SharedOnRouter cifs vers=2.0,username=myname,password=mypass,iocharset=utf8 0 0                      [/highlight]
Use this:
[highlight]//192.168.1.1/OCZ1920GB_0 /media/SharedOnRouter cifs vers=2.0,username=myname,password=mypass,[COLOR=#0000cd]**uid=1000**[/COLOR],iocharset=utf8 0 0                      [/highlight]
To find the correct uid number for your user name run this command:
```
id
```

---

### Post by vishnumrao on 2019-09-28
Thanks for the help. I am able to mount it with vers=2.0. But there was hardly any change in the transfer speeds. write speeds stuck at 1.5-1.6 MBps. 

I mounted the NAS share on my raspberry pi model B. Even that manages 5-6 MBps. There the bottleneck becomes the single core CPU. I can see it maxing out!

Any ideas on how to improve smb / cifs throughput on Ubuntu?

---

