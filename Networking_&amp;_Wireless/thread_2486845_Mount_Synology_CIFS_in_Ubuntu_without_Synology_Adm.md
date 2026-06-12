---
title: "Mount Synology CIFS in Ubuntu without Synology Administrator account"
date: 2023-05-13
forum: Networking &amp; Wireless
---

### Post by john878433 on 2023-05-13
I'm trying to mount a Synology CIFS share in Ubuntu 20.04 VM. I've been working for days trying to wrap my head around this and fix the issue I'm having.
Currently I have a working CIFS mount. But the credentials that I'm using are for the Administrator in Synology. To me that could be a security issue. The reason I used the administrator is because Error 13 Permission issues when trying to mount the share.
I use a credentials file for authentication
```

/home/john/.smbcredentials

```
Contents of credentials file (edited):
```

username=synologyadmin
password=supersecretpassw

```
My fstab file has this line (edited):
```

//192.168.x.x/backup /home/john/server cifs credentials=/home/john/.smbcredentials,vers=3.0,nounix,iocharset=utf8,uid=1000,gid=1000,file_mode=0777,dir_mode=0777 0 0

```
I made another user with administrator rights (and password) on my Synology with read and write access to  //192.168.x.x/backup. Changed the credentials file to this new administrator. But the error 13 remains. Who has the golden tip to fix this issue?

---

### Post by TheFu on 2023-05-14
So, NFS is the protocol used by Unix for file access over a network. Synology should support this.  Is there a reason you don't use it?  NFS mounts aren't per-user. They are system-to-system.  Normal Unix permissions control access to NFS mounted storage.  It also happens to be a little faster than CIFS and much better for media streaming stuff.

[https://kb.synology.com/en-us/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-us/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

Synology questions are best asked on their website/forums, since many of their models run a stripped down Linux.
BTW, mounting extra storage under a user's HOME directory is generally a bad idea.  Mount it somewhere else, then use a symlink to make access to it easier, if you must.

As for NFS mounts, those are easy, just add to the fstab.  

```
mkdir /media/server
```
Then use sudoedit to modify the /etc/fstab with something like this:
192.168.x.x:/backup /media/server nfs  nconnect=2,async   0 0[/CODE]
I've assumed you  enabled "nfs service" in the synology.  Then you can use chmod and chown just like on any other Unix-like OS to manage permissions.

---

### Post by john878433 on 2023-05-15
Thanks for the reply. I'm aware of the existence of NFS. My reason for using CIFS/Samba is that I'm trying to make a Samba share on my TrueNAS server. This share needs to work with Docker/Portainer AND be accessible with an iPhone/iPad. NFS doesn't work with my Apple devices. Couldn't get the CIFS mount to work in Portainer so I started experimenting with my Synology server and Ubuntu VM (runnimg on my TrueNAS). I do have Portainer working with external NFS mounts.

---

### Post by TheFu on 2023-05-15
I don't use those container tools, but the tools I do use require native Linux file systems.  That would mean that CIFS won't work, but NFS should.    I would check whether CIFS can be used where you need it, related to Linux containers.  I have doubts, but don't actually know.

For my portable Android devices, I use sftp/rsync to transfer files when I'm not using nextcloud.  Every networked OS has good-to-great sftp clients.  On Linux desktops, almost every file manager supports using sftp:// URLs, assuming ssh has been installed.  There's also sshfs.  Just throwing out some ideas.

Sorry, I'm no help with CIFS.  I have it setup on 1 system here, but barely use it anymore since we powered off all the MSFT stuff about 18 months ago (still have 1 VM to boot for tax stuff, as needed). When that 18.04 system gets a fresh 20.04 install (this week), I doubt I'll bother setting up CIFS again.

---

### Post by john878433 on 2023-05-16
Thanks again. I just installed ShellFish on my iPhone . It has SFTP built in and integrates nicely with the iOS files app. With this app I can access my TrueNAS NFS shares. My Docker containers write to these NFS shares. Having direct access to edit and upload files now is very nice. But I still see value in using CIFS shares and being able to mount them in Ubuntu. If I find a solution I will post it there.

---

### Post by TheFu on 2023-05-16
CIFS definitely has a place ... if you have MS-Windows clients.
But with Ubuntu/Linux as the client, NFS would be the preferred solution.  There are many different CIFS implementations and MSFT keeps changing it, especially since around 2019 when they decided to address many of the security problems with their implementation.  Since that time, other implementations have tried to follow the MSFT defaults - sometimes successfully and other times, not so much.  For example, when MSFT stopped using nmb to broadcast storage locations and switched to mDNS, that was a huge change that not all Linux distros caught.

Linux has a problem.  There are users still with NT file sharing enabled and others running Windows11 who want the latest, incompatible, solution.  Which settings should be the default for deployments?  Well, When Win7 support ended, the Samba team tried to make the default be what worked with Win10.  That broke lots and lots of systems.  Since I don't have a Synology, I suspect their NAS boxes had the exact same issues as Linux Samba did/does.  They have to pick the defaults to be compatible with the greatest number of their users.  Ubuntu users connecting to a NAS would prefer to use NFS for obvious reasons, so I doubt much, if any, testing was performed around an Ubuntu client using CIFS to connect to a Synology NAS.  It is really more of a question for Synology support.  

You can scan the synology using nmap to get the CIFS version they are using.  The command would be:
```
sudo nmap --script smb-protocols 192.168.22.22
```
Obviously, change the IP address to point at your synology static IP.

---

