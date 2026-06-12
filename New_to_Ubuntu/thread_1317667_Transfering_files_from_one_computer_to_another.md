---
title: "Transfering files from one computer to another"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by mathfreak123 on 2009-11-06
Hey, I want to transfer a huge number of files from one computer to another. Both computers are in my home network.

1. I was wondering if I could use a single Ethernet cord to connect one computer directly to the other, and I realized that it didn't work.

2. My second idea was to have both computers connected to the router, and use ftp or sftp. I've used ftp and sftp before, but I've never gotten another computer to allow incoming sftp connections before (which is probably why I failed).

Can I have some help to get either idea working?

---

### Post by unamanic on 2009-11-06
For option 2:
Are both runing Linux? If so try, "sudo aptitude install openssh-server" on one or both and use either use Placed->connect to server... SSH -or- rsync -or- scp

---

### Post by Dark Aspect on 2009-11-06
> **mathfreak123 said:**
> 1. I was wondering if I could use a single Ethernet cord to connect one computer directly to the other, and I realized that it didn't work.


You need a [crossover cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") for this to work.

> **mathfreak123 said:**
> 2. My second idea was to have both computers connected to the router, and use ftp or sftp. I've used ftp and sftp before, but I've never gotten another computer to allow incoming sftp connections before (which is probably why I failed).

I have no idea

Now, I would probably just remove one hard drive and mount it as a second hard drive in one of the computers. Than copy and paste the data from one to the other.

---

### Post by sailthesea on 2009-11-06
> **mathfreak123 said:**
> Hey, I want to transfer a huge number of files from one computer to another. Both computers are in my home network.

1. I was wondering if I could use a single Ethernet cord to connect one computer directly to the other, and I realized that it didn't work.

2. My second idea was to have both computers connected to the router, and use ftp or sftp. I've used ftp and sftp before, but I've never gotten another computer to allow incoming sftp connections before (which is probably why I failed).

Can I have some help to get either idea working?

 Well I can't really help but am trying to do something similar (access my Desktop with my laptop on the home network) So I'll post in

 1. You would think that would work but its not like that

 2. If you have Windows and Ubuntu on the same network I think the firewall causes the problem Have been trying this out but have grown weary of running round the house restarting and fiddling with machines

 In theory you should be able to support file sharing over your secured home network quite easily Am hoping your thread might help me to learn how as well!
 If I get any more ideas I'll be back But it's bed for now (been up for 23 hours Zzz
 Good luck!

---

### Post by Darce on 2009-11-07
If the PC's are on the same network and can already 'see' each other, isnt it simply a matter of sharing some folders ? Open up the file browser, right click on a folder and select Properties. Click the 'Share' tab, fill in the blanks and press ' Create Share' You may be asked to install the Windows Networks Sharing Service.

---

### Post by SaintDanBert on 2009-11-07
> **Darce said:**
> 
If the PC's are on the same network and can already 'see' each other, isnt it simply a matter of sharing some folders ? Open up the file browser, right click on a folder and select Properties. Click the 'Share' tab, fill in the blanks and press ' Create Share' You may be asked to install the Windows Networks Sharing Service.


If both boxes are linux on the same LAN (at home), enable NFS (network file services) and then mount resources from one workstation as resources on the other workstation. I don't suggest doing this across the public internet, but in the security of your own LAN, it seems fine to me.

~~~ 0;-Dan

---

### Post by mathfreak123 on 2009-11-07
Both computers are on Linux.

> **unamanic said:**
> For option 2:
Are both runing Linux? If so try, "sudo aptitude install openssh-server" on one or both and use either use Placed->connect to server... SSH -or- rsync -or- scp

I'm going to try this idea first, later.

---

### Post by doas777 on 2009-11-07
ssh is slower than other options, since it is encrypted. samba is probably your best bet. it runs at about 10MBps on 100mbps links, and 30-35MBps on gigabit links. scp usually runs at about 15MBps on gigabit.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)

---

### Post by Iowan on 2009-11-07
Just to give you [another]("http://ubuntuforums.org/showthread.php?t=218630") option...

---

### Post by mwalimu54 on 2009-11-07
This may not be quite what you're looking for, but did you ever consider Dropbox?  [http://getdropbox.com]("http://getdropbox.com")  It's a pretty smooth cloud system if both boxes are on the web.

---

### Post by mathfreak123 on 2009-11-11
> **Iowan said:**
> Just to give you [another]("http://ubuntuforums.org/showthread.php?t=218630") option...

This method worked great. Thank you for pointing me to this!

---

