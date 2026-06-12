---
title: "Problems accessing samba share on Slackware server"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by toothandnail on 2016-06-07
Thought I had this fixed, but....

I have a desktop machine running Xubuntu, and a small Slackware-based server. The desktop machine also runs Win7, so I'm using Samba rather than NFS on the Slack box.And I've hit a very strange problem which seems to be unique to Xubuntu (and presumably others in the Ubuntu family.

smb.conf has the share set as below:

```
[files]
comment = Samba file area
path = /var/files
read only = no
writeable = yes
browseable = yes
create mask = 0775
force create mode = 0664
directory mask = 0775
force directory mode = 0775
```

The user has a valid login to the Slackware server, and is also in the samba password file. If I use Thunar, I can access the share and copy files to it. However, because the backup is scripted, I need to use a mount command to make the share available to the script. I'm using this:

```
sudo mount -t cifs //<ip-address>/files /mnt/smb -o user=xxxx,passwrd=yyyy
```

That command mounts the share without problems. I can copy files to it, but, I cannot run the backup script (which uses rsync). Equally, if I use touch to create a zero length file on the share, I get a permission denied error, but the file is created. If I then attempt to edit the zero length file, as soon as I try to save the file, I get permission denied again, and the save fails. If I then want to delete the zero-length file, I get a prompt from rm "do you want to delete xxx write protected file". I can delete it, but I always get the prompt, even though rm is not set to be interactive.

What is **really** confusing is that I only have this problem under Xubuntu. If I try the same things using my laptop (which has Arch Linux, Sparky Linux and Xubuntu 14.04 and 16.04 installed), the problem only occurs when I use either Xubuntu installation. With Arch or Sparky, I can use touch, I can edit a file and save it and I can run rsync against the share without any errors.

So, what is different about the Ubuntu version of cifs-utils? I can see nothing in the share permissions or ownership that should cause the problem, and I've pretty well run out of things to try to fix it. Help?

Paul.

---

