---
title: "Can't see Windows shares"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by selwynpolit on 2008-04-22
I used to be able to browse via Dolphin to my windows computers by clicking on Network, selecting Samba shares and then clicking workgroup.  Now Dolphin says Loading directory for a long time then it says timeout on server workgroup.

I've been keeping up with all the patches.  Any suggestions where I should look?  This is an ASUS M2A-VM board with an AMD 64x2 processor and 4GB Ram.  I am running the 64 bit version of Kubuntu 7.10.

thanks

Selwyn

---

### Post by sunspots on 2008-04-22
I'm also having this problem.

I have configured Kubuntu 8.04 RC on vmWare. Set up Samba with a share. When I look in Network Neighbourhood on Windows XP, I can see the Kubuntu directory.

However, trying to look at WIndows inside Kubuntu just sits there and eventually times out. I do see the Windows network in the SAMBA share.

Do I need to install the ntfs module in Kubuntu?
Thanks

---

### Post by selwynpolit on 2008-04-27
> **sunspots said:**
> I'm also having this problem.

I have configured Kubuntu 8.04 RC on vmWare. Set up Samba with a share. When I look in Network Neighbourhood on Windows XP, I can see the Kubuntu directory.

However, trying to look at WIndows inside Kubuntu just sits there and eventually times out. I do see the Windows network in the SAMBA share.

Do I need to install the ntfs module in Kubuntu?
Thanks

I don't think you need to install an ntfs module - I didn't before when it was working on my system. 

I think it might be a configuration thing - but no-one seems to know about it.  I have installed ubuntu 8.04 in my vmware setup and it sees my windows shares just fine.  It hiccupped a few times though when I changed the vmware network setup but always came back after a reboot.  My kubuntu 7.04 machine however remains steadfastly uninterested in seeing the windows network devices.  I tried live booting on a kubuntu 8.04 CD and it had no problem so I know my hardware is ok.  

I've been digging around a bunch on the web and found a nice article about mounting windows shares at [http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html) but that didn't get me down the road of what the permissions and issues are.

Good luck.
Selwyn

---

### Post by sunspots on 2008-04-28
Thanks for the links. I started reading and trying the samba mount command, but it gave me an error. Hunting around for the error I found this link

[http://www.thatsquality.com/linux/mounting-windows-smb-file-shares-using-cifs](http://www.thatsquality.com/linux/mounting-windows-smb-file-shares-using-cifs)

It talks about using CIFS instead of smbfs. It also mentioned that you had to create a folder somewhere (I created in /mnt) and then do the mount with CIFS. Well that worked fine. Possible the smbfs would have also now the folder for the share is created.

I can now see any files & folders on that drive now it is mounted. However, now I have a problem writing to the drive.

Even though my permissions on the folders are drwxrwxrwx and ownerships are root root. I did notice that mnt has permissions of drwxr-xr-x. So, I tried sudo to create a file on the share, but still got error can't write to the folder.

Back to thinking I might have to install ntfs support.

Have you been able to write to your share?

Thanks again for the pointers.

---

### Post by Edk on 2008-06-12
Don't know if anyone is still monitoring this, but this command got me out of the problem:

[INDENT]sudo mount -t cifs //IP_of_the_server/path_of_server_if_there_is_one /mnt/name_of_mount_point -o username=xxx,password=xxx,uid=MY-USERNAME-ON-UBUNTU,gid=users[/INDENT]

So an example might be

[INDENT]sudo mount -t cifs //192.168.0.6/data /mnt/server -o username=MYSERVERNAME,password=MYSERVERPASSWORD,uid=MY-USERNAME-ON-UBUNTU,gid=users[/INDENT]

Hope this helps

---

### Post by selwynpolit on 2008-06-12
In my case I believe the problem is a DNS problem.  It turns out that I can connect to machines using their IP address but for some reason my Kubuntu can't resolve the MS Windows computer names any more.  I believe MS Windows uses netbios (netbeui now?) for it's names. At one point I could just browse my workgroup, now it just times out.  Its a puzzler...

Selwyn

---

