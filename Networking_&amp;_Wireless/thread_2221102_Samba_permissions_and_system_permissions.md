---
title: "Samba permissions and system permissions"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by kody on 2014-04-30
Hi there,

I'm running Ubuntu 13.10 as a samba file server on our windows PC network.

I'm having an issue where my directory mask = 0775, but my directory permissions stay as drwxr-xr-x.

I assume that it's now allowing the group write permission because of some system level permission, but I have no idea where to set that.

Can anyone help? I'm sure this must be posted somewhere else, but I can't find exactly what I'm looking for with the search terms I've used. 

Thanks in advance!
-Kody

---

### Post by bab1 on 2014-04-30
> **kody said:**
> Hi there,

I'm running Ubuntu 13.10 as a samba file server on our windows PC network.

I'm having an issue where my directory mask = 0775, but my directory permissions stay as drwxr-xr-x.

I assume that it's now allowing the group write permission because of some system level permission, but I have no idea where to set that.

Can anyone help? I'm sure this must be posted somewhere else, but I can't find exactly what I'm looking for with the search terms I've used. 

Thanks in advance!
-Kody
It is a bug.  See [here]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686") for the answer.  look at the posts around #23.

The bottom line is you install **[COLOR="#FF0000"]upstart 1.11-0ubuntu1[/COLOR]** from Trusty (14.04)

   1.  Download latest published package for your architecture:
   [https://launchpad.net/ubuntu/trusty/+package/upstart]("https://launchpad.net/ubuntu/trusty/+package/upstart")
    2. Install with:
```
    sudo dpkg -i upstart_1.11-*.deb
```

   .3. Reboot.

---

### Post by kody on 2014-04-30
Gah, still doesn't work. Updated to upstart_1.12, but directories are still created without the group w.

Anything else look off in my Samba.conf?

[global]
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
security = user
encrypt passwords = true
obey pam restrictions = yes
unix password sync = yes
passwd program = passwd %u
passwd chat = *New\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
	map to guest = bad user
	usershare allow guests = yes

[EngShares]
path = /srv/samba/eng
comment = Engineering File Server Share
valid users = @engineering
write list = @engineering
directory mask = 0775
create mode = 0660
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no
force group = engineering

---

### Post by bab1 on 2014-05-01
> **kody said:**
> Gah, still doesn't work. Updated to upstart_1.12, but directories are still created without the group w.

Anything else look off in my Samba.conf?

```
[global]
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
security = user
encrypt passwords = true
obey pam restrictions = yes
unix password sync = yes
passwd program = passwd %u
passwd chat = *New\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
	map to guest = bad user
	usershare allow guests = yes

[EngShares]
path = /srv/samba/eng
comment = Engineering File Server Share
valid users = @engineering
write list = @engineering
directory mask = 0775
create mode = 0660
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no
force group = engineering
```
I think you need to determine how the file or directory is being create.  The umask is always the last umask stated.  in other words, the default is the starting point.  It may not be what is applied at creation time.  A remote Windows host user may not create the file the same way as a remote Linux host user.  A local Linux user using a GUI interface can be different from the CLI user,

I always set group inheritance at the root directory of the share.  If /srv/samba/data is the directory shared then I would use chmod to set 2775 on that directory.  Then I would set the ownership to the user:group I wanted.

This is a typical group managed public share on one of my Samba servers```

[public]
        comment = Shared Data
        path = /srv/public
        browseable = yes
        guest ok = yes

        force group = users
        writeable = yes

        create mask = 0664
       directory mode = 2775


```...Note that the group is ***users *** and it is the only thing that is of importance.  I am using Ubuntu 12.04 myself but I have used the patch on other Ubuntu 13.10 machines and it works fine.  The umask should be 0002 which provides the default 775 for directories and 664 for files.

I would test each method to see which user (Windows or Linux) is actually causing the problems.  If you need to you may need to use xattr and Windows ACL's to accomplish your goals.  I don't use Windows or POSIX ACL's myself. 

One last thing; 99% of the time the smb.conf defaults are correct.  I would change only the workgroup and if needed the netbios name and name resolution order.  Then add the share definition at the bottom.

---

