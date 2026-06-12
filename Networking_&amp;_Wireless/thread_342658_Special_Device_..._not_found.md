---
title: "Special Device ... not found"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by drs305 on 2007-01-20
Found a typo. Think I answered my own question. Please spend your time helping another. Thanks.


>>>>>>>>

I found I can't edit the title, but it should probaby read "Special Device...does not exist".

I am new to Edgy and just tried to make two computers share files with NFS.  I eventually got the main computer (xxx)  to mount a folder on the second (yyy) and was happy. I then (big mistake) tried to reverse the process so I could view yyy's folder on the main computer. Now I can't get either to work.

When I try to mount the xxx folder on the second computer with the mount command from the root directory:
mount 192.168.0.3/home/xxx/xxx /mnt/abcdef
I get a message stating:
special device 192.168.0.3/home/xxx/xxx does not exist



Things I changed since the first successful attempt include the etc/exports, hosts.deny and hosts.allow files but I am pretty sure I changed them back on the correct machine.  I have permissions for 192.168.0/255.255.255.0 and then even added specific IPs when the universal one didn't seem to work. I 'commented out - #' everything in the deny file to ensure I wasn't blocking the computer. I may have installed different nfs server/client files too but don't remember what I did with Synaptec. It seemed I had to have server or client files, but it wouldn't let me have both. Currently I have nfs-common and nfs-kernel-server installed on the main computer and nfs-common and nfs-user-server on the second computer.

I use DHCP and my main computer has always (at least in Windows) been 192.168.0.3 and the second 192.168.0.2.  Ping to both those addresses works normally.  I have tried to include specific and universal IP addresses in the above files but still can't get the second computer to find the host. (I never made any inputs in the hosts file.) Note: the domainname command doesn't seem to work.

That also leads me to another question. For a single home computer, what would the server name be if I didn't use an IP address? I assume my hostname is my logon name but how do I set the domain name or did I designate a name during installation (and where would I find it now).

Thanks for any assistance. I know I'm casting a pretty broad net.

---

