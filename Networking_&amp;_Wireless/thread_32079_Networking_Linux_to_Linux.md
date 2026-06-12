---
title: "Networking Linux to Linux"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by mendahu on 2005-05-06
Hello all,

I've just switched from windows to Ubuntu linux on my two computers (one's a notebook).  I'm having a hard time networking the two computers so that I can share files.  All I really want to do is have one folder that's accessible (read and write) by both computers, stored on my main PC (not the laptop).   I also wouldn't mind printer sharing, but that's not a priority.

I am not a programmer at all, so if anyone can help me using layman's terms, I'd be VERY appreciative.  

I'm not sure if I should use Samba or NFS.  I can navigate my way around a terminal with minimal proficiency.  Any help would be appreciated.

Jake
Windows Ex-pat, Alberta, Canada

---

### Post by ifrflyer on 2005-05-06
Many will be more knowledgable than me on this (I'm new at this too) but NFS is really a slow option and I think you should look at some others. Samba has the advantage of benig able to allow in Windows and Mac machines and that's always useful. It's fast and easy to configure, and you can get help anywhere. 

Sshfs-fuse  is a *really* nice option which allows you to mount a network drive across an encrypted secure connection; in this way you can span your network (with an IP pointnig service such as dyndns) across the internet from, say, a coffee shop, and have all your files secure and protected. It's wonderful. 

You can also mount a samba drive through a tunneled SSH connection by using port forwarding (google "port forwarding" for more). That's a great option.

Anyone else?

---

### Post by luna6 on 2005-05-06
also one more way to transfer files is through good ole ftp....chances are you have vsftpd installed and can set it up with minimal fuss (edit the /etc/vsftpd.conf) and do not allow anonymous logins, allow local users, and write access..and done...I use samba as well....but i noticed mostly when I want to view files from another computer, or stream media content..I will select the samba mounted drives, but when throwing files from one computer to the other I usually open up gftp and transfer files that way....I just prefer it..:)

---

### Post by mendahu on 2005-05-06
It may be minimal fuss to you (setting up vsftpd), but its more or less an alien language to me, opening up that config file.  I thank you for your help, but I'm gonna need step by step help in setting this up.  

-Jake

---

### Post by mendahu on 2005-05-06
Hey all,

Thanks again for all the help you offered.  I managed to get Samba to like me, and I now have my folder shared to both computers.  Thanks!

-Jake

---

