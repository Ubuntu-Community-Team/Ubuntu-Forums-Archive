---
title: "mount drives in linux"
date: 2015-07-27
forum: Networking &amp; Wireless
---

### Post by pradeep15 on 2015-07-27
Hi,


Is there any way to mount sharepoint link into *nix machine. 


Example: 


I have windows sharepoint portal and a linux device.


linux device is having lot zip files and it needs to be transferred to sharepoint portal. Is there anyway to map sharepoint portal link in *nix machine. I can map drive that sharepoint link into my windows computer.


Is it possible? All help will be greatly appreciated.


Regards,
Pradeep

---

### Post by TheFu on 2015-07-27
Linux can mount NFS shares.
Linux can mount CIFS shares.
Linux can mount certain block devices - like iSCSI and AoE. Other SAN protocols are supported too.
Linux can mount storage over ssh using sshfs.
Many of [these file systems]("https://en.wikipedia.org/wiki/List_of_file_systems#Distributed_file_systems") can be mounted from a Linux machine too. The list is extensive.

So - the question is does Sharepoint support any of those? That is a question for Microsoft support, perhaps?

---

### Post by pradeep15 on 2015-07-28
If its NFS how it can be achieved.

---

### Post by Bucky Ball on 2015-07-28
Take a look at some of the links [here]("https://duckduckgo.com/?q=mount+nfs+ubuntu") and see if you can come up with some clues. Let us know and provide a link if you have questions or run in to trouble. Good luck. :)

---

### Post by TheFu on 2015-07-28
> **pradeep15 said:**
> If its NFS how it can be achieved.

There are many different sorts of NFS mounts.  So the answer is "it depends."
I'm 99.9999% certain that Sharepoint does NOT support NFS.  The back-end storage to which Sharepoint connects, may.

I did a websearch for "*nfs ubuntu*" and found these:
* [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
* [https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)
* [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-14-04)
* [https://www.howtoforge.com/nfs-server-on-ubuntu-14.10](https://www.howtoforge.com/nfs-server-on-ubuntu-14.10)
and those are just the 1st four results.  These are reputable sources.  

If you need more details, make the query "ubuntu nfs server guide" and look for "serverguide" in the URL.
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html) - there you go - official, Ubuntu, instructions for a trivial example.

---

### Post by pradeep15 on 2015-07-28
Thanks all, checking all the links.

---

### Post by pradeep15 on 2015-07-30
Hi All,

It looks like I need to install NFS package where i wouldnt get permission. Initially I assumed it would be easy to do it without installing any additional packages. I think i will drop this plan unless there is something which can be done easily.

Thanks for all the help. I was able to get some knowledge out of those links mentioned above.

Regards,
Pradeep

---

### Post by Bucky Ball on 2015-07-30
If you are going to drop the plan, we don't have a 'resolved' tag, but we do have a solved one. Please see the first link in my signature to help others. This will not close the thread to further discussion. :)

---

### Post by SeijiSensei on 2015-07-30
A quick Google search for "mount sharepoint linux" indicates this can be done by installing davfs.  I found **davfs2** in the Ubuntu repositories.  See, among others, [http://www.unix.com/emergency-unix-and-linux-support/235563-adding-permanent-mount-davfs2.html](http://www.unix.com/emergency-unix-and-linux-support/235563-adding-permanent-mount-davfs2.html).

Apparently Sharepoint is essentially nothing more than a [WebDAV](http://www.webdav.org/) server.

---

### Post by pradeep15 on 2015-08-04
ok I tried and i got this error. not so sure where should i give permission. mnt/folder3 is on R+w+x priv.

mount -t cifs //sharepoint.mycompany.com/folder1/folder2/folder3   /mnt/folder3 -o username=domain\username
Password:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

