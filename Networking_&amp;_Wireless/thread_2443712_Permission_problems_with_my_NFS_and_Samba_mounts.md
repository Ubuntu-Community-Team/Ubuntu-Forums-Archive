---
title: "Permission problems with my NFS and Samba mounts"
date: 2020-05-19
forum: Networking &amp; Wireless
---

### Post by nocom2 on 2020-05-19
I have a Qnap server containing shared mounts for my win10 and Ubuntu 20.04 clients. Strange things do happen which Ithink are caused by wrong permissions but I am not sure of that. Qnap uses NFS v4 for Ubuntu and Samba for windows. I'll describe the problems on my Ubuntu client for the rest of this thread.

This works ok, I use the NFS network shares for all my work, I can read, modify and delete files and that was ok until I started to use visual studio code (vscode). When I start a bash shell and start `code` to start vscode it starts ok. When I `cd /media` everything is ok, but when I `cd /media/i` (the local mount point of an NFS file share) I get the error 

    ```
cannot open path of the current working directory: Permission denied
```

The same happens to atom I found out later and some other programs like remarkable, but not all. Spyder works ok as does Pinta. The /etc/fstab line for mountpoint /media/i is:

    ```
tinctoris:/files/files /media/i nfs auto 0 0
```

The permissions of /media/i are:

    ```
drwxrwxrwx  7 root   root   4096 mei 12 04:09 i
```

and the permission of tinctoris:/files/files:

    ```
drwxrwxrwx  7 admin  administrators 4.0K 2020-05-12 04:09 files/
```

Is there any reason while programs like code, atom and remarkable cannot run because of permissions? Is it a permissions problem? Any help will be greatly appreciated.

---

### Post by TheFu on 2020-05-19
Is vscode a snap package?  Snaps don't get access to storage outside the user's HOME without a special request AND the snap package has to specifically allow the request.
**snap connections <application-name> --all** will show all the allowed permissions that a snap package allows.  You'll probably want to run something like:
```
snap connect vscode:removable-media
```
to allow vscode to access /mnt/ and /media/ storage locations.

This all assumes vscode is a snap package. If not, then the issue is something else, but at least you'll know it isn't a snap issue.

BTW, 777 permissions are for lazy people who don't care about security.  It is likely anyone on your network can delete all those files.

---

### Post by nocom2 on 2020-05-20
Unsnapping vscode and reinstalling from the microsoft website did the trick. Thanks very much for your solution. The dumb thing is that I had arrived at the same solution when trying to run docker: [https://stackoverflow.com/questions/61554465/cannot-run-docker-from-network-mounted-directory](https://stackoverflow.com/questions/61554465/cannot-run-docker-from-network-mounted-directory), not realizing this was a general problem instead of just docker. And thanks for sharing a solution, however, as all my work consists of working from network shares it gets a bit tedious to provide allowances for all my (now 6) shares. That means banning snap as much as possible. I know, canonical is working in using snap more but the current situation is unworkable for me.  BTW, Thanks for pointing this out to me. I am still some kind of Linux noob.  If you can direct me to some info how to setup the permissions for NFS in such a way that I and my household can easily the access the information on the shares that would be very helpful. Thanks again!

---

### Post by TheFu on 2020-05-20
<rant>

I don't/won't use docker.  Tired of chasing the new shiny thing. Did that in the 1990s.  Have a few LXD containers running here. They work pretty well and are easy to understand. Currently running a DNS server inside one. Need to setup a secondary to handle times when the DNS host machine is down.

Lots of opinions follow.  I'm not any expert on snaps, so this are what I've seen and read. New versions may solve the issues.

snaps are new to everyone, except the true believers.  The true believers can't/won't consider that Unix is supposed to let the users have control, not the admin.  A desktop/workstation isn't the same as a cell phone.  There are lots of different ways for programs to be run, programs to access data, and local control over those areas **must** be provided.  Snaps break those ideas.

I think snaps, in extremely specific situations, can be useful.  Given the choice, I'd rather NOT have any snaps on my systems.  If I need a program to be constrained, then I can constrain it using apparmor or firejail or a Linux container or one of the other 10 methods available to us.

I know of NO METHOD to specifically allow NFS mounts to be accessible by snap-constrained programs.  This is a failure in foresight by the snap team and would have been obvious to many.

There is the /mnt/ and /media/ workarounds, but whoever decided those were the only locations that snaps may be extended to support hasn't read and understood the Linux File System Hierarchy standards document.  

/mnt/ is for temporary mounts for admins to perform file system work.  It was never meant for permanent mounting.
/media/ is for temporary portable mounts, like a thumb drive.  Stuff that is there for a few hours only.

Where are permanent mounts via eSATA, USB3, Infiniband, SATA, SCSI, IDE supposed to go?  Well, not under /mnt/ or /media/  that's 100% certain.  The snap team is wrong and has ignored calls for local control over additional storage locations.   [https://forum.snapcraft.io/t/snaps-and-nfs-home/438](https://forum.snapcraft.io/t/snaps-and-nfs-home/438) where they say some other part of the OS is the issue.  That doesn't help us.  
[https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)
[https://askubuntu.com/questions/1033344/how-to-give-snaps-access-to-somedir](https://askubuntu.com/questions/1033344/how-to-give-snaps-access-to-somedir)
bind mounts, hardlinks and symbolic links don't workaround this issue either.

[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1643706](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1643706) here they call it a "feature."  And it is, until it isn't.
One reply is actually suggesting that a GTK library will be required, then use a FUSE file system that gets registered with snaps.  Just give us local control over the constrained areas. Period.  Anything less is "broken by design."

Using NFS is extremely common in corporate networks.  I've been using it since the early 1990s and have seen LANs with thousands of client machines all using NFS for many different purposes. Snaps are broken until NFS support is solid, under local control.
```
istar:/d/D1                       nfs4  3.5T  3.5T   24G 100% /d/D1
istar:/d/D3                       nfs4  3.6T  3.6T   23G 100% /d/D3
istar:/d/D2                       nfs4  3.6T  3.6T  5.3G 100% /d/D2

```
How do we access files on those NFS shares when a snap package is involved?  The short answer is, we don't.  So, 10TB of files cannot be accessed by the tools that need to access them, if snaps are used.

What about people working in teams needing to access data in shared repos?  That data doesn't belong in /home or /mnt or /media.

I haven't checked if CIFS mounts have the same issue, but suspect they do.  I bet THAT would be fixed, if broke, because i
</rant>

There are a number of threads here about snaps and how they aren't working for users.  You are far from the first.  I suppose we all need to open separate bugs for snaps - hundreds of bugs - to get the point across.  
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

