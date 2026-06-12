---
title: "scp / sftp umask"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by ew1 on 2008-05-20
I am trying to set the umask for any scp or sftp transactions on hardy heron. I am trying to set it to 002 so multiple users can edit the same file.  I have read the forums and created a Subsystem wrapper in the sshd_config file to set it and that did not work.  It does not appear that the .profile gets read on only a scp or sftp transactions.  Has anyone had any luck successfully implementing this.
Thanks for your time

---

### Post by itobenon on 2008-08-27
I have the same problem, and am curious to know if a solution has ever been found for this...

further; this seems to be a VERY LONG standing bug...
anyone know why it has not been corrected yet?

TIA

---

### Post by fozzyuw on 2009-04-03
I have not found a solution and I even started a similar thread, now coming across this one.

[http://ubuntuforums.org/showthread.php?p=6966063#post6966063]("http://ubuntuforums.org/showthread.php?p=6966063#post6966063")

I'm far too much of a Linux newbie to figure this out.  It's getting to the point that I might have to go back to Windows because I can't seem to get something as simple as an sFTP server setup with one user account (an admin account) the ability to delete other users files because I can't get group write permissions to be set on uploaded files. :shock:

---

### Post by CyberMando on 2009-04-03
Ssh, scp and sftp will honor umask set in .bashrc, but not in .bash_profile or .profile or .login. They also will not open permissions but willreduce them if the umask calls for it.

---

### Post by kelt65 on 2011-12-19
> **CyberMando said:**
> Ssh, scp and sftp will honor umask set in .bashrc, but not in .bash_profile or .profile or .login. They also will not open permissions but willreduce them if the umask calls for it.

Well, for the openssh (OpenSSH_5.3p1 Debian-3ubuntu7) that comes with Ubuntu 10.04LTS none of the above is true.

I've tried (in the sshd_config on the target machine) all the following with no success for scp and sftp:

ForceCommand /usr/local/bin/umask-wrapper
  - Sets the umask and runs the original ssh command. Doesn't do anything

Subsystem sftp /bin/sh -c 'umask 0002; /usr/lib/openssh/sftp-server'
  - Doesn't do anything

I've also tried pam_umask and setting the following in /etc/pam.d/ssh:
session    optional     pam_umask.so umask=0002
  - Doesn't do anything

These solutions seem to be working for others but not here. I'm trying to figure out if my config is clobbering these settings somehow but I'm not seeing it ...:(

---

### Post by njcheng on 2012-03-28
I'm having the exact same problem.  No matter what I add to the following files seems to make any difference for sftp via any client I use or scp, yet the umask works properly in the shell:
/etc/pam.d/common-session
/etc/pam.d/common-session-noninteractive
/etc/pam.d/sshd

Can anyone explain more conceptually what's going on here?  Is the sftp client responsible for setting/obeying umask or is that something that can be set on the server?  Is there any way to force all clients to obey both the setgid and umask settings?

---

### Post by Iowan on 2012-03-28
From the Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

