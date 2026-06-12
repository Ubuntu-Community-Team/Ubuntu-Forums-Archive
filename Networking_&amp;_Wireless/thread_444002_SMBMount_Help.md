---
title: "SMBMount Help"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Socratez on 2007-05-14
I have been having the most frustrating time trying to get my network share to mount on my 7.04 machine .... The NSLU2 server share I am attempting to connect to has a space in the share name.  I can not get connected to share "DISK 2"  because of this. I have tried browsing through nautalis and I get smb://192.168.2.22/DISK%202 in the address bar. I want to have the smb file systems mount a boot time but I can not even connect to them via command line. Can anybody help me out? I have followed a few  how-to's but the issue is how to access a share with a space in it's name? Thanks in advance


Soc


===EXTRA INFO====


This is what I get listed when using smbclient

smbclient -L //192.168.2.22


Domain=[OCEAN] OS=[Unix] Server=[Samba 3.0.11]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN 1         Disk      
        DISK 1          Disk      For everyone
        ADMIN 2         Disk      
        DISK 2          Disk      For everyone
        IPC$            IPC       IPC Service (Network Attached Storage)
        ADMIN$          IPC       IPC Service (Network Attached Storage)
Domain=[OCEAN] OS=[Unix] Server=[Samba 3.0.11]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        EARTH                CENTRALAMERICA

I have tried the following

root@CentralAmerica:/DISK2# smbclient  //192.168.2.22/DISK%1
Password: 
Domain=[OCEAN] OS=[Unix] Server=[Samba 3.0.11]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
root@CentralAmerica:/DISK2# smbclient  //192.168.2.22/DISK%201
Password: 
Domain=[OCEAN] OS=[Unix] Server=[Samba 3.0.11]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
root@CentralAmerica:/DISK2# smbclient  //192.168.2.22/DISK%202
Password: 
Domain=[OCEAN] OS=[Unix] Server=[Samba 3.0.11]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
root@CentralAmerica:/DISK2# smbclient  //192.168.2.22/DISK\1
Password: 
Domain=[OCEAN] OS=[Unix] Server=[Samba 3.0.11]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
root@CentralAmerica:/DISK2#

---

### Post by Nythain on 2007-05-15
have you tried throwing a \ before the space, like Disk\ 2

ok, i see you TRIED with disk\1, but you forgot to actually add the space... the \ doesnt replace teh space, it just lets linux know a space is coming up

---

### Post by dmizer on 2007-05-15
the slug doesn't work well with samba.  but you can implement nfs on it 
instead.[http://www.nslu2-linux.org/wiki/Optware/Nfs-utils](http://www.nslu2-linux.org/wiki/Optware/Nfs-utils)

there's potential that you can make it work correctly with samba, but nfs will be a more appropriate for linux networking anyway.  more information about implementing nfs on your linux box (not on your slug) can be found in the fourth link in my sig.

Nythain ... send me some Arthur Bryants please!!!

---

### Post by Socratez on 2007-05-15
I have not modded my NSLU2 because I do not want to loose my data.... Maybe I can do it without loosing information ? I am not so kean on that as I have over 500GB of information on the disks ....

---

### Post by Socratez on 2007-05-15
I got it all figured out ... I was using the wrong syntax to mount the disks ... I did manage to get them to mount now I will work on automounting at boot time ... thanks for the help thus far ..... Much Appreciated



Soc

---

### Post by Biffa2001 on 2007-05-15
> I got it all figured out ... I was using the wrong syntax to mount the disks

Could you post the corect sytax as I am having the same problem :-)

Cheers
Steve

---

### Post by dmizer on 2007-05-15
were you able to mount with cifs or smbfs?  if smbfs, you're going to run into problems with that.  smbfs will only provide for file transfers up to 2gig.  it's also less stable, so larger file transfers are often a problem.  power to you if it is satisfactory for you, but keep this in mind for the future.

there's some good information on it here: [http://www.movingtofreedom.org/2007/02/06/samba-and-the-nslu2-network-shares-in-gnu-linux/](http://www.movingtofreedom.org/2007/02/06/samba-and-the-nslu2-network-shares-in-gnu-linux/)

i don't think the mod will destroy your data.  but i don't have first hand experience with this unit, so i can't say for sure.

---

