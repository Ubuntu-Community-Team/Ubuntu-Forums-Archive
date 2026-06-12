---
title: "How I got gnome-user-share to work with UFW."
date: 2023-02-22
forum: Networking &amp; Wireless
---

### Post by jadaube2 on 2023-02-22
Hey everyone- I thought I’d just share how I got Ubuntu’s File Share feature to cooperate with the firewall.  I’m talking about the option to share one’s “Public” folder on the network through Settings > Sharing > File Sharing on Ubuntu 22.04.  I wanted to share files among the other Ubuntu machines on my network without the headache inherent in SAMBA. Per Ubuntu’s Desktop Guide, I could share personal files on the Public folder by installing gnome-user-share, and enabling file sharing in the settings menu as described above. Only problem is with the UFW firewall up, connections were completely blocked.  I searched all over the interwebs trying to figure out which ports needed to be open, but it was all in vain.  Finally, I used ```
sudo tail -f var/log/ufw.log
``` to see what connection was being refused.  Turns out it was port 33669, TCP protocol.  I opened it up and sure enough, I was able to access the Public folder from the other computers on my LAN.  I don’t know if gnome-user-share always uses this port, but if you’re having a similar problem, trying opening 33669. If that doesn’t work, just use “sudo tail -f var/log/ufw.log” and see what’s bouncing off your firewall.


Cheers.

---

### Post by TheFu on 2023-02-24
>  gnome-user-share uses a WebDAV server to share the Public folder, and advertises the share on the local network using mDNS. 

Yuck.  WebDAV has had lots and lots of security failures.  This solution being stuck with WebDAV will have performance issues too.
There are better, faster, and more secure, options.
The Linux options are:
[LIST]
[*]NFS
[*]SFTP
[*]sshfs
[/LIST]

NFS should be the "go to" answer for LAN storage access when both systems are on the same relatively secure network.  This is server-to-server file sharing over the network and 99.9% of applications wouldn't know the difference between local storage and NFS.  All Unix file permissions are supported. chmod, chown work.  When an admin sets up NFS, all users of the system automatically gain access, based on Unix permissions, to the storage.  This is unlike CIFS.  Once an NFS mount is created by the admin, it can be accessed by any program/level - file managers, whatever.  Where ever the storage is mounted is where it will be found.  There's no extra "drive letter" in MSFT-speak, for the NFS storage. It appears as it is local.  NFSv3 security is basically provided by static IPs between the 2 systems, though the NFS server is the only one that NEEDS a static IP, clients can be mDNS or DNS or straight IP known to the server.  For more security, NFSv4 added Kerberos server-to-server keys and strong encryption. Kerberos is a hassle.

sftp is based on ssh, ssh credentials and security. It shares the same port as ssh.  Every Linux file manager seems to support sftp://, so if you install ssh on both systems and use a file manager, you'll have direct access to storage based on your ssh permissions.  
Install ssh:   **sudo apt install ssh fail2ban**
Try a URL like: **sftp://192.168.x.x/Public** in your file manager, you should see a login prompt to get access.  DNS {bobs-computer} and mDNS names {bobs-computer.local} can be used instead of the IP address, if those are setup.
If you have setup ssh-keys between the client and server, then it is possible to not get prompted for credentials, since all ssh-based tools honor ssh-keys automatically.  Same for ~/.ssh/config settings to make life easier.  BTW, some file managers don't use 'sftp://' in the URL, they have a different keyword, but it is the same.

sshfs is also based on ssh, credentials and security.  It is a way for user-to-server mounts that are under control of users.  It mostly supports Unix permissions.  With modern CPUs and AES encryption, performance is quite good.  ssh-keys work. Same for ~/.ssh/config settings to make life easier.
```
mkdir ~/bobs-computer   # create an empty directory to use as a "mount point"
sshfs bobs-computer:~/Public    ~/bobs-computer   # that will mount the remote storage for the userid on bobs-computer (that would be the $HOME/Public directory).
```
When done, umount with **sudo umount ~/bobs-computer ** or **fusermount -u ~/bobs-computer**

Anyway, other options that are better than WebDAV.  Everyone who has used WebDAV knows how poor the performance is.
For Gnome users, [https://help.gnome.org/users/gnome-help/stable/nautilus-connect.html.en](https://help.gnome.org/users/gnome-help/stable/nautilus-connect.html.en) spells out how to use Nautilus to access multiple different remote file options, including nfs, ssh, sftp.  The other options really shouldn't be used, IMHO.

---

### Post by jadaube2 on 2023-03-06
Just an update - it turns out that the port used by gnome-user-share is dynamic and changes every reboot. See, for example, [HTML]https://bugzilla.redhat.com/show_bug.cgi?id=179187[/HTML] .  No one seems to have found a solution for continuously opening up the firewall for that specific service, so I simply reserved IP addresses on my LAN for the Ubuntu machines, and opened up the firewall to them , while leaving it closed to the stuff I don't trust (i.e. android tables, ring doorbell, etc.).

---

### Post by TheFu on 2023-03-06
Internet?  gnome-user-share is scary to open to the internet. Just use something based on ssh with ssh-keys, never passwords if it is going to be available over the internet.  Then the port is 100% under your control and you can have your router do port translation for a little more security.

---

