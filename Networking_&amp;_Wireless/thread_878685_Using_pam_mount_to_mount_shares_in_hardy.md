---
title: "Using pam_mount to mount shares in hardy"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by tanveer on 2008-08-03
Hi all,
I have joined a hardy machine with windows 2003 AD using likewise Open and login with AD credentials. Now to mount network home folder of users I installed libpam-mount and that created /etc/security/pam_mount.conf.xml.

Now I added the line below

[PHP]
.......
<!-- mntcheck utility for BSDs which lack /etc/mtab -->
<mntcheck>mount</mntcheck>

<pmvarrun>pmvarrun -u %(USER) -o %(OPERATION)</pmvarrun>


<volume options="uid=%(USER),gid=root,dir_mode=0700,nosuid,nodev" user="*" fsype="cifs" server="fs1" path="users" mountpoint="/home/local/DOMAINANME/AD_username/mountfolder_name" />


<!--
Volumes that will be mounted when user triggers the pam_mount module
(usually at login).

    <volume
        user="*" | pgrp="foo" | sgrp="bar"
        invert="1"
      ..........

[/PHP]

Below are my pam.d location files
[PHP]
mod@lab1:/etc/pam.d$ ls
atd   common-account                  common-auth.lwidentity.orig  common-password.lwidentity.orig  cron    gdm-autologin      other   ppp    su
chfn  common-account.lwidentity.orig  common-pammount              common-session                   cupsys  gnome-screensaver  passwd  samba  sudo
chsh  common-auth                     common-password              common-session.lwidentity.orig   gdm     login              polkit  sshd
mod@lab1:/etc/pam.d$ cat common-account.lwidentity.orig 
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account required        pam_unix.so
account requisite       pam_krb5.so ignore_root
mod@lab1:/etc/pam.d$ cat common-auth.lwidentity.orig 
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    requisite       pam_unix.so nullok_secure
auth    optional        pam_smbpass.so migrate
auth    optional        pam_mount.so use_first_pass
mod@lab1:/etc/pam.d$ cat common-account.lwidentity.orig 
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account required        pam_unix.so
account requisite       pam_krb5.so ignore_root
mod@lab1:/etc/pam.d$ cat common-password.lwidentity.orig 
password   sufficient   pam_unix.so nullok obscure md5 min=4 max=8
password   requisite    pam_krb5.so ignore_root
mod@lab1:/etc/pam.d$ cat common-session.lwidentity.orig 
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session required        pam_unix.so
session sufficient      pam_localuser.so
session optional        pam_mount.so
mod@lab1:/etc/pam.d$ 

[/PHP]
But it doesn't work at all. Any help what is going wrong or is the  syntax is wrong.
Thanks in advance

---

### Post by trainerbill on 2008-09-05
your problem is in common-session.  You can't have any sufficients before the pam_mount.  Also in your common-auth I am not seeing any likewise open entries so I doubt you are even able to authenticate via likewise.  I could be wrong there.  If I were you I would unjoin the box, purge likewise-open, reinstall likewise open and set your pam files to something similar to this

/etc/pam.d/common-auth

auth    sufficient      pam_unix.so nullok_secure
auth    required        /lib/security/pam_lwidentity.so try_first_pass
auth    optional        pam_mount.so try_first_pass
auth    optional        pam_smbpass.so migrate missingok


/etc/pam.d/common-session

session optional        pam_unix.so
session optional        /lib/security/pam_lwidentity.so try_first_pass
session optional        pam_mount.so try_first_pass

This is how I have it setup and it authenticates via likewise and mounts my home folder that is located on a file share.

If you want a quick fix you could try editing your common-session file to look like this

session required        pam_unix.so
session optional        pam_mount.so 
session sufficient      pam_localuser.so

That might work but no guarantees.

Good Luck

---

### Post by maunir on 2008-10-21
I'm getting this error while trying to mount one of my shares.  Any help would be appreciated.

Oct 21 09:29:18 kei-lxtest sudo: pam_unix(sudo:session): session opened for user root by mshah(uid=0)
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(rdconf1.c:554) path to luserconf set to /root/.pam_mount.conf.xml 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:460) Entered pam_mount session stage 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:481) back from global readconfig 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:485) going to readconfig user 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(rdconf1.c:697) volume wildcards ignored for "root" and uid0 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:490) back from user readconfig 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:495) no volumes to mount 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:548) done opening session (ret=0) 
Oct 21 09:29:18 kei-lxtest sudo: pam_unix(sudo:session): session closed for user root
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:589) received order to close things 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:591) No volumes to umount 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:635) pam_mount execution complete 
Oct 21 09:29:18 kei-lxtest sudo: pam_mount(pam_mount.c:116) Clean global config (1073741824)

---

### Post by maunir on 2008-10-21
Installed smbfs package and it worked.  No authentication and automatic login.

---

### Post by tensop on 2008-12-09
> **maunir said:**
> Installed smbfs package and it worked.  No authentication and automatic login.

Bump.

I'm trying to get the exact same thing as you going but i'm having no success... i cannot even see any messages from pam anywhere in any log file or console output

could you list your exact method if possible?

---

