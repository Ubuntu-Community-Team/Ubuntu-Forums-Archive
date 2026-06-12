---
title: "Working on Setting up an SFTP Server"
date: 2014-04-01
forum: Networking &amp; Wireless
---

### Post by Brent_Wassell on 2014-04-01
I just setup Ubuntu 12.04 Server LTS on an ESXi host. The sole purpose of this VM is to act as an SFTP server.  I'm wondering the best way/guide to set this up?  Ideally I could have a list of users and passwords, and each user would only have access to a particular folder.

Also, the storage for this VM will need to be accessible from Windows machines on the network, so I'm pretty sure I'll need to setup Samba or some other means of configuration.

Any guides/advice/questions would be awesome!

Good to be back on the forums (other than losing my post count).

---

### Post by Lars Noodén on 2014-04-01
You're probably looking for chrooted SFTP.  There are lots of tutorials, good and bad ones, out there about what to add in sshd_config.  Write here if you have questions on them but it's only a few steps.  

About remote access from legacy systems, you can use WinSCP, FileZilla or maybe SSHFS.  Those all support SFTP so the connection will be secure.

---

### Post by Brent_Wassell on 2014-04-01
Is Chroot a "secure way" of doing things for non sudoers?  Let's say I have 3 users with their own folder and their own file of README-User1.txt

User 1's chroot actual path = /home/chroot/user1 (contains README-User1.txt)


User 2's chroot actual path = /home/chroot/user2 (contains README-User2.txt)


User 3's chroot actual path = /home/chroot/user3 (contains README-User3.txt)


If user 3 connects and runs LS, they would only see README-User3.txt, corrrect?  If they tried to CD to a different directory or search somewhere else, they wouldn't be able to, correct?

---

### Post by Lars Noodén on 2014-04-02
Chroot will lock designated users, sudo or not, into a subdirectory out of which they cannot ascend.  They can still descend into sub-subdirectories and so one, if the permissions allow them to.  So depending on where you chroot them to, they cannot read other people's files.

The only trick with SFTP's built-in chroot is that the target directory must be owned by root and not writable by anyone else.  That means the permissions and or layout have to be adjusted a little to make the plan fit in that constraint.

---

### Post by Brent_Wassell on 2014-04-03
I made a directory /sftp

In that folder I have /sftp/user1 /sftp/user2 etc

I have the chroot set for those users so when I establish an sftp connection it lands them in their folder only - that is working just fine.  I disabled SSH access so the users have no shell.

Here's the problem:

I want to setup a Samba share for /sftp so that I can access all of the data from a windows machine in my company. I have the following in /etc/samba/smb.conf
[ShareName]
path = /sftp
available = yes
valid users = svradmin
read only = no
browseable = yes
public = no
writeable = yes

After restarting smbd, I can see the shares and copy existing files out of the share from a Windows machine - but I can't edit/delete/add files through the SMB share.  Also, since adding that as a share it seems to have somehow broken SFTP access for my test users...

---

### Post by Lars Noodén on 2014-04-03
> **Brent_Wassell said:**
> 
In that folder I have /sftp/user1 /sftp/user2 etc

One other way you might reach the same folders from legacy operating systems would be WinSCP.  

The one catch with chrooted SFTP is that the chroot target has to be owned by root and not writable by anyone else.  If that is not the case then chrooted SFTP will not work.  The it's fine for the user to own or otherwise be able to write to files or subdirectories inside the chroot.  That makes it harder to plan when mixing with Samba and others.  

I am no longer that familiar with Samba, others here are, but I would check the permissions for the directories.

---

### Post by Brent_Wassell on 2014-04-03
> **Lars Noodén said:**
> One other way you might reach the same folders from legacy operating systems would be WinSCP.  

The one catch with chrooted SFTP is that the chroot target has to be owned by root and not writable by anyone else.  If that is not the case then chrooted SFTP will not work.  The it's fine for the user to own or otherwise be able to write to files or subdirectories inside the chroot.  That makes it harder to plan when mixing with Samba and others.  

I am no longer that familiar with Samba, others here are, but I would check the permissions for the directories.

Permissions for /sftp
drwxr-xr-x  4 root root  4096 Apr  3 08:42 sftp

Permissions for folders in /sftp
drwxr-xr-x 3 testuser testuser 4096 Apr  3 08:59 TestUser

I have root as the owner for /sftp - is that the issue?

---

### Post by Lars Noodén on 2014-04-03
That will work if you have /sftp as your chroot target

```

ChrootDirectory /sftp

```

If you have a different target, say this:

```

ChrootDirectory /sftp/%u

```

Then you will need these:

```

drwxr-xr-x  4 root root  4096 Apr  3 08:42 /sftp/user1/
drwxr-xr-x  4 root root  4096 Apr  3 08:42 /sftp/user2/
...

```

---

### Post by Brent_Wassell on 2014-04-03
From my **/etc/ssh/sshd_config**

Subsystem sftp internal-sftp
Match User testuser
        ChrootDirectory /sftp/TestUser
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTCPForwarding no


I set it so when testuser connects via SFTP their ChrootDirectory is /sftp/TestUser.  In order for this to work, I had to make them the owner of that folder.  If root:root is set for /sftp/testuser then it won't let me sftp as them.

Thank you for your help - it's good to get back into working with Linux Systems.

---

### Post by Lars Noodén on 2014-04-03
Strange.  That's kind of the opposite of what the manual page says and what I get when I try your settings.  If I have the directory owned by the user, I get this when trying to connect with sftp with your settings:

Write failed: Broken pipe
Couldn't read packet: Connection reset by peer

Are you reloading the SSH server configuration after making changes to sshd_config?

```

sudo service ssh restart

```

---

### Post by Brent_Wassell on 2014-04-03
I was restarting with sudo /etc/init.d/ssh restart

I changed /sftp/TestUser to be owned by root:root and I was able to SFTP in as testuser still - and upload and delete files okay!

From the SambaShare I am connecting as a user other than testuser - and I can see and copy files out of the TestUser folder, but I can't add/delete/remove files.

It seems the uploaded files are instantly owned by testuser
Example file uploaded to /sftp/TestUser by testuser
-rw-rw-r-- 1 testuser testuser 41615 Apr  3 11:07 nmap.txt

---

