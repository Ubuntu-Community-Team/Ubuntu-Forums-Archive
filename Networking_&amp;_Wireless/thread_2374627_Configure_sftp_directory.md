---
title: "Configure sftp directory"
date: 2017-10-17
forum: Networking &amp; Wireless
---

### Post by thisfro on 2017-10-17
Hey guys

I'm trying to access a specific (and only this) location on my server. It's running openssh-server and root works fine.

What I already did:
- created a group foo-group
- added user foo to this group 
- accessed file system via sftp

What I want to achieve:
- Login to folder /mnt/foo
- Have permission to write on /mnt/foo

I tried to add this to the /etc/ssh/sshd_config
```

Subsystem sftp internal-sftp
Match group foo-group
             ChrootDirectory /mnt/foo
             ForceCommand internal-sftp -d /default

```

When I try to restart ssh, it throws me
```
Job for ssh.service failed because the control process exited with error code. See "systemctl status ssh.service" and "journalctl -xe" for details.
```

Which doesn't help me tho...

Any idea what went wrong?

Thx for help!

PS:
/mnt/foo is obviously not the real directory, but holds for a subdir on a mounted harddisk

---

### Post by TheFu on 2017-10-19
Welcome to the forums.

Don't know what "root works" means - On Ubuntu systems, we don't use root.

/mnt should be used only for temporary mount needs - like to copy files off storage. A rule-of-thumb is that if you need something overnight, then /mnt shouldn't be used.  Can't tell from your post if that is the situation.

You didn't mention changing any file/directory permissions - sftp honors all local permissions, unlike Samba/CIFS/SMB.   File and directory permissions are the core of all Unix security.  Best to spend the 45 minutes today, now, to learn those at a beginning level. It will prevent hours, days, weeks, months, of frustration once you understand these simple things.  I just taught about 100 students permissions 2 weeks ago.  We created 3 user accounts.  Put 2 of them into the same group, left 1 outside the group.  Then we created a few directories in /tmp/ to practice under using 3 different terminal windows.  I had them go crazy with every possible combination of permissions - that's 32-bit worth, but started with 775, 664, 711.   It really opens your eyes to see what works and what doesn't for users in and outside the group.  Spend 45 min now.  You can also search for "file permissions tutor" to get started, but that will only be the main 10 permissions. There are thousands, but they follow a clear, elegant, pattern, so _understanding_ is much more important than memorizing.

What you want is probably ```
chmod 775 /mnt/foo && chmod g+s /mnt/foo
``` - assuming the group is setup correctly on the directory and no files exist there yet.  The g+s will ensure all new files are created with the correct group, automatically.

As for the failure for a service to start, check the log files and turn up the "verbose" setting on the service to get more logging, if needed.  Using a chroot for any service is usually non-trivial, since getting all the dependent libraries included inside the chroot is important.  For the internal-sftp, that should be addressed already, making this "just work", in theory.  Often it is smart to follow the method spelled out by the daemon authors.  The openssh project didn't come up in the first pg of search results, but debian did: [https://debian-administration.org/article/590/OpenSSH_SFTP_chroot_with_ChrootDirectory](https://debian-administration.org/article/590/OpenSSH_SFTP_chroot_with_ChrootDirectory)  I see some subtle differences in the way you did it and their guide.  The Arch Wiki might be useful as well.

---

