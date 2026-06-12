---
title: "cannot connect from vista to ubuntu 8.04"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by charlie204 on 2009-04-23
I am trying to connect from my vista machine to my ubuntu machine, and I cannot find the computer in my network workgroup. Before I installed samba and firestarter I was able to access my share. Now, if I use the IP address, I can get to the share, but not by using the computer name which had worked at some time. I also installed PuTTy on the Vista machine, attempted to connect via ssh protocol, and it cannot locate the computer by name. When I attempt to connect via ip address, it says connection is refused.
 
ping says:
Reply from 192.168.1.104: bytes=32 time<1ms TTL=64
 
I do not know what to try next.

---

### Post by Peter09 on 2009-04-23
Have you set the correct workgroup in smb.conf?

---

### Post by charlie204 on 2009-04-23
smb.conf is supposed to be in /etc, isn't it? I do not see the file.

---

### Post by charlie204 on 2009-04-23
I found it. /etc/samba/smb.conf
 
I have the line workgroup = workgroup within the [global] settings area.

---

### Post by LiamWilson on 2009-04-23
Can you acess them ny going 'Places' > Network > Windows Network (and then clicking through the various options)

---

### Post by scheuri on 2009-04-23
The whole thing with resolving names in windows and not connecting to your linux box with hostnames (but IP) sounds like a WINS issue.

I guess you do not have a DNS installed in your private network, therefor Samba might act as some sort of DNS (WINS) for Vista and might not serve the correct information.

Maybe google will help you. Keywords might something along the line of "vista samba wins".

However, there is a little workaround for the time being.
If your linux box has a fix IP in your private network you might want to add that to the hosts-file of vista (with the corresponding hostname).
So vista will use the hosts file and resolve the name of your linux box (hopefully correctly).

That is not a solution to your problem, it is a workaround!

cheers
scheuri

---

### Post by charlie204 on 2009-04-23
I see in /var/log/samba directory, a log for info from this computer. It says:
[2009/04/22 23:53:56, 0] smbd/service.c:make_connection(1191)
dz530csm (192.168.1.107) couldn't find service shar
[2009/04/22 23:53:56, 0]  param/loadparm.c"process_usershare_file(4606)
process_usershare_file: stat of /var/lib/samba/usershares/shar failed. No such file or directory.
Looking in that directory, I see no files.
Is this a complaint of windows or of itself?

---

