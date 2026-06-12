---
title: "Sharing files between linux boxes"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by persev on 2007-09-27
Searching has yielded no helpful advice. I have used Ubuntu since 5.10 and now have Feisty installed on 1 desktop and 2 laptops all connect through a wireless router with just wep incryption. Most everything works great but file sharing. I set up a couple of folders on each box to enable me to share family pics so I don't have to upload from the camera's to each box. I would like to be able to upload/download from any of my boxes. I can see all boxes on the network when I go to Places>Network but when I click on one of the boxes I get an error message "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: xyz-laptop"." and nothing shows up if I share a folder with NFS.
ANY help would be greatly appreciated AND allow me to impress my wife with my linux skills (she doesn't like linux but isn't willing to fix windows herself when it breaks).

---

### Post by notwen on 2007-09-27
I would go strictly w/ NFS.  I use NFS to share files and stream media from my file server to multiple PCs and laptops.  [Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server") is a simple, yet straight-forward how-to.  Simply install the server package on the PC you're wanting to share and the client on the PCs you're wanting to access the shared folders.  Post back if you run into any issues. =]

---

### Post by persev on 2007-09-27
> **notwen said:**
> I would go strictly w/ NFS.  I use NFS to share files and stream media from my file server to multiple PCs and laptops.  [Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server") is a simple, yet straight-forward how-to.  Simply install the server package on the PC you're wanting to share and the client on the PCs you're wanting to access the shared folders.  Post back if you run into any issues. =]

Well I want to share folders between boxes, I didn't really want to deal with a full server and I would rather use Nautilus to move the files, at this point it seems that Nautilus is not usable for sharing files which makes me wonder why Network shows up at all in the menu.

---

### Post by notwen on 2007-09-27
NFS allows you to mount the shared folder on your client box so it shows up in Nautilus as if it were a local folder.  Have you attempted the procedures on ubuntuguide yet?

---

### Post by persev on 2007-09-27
> **notwen said:**
> NFS allows you to mount the shared folder on your client box so it shows up in Nautilus as if it were a local folder.  Have you attempted the procedures on ubuntuguide yet?

In the process, have my desktop done.

---

### Post by notwen on 2007-09-27
It's pretty easy, you could also have /etc/fstab automount these shared drives if you like, just be sure to add the startup service command to your startup applications on the server machine where your shared folders/files are hosted.  I have a cron job added to make sure the server is always up & running.  Then on my client PCs and laptops I've simply created a launcher giving the "mount" command for the specified shared folder.  Also pay attention to how you're mounting, since you want to actually share the folders/files you would want read/write access.  Please post back with your results or if you run into any issues. =]

---

### Post by persev on 2007-09-27
> **notwen said:**
> It's pretty easy, you could also have /etc/fstab automount these shared drives if you like, just be sure to add the startup service command to your startup applications on the server machine where your shared folders/files are hosted.  I have a cron job added to make sure the server is always up & running.  Then on my client PCs and laptops I've simply created a launcher giving the "mount" command for the specified shared folder.  Also pay attention to how you're mounting, since you want to actually share the folders/files you would want read/write access.  Please post back with your results or if you run into any issues. =]

Finished guide on "server" and "client" and it didn't work, no NFS shares are shown, just SMB shares which doesn't allow me to access the files from previously posted  error. I used the automount part of the guide. How do I add the start up service? I still don't understand why files have a share option if it doesn't work.

---

### Post by notwen on 2007-09-27
Disregard the share options of folders/files.  Did you export your new config after setting up your nfs server?

```
sudo exportfs -a
```

You simply need to create a folder on your client machines '/shared_01' for example.  Then give this command in a terminal:

```
 sudo mount 192.168.1.1:/path/to/shared/files shared_01
```

Your shared folders would then show up under /shared_01.  Make sure you use your server's intranet ip address.

This command should start your nfs server at every boot;  I forget how I got around the sudo part, I'll check once I get home:
 
```
sudo /etc/init.d/nfs-kernel-server start
```

---EDIT---

I would also recommend having your router give your server machine a static ip, this keeps you from having to change the specified ip every time you mount the shared folders.

---

### Post by persev on 2007-09-27
> **notwen said:**
> Disregard the share options of folders/files.  Did you export your new config after setting up your nfs server?

```
sudo exportfs -a
```

You simply need to create a folder on your client machines '/shared_01' for example.  Then give this command in a terminal:

```
 sudo mount 192.168.1.1:/path/to/shared/files shared_01
```

Your shared folders would then show up under /shared_01.  Make sure you use your server's intranet ip address.

This command should start your nfs server at every boot;  I forget how I got around the sudo part, I'll check once I get home:
 
```
sudo /etc/init.d/nfs-kernel-server start
```

---EDIT---

I would also recommend having your router give your server machine a static ip, this keeps you from having to change the specified ip every time you mount the shared folders.

Will try, I did find out the problem with Samba on my server/desktop smbfs has unresolved dependencies it is now working from one of my laptops.

Removed and reinstalled Samba and smbfs, getting error again. ```
 sudo mount 192.168.1.1:/path/to/shared/files shared_01
``` failed "server: Permission denied"

---

### Post by notwen on 2007-09-27
Will Windows machines be needing access to these shared folders as well?  I'm going by the thread title and only have experience w/ strictly linux to linux sharing.

---

### Post by persev on 2007-09-27
> **notwen said:**
> Will Windows machines be needing access to these shared folders as well?  I'm going by the thread title and only have experience w/ strictly linux to linux sharing.

I only use linux, I have no windows machines. Samba is the only thing that shows up in Nautilus though. Obviously NFS is for very technical people, I am just a human being. I truly don't understand why sharing folders between boxes has to be so difficult, this is frustrating and depressing.

I did find out the problem with Samba on my server/desktop smbfs has unresolved dependencies it is now working from one of my laptops.

Removed and reinstalled Samba and smbfs, getting error again.

and 

" sudo mount 192.168.1.1:/path/to/shared/files shared_01" 

with my info failed "server: Permission denied"

---

### Post by persev on 2007-09-27
Thanks for the help anyway.

---

### Post by notwen on 2007-09-27
NFS is very simple, let me know if you'd like to attempt it again. =]

---

