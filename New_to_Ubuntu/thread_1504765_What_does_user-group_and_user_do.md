---
title: "What does user-group and user do?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-06-08
What is the difference between user-group and user, what do they do? When should I use user-group?

---

### Post by Gone fishing on 2010-06-08
It to do with permissions for example Tsepo is a teacher. 

Only he is given rights to read, write and create files in his home folder. 

As a teacher he has rights to create files in the "for students" folder which is in the teacher group, students can read this folder but not write to it.

---

### Post by germanix on 2010-06-08
Tsepo is a very clever teacher. He knows how to use Ubuntu correctly. Thank you Tsepo for teaching us to. :lolflag:

---

### Post by doas777 on 2010-06-08
an example:
I have several users that are members of a group called 'users', they have read/exec rights on my samba shares, so they can get to files. I however want to be able to write to these folders, so the samba folders are owned by 'doas777:users'. that way they can get to them, and I can edit them. I also use setGID to force all the files created there to be owned by group 'users', and have a umask set up to force the permissions. 

hth

---

### Post by Backharlow on 2010-06-08
Every file and directory has permissions, which is like a setting for who has what access to that file. Permissions are displayed as a three digit number; first number is the user second is group third is world (everyone).
If the permission is... 777
7 means read and write and execute are allowed.
so 777 is user = 7, group = 7, world = 7
user can read/write/execute,
group can read/write/execute
everyone can read/write/execute
Now, I just did in terminal:
#: stat somefile
the output is:
  File: `test-sekuli3.py'
  Size: 186       	Blocks: 8          IO Block: 4096   regular file
Device: 802h/2050d	Inode: 1212680     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/  daniel)   Gid: ( 1000/  daniel)
Access: 2010-06-05 10:25:11.000000000 -0500
Modify: 2010-06-05 10:18:18.000000000 -0500
Change: 2010-06-05 10:18:18.000000000 -0500

Now, under access it says (0644/-rw-r--r--).
So instead of 777 this one is 644, or in other words -rw-r--r--.
This means
user can rw (read and write but no execute) which is 6
group can just r (read, no write, no execute) which is 4
world can just r (read, no write, no execute) which is 4

in nautilus, you only get the -rw-r--r-- way of displaying permissions, I guess because the number way is harder to remember.
now back up...
the user has read and write for this file. I am the user. 
Uid: ( 1000/  daniel)
that means I can read and write and any application that runs under my account can also read and write that file because it has my permission.
if they are in the group daniel, they can read the file but not write.
everyone else on the computer can only read the file, but not change it, because world setting is set to read.
you might set world to no read, no write, no execute. then, only the user and group settings allow any access.
chmod changes the permissions on a file
chown changes the owner (user) on a file
chgrp changes the group on a file
or you can use nautilus > properties


don't be afraid to use the Ubuntu Help viewer.
gnome menu > System > Help and Support
It is actually quite complete and easy to understand.
Under Advanced topics > Users and Groups...

> Users and Groups in the Debian System
Joey Hess
Colin Watson
David Mandelberg

Copyright © 2001, 2002, 2003, 2004, 2005, 2007 Joey Hess, Colin Watson, David Mandelberg

This document is free; you can redistribute it and/or modify it under the terms of version 2 of the GNU General Public License as published by the Free Software Foundation.

This document is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this document; if not, write to the Free Software Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA.

Table of Contents
1. Introduction
2. Users and Groups

Chapter 1. Introduction

The Debian base-passwd package contains the master versions of /etc/passwd and /etc/group. The update-passwd tool keeps the entries in these master files in sync on all Debian systems. They comprise only "global static" ids: that is, those which are reserved globally for the benefit of packages which need to include files owned by those users or groups, or need the ids compiled into binaries. Since this reservation is a serious restriction, these ids must be allocated by the base-passwd maintainer on request. In general, packages should avoid requesting such ids where possible and instead allocate system users or groups dynamically. See Debian Policy for further details.

The Debian Policy Manual reserves ranges for these global static users and groups, but it makes no attempt to allocate individual numbers or define their purposes. This document fills that gap by describing the purposes of the individual entries in these master files.

This is a work in progress. Items in need of feedback are marked with the "HELP" tag. Please send mail to <base-passwd@packages.debian.org> or file a bug with the Debian bug tracking system if you have more information.
Chapter 2. Users and Groups

Many users have a corresponding group, and these pairs will be treated together.

root

    Root is (typically) the superuser. 
daemon

    Some unprivileged daemons that need to be able to write to some files on disk run as daemon.daemon (portmap, atd, lambdamoo, mon, and others). Daemons that don't need to own any files sometimes run as nobody.nogroup instead; it is generally better practice to use a dedicated user, and more complex or security-conscious daemons certainly do this. The daemon user is also handy for locally installed daemons, probably.

    LSB 1.3 lists daemon as legacy, and says: "The 'daemon' UID/GID was used as an unprivileged UID/GID for daemons to execute under in order to limit their access to the system. Generally daemons should now run under individual UID/GIDs in order to further partition daemons from one another." 
bin

    HELP: No files on my system are owned by user or group bin. What good are they? Historically they were probably the owners of binaries in /bin? It is not mentioned in the FHS, Debian Policy, or the changelogs of base-passwd or base-files.

    LSB 1.3 lists bin as legacy, and says: "The 'bin' UID/GID is included for compatibility with legacy applications. New applications should no longer use the 'bin' UID/GID." 
sys

    HELP: As with bin, except I don't even know what it was good for historically.

    I'm told that /var/spool/cups is owned by group sys, dunno why. 
sync

    The shell of user sync is /bin/sync. Thus, if its password is set to something easy to guess (such as ""), anyone can sync the system at the console even if they have no account on the system. 
games

    Many games are sgid to games so they can write their high score files. This is explained in Debian Policy. 
man

    The man program (sometimes) runs as user man, so it can write cat pages to /var/cache/man and update its databases there. 
lp

    The lp* devices are writable by this group so that users in it can access the parallel ports directly. Traditionally this job is taken by a printer daemon instead which will only need to run in this group.

    The lpr system keeps its spool directories owned by lp/lp. Its daemon and frontend tools (through setuid) run as user root.

    HELP: what do other print systems (rlpr, lprng, ...) do? 
mail

    Mailboxes in /var/mail are owned and writable by group mail, as is explained in Debian Policy. The user and group is used for other purposes as well by various MTAs and MUAs. 
news

    Various news servers and other associated programs (such as suck) use user and group news in various ways. Files in the news spool are often owned by user and group news. Programs such as inews that can be used to post news are typically sgid news. 
uucp

    The uucp user and group is used by the UUCP subsystem. It owns spool and configuration files. Users in the uucp group may run uucico. 
proxy

    Like daemon, this user and group is used by some daemons (specifically, proxy daemons) that don't have dedicated user ids and that need to own files. For example, group proxy is used by pdnsd, and squid runs as user proxy. 
majordom

    Majordomo has a statically allocated uid on Debian systems for historical reasons. It is not installed on new systems. 
postgres

    Postgresql databases are owned by this user and group. 
www-data

    Some web servers run as www-data. Web content should not be owned by this user, or a compromised web server would be able to rewrite a web site. Data written out by web servers will be owned by www-data. 
backup

    Presumably so backup/restore responsibilities can be locally delegated to someone without full root permissions?

    HELP: Is that right? Amanda reportedly uses this, details? 
operator

    Historically, the operator user account was used by system operators with low privilege to dump filesystem backups to tape, and was in the root group so that it could do this. In Debian, the use of a utility such as sudo to gain privilege is preferred over such highly-special-purpose accounts, and the operator user is no longer created by default. It had uid 37.

    The operator group is used by dump -n to notify logged-in operators via wall when it requires operator attention. This is a historical use, and new applications should not behave this way. (If nothing else, the group should be configurable.) 
list

    Mailing list archives and data are owned by this user and group. Some mailing list programs may run as this user as well. 
irc

    Used by IRC daemons. A statically allocated user is needed only because of a bug in ircd: it setuid()s itself to a compiled-in user id on startup. 
gnats

    HELP: Evidently used by gnats. And it needs a static set why? 
nobody, nogroup

    Daemons that need not own any files sometimes run as user nobody and group nogroup, although using a dedicated user is far preferable. Thus, no files on a system should be owned by this user or group.

    (Technically speaking, it does no harm for a file to be owned by group nogroup as long as the ownership confers no additional privileges, that is if the group and other permission bits are equal. However, this is sloppy practice and should be avoided.)

    If root-squashing is in use over NFS, root access from the client is performed as user nobody on the server. 
messagebus

    The dbus daemon (dbus-daemon-1) runs as this user and group. 
postfix

    Used by the postfix MTA. 
haldaemon

    Used by the hardware abstraction layer (hal). 
gdm

    GDM (GNOME Display Manager) runs as this user/group. 
saned

    Added by sane-utils, but appear to be unused. 
klog

    Used by klogd, the kernel logger.

syslog

    Used by syslog, the general purpose logger. 

Other groups have no associated user.

adm

    Group adm is used for system monitoring tasks. Members of this group can read many log files in /var/log, and can use xconsole.

    Historically, /var/log was /usr/adm (and later /var/adm), thus the name of the group.

    HELP: Perhaps policy should state the purpose of this group so users may be safely added to it, in certainty that all they'll be able to do is read logs. Wouldn't hurt to rename it 'log' either ... 
tty

    Tty devices and /dev/vcs* are owned by this group. This is used by write and wall to enable them to write to other people's ttys. 
disk

    Raw access to disks. Mostly equivalent to root access.

    HELP: Well, I have some disk devices in /dev owned by the group, but I can't see the point. On another system, I noticed that some of the files lilo puts in /boot are also owned by disk. I can imagine local uses for such a group, like if you want to give some users in the group direct access to some hard disk. But these uses I've found on my systems seem to preclude doing that easily; if I put a user in group disk here, they'd have write access to the root filesystem. 
kmem

    /dev/kmem and similar files are readable by this group. This is mostly a BSD relic, but any programs that need direct read access to the system's memory can thus be made setgid kmem. 
dialout

    Full and direct access to serial ports. Members of this group can reconfigure the modem, dial anywhere, etc. 
dip

    The group's name stands for "Dialup IP". Being in group dip allows you to use tools such as pppd, pon, and poff to make dialup connections to other systems using predefined configuration file(s) in the /etc/ppp/peers directory. 
fax

    Allows members to use fax software to send or receive faxes. 
voice

    Voicemail, useful for systems that use modems as answering machines. 
cdrom

    This group can be used locally to give a set of users access to a CD-ROM drive. 
floppy

    This group can be used locally to give a set of users access to a floppy drive. 
tape

    This group can be used locally to give a set of users access to a tape drive. 
sudo

    Members of this group do not need to type their password when using sudo. See /usr/share/doc/sudo/OPTIONS. 
audio

    This group can be used locally to give a set of users access to an audio device. 
src

    This group owns source code, including files in /usr/src. It can be used locally to give a user the ability to manage system source code.

    HELP: /usr/src is owned by group src and is setgid. This doesn't make files put there by foo-src packages necessarily be owned by group src though. If the intent is to make group src be able to manage source code, perhaps policy should say that foo-src packages make files in /usr/src owned and writable by the group (and files in tarballs dropped there likewise)? 
shadow

    /etc/shadow is readable by this group. Some programs that need to be able to access the file are setgid shadow. 
utmp

    This group can write to /var/run/utmp, /var/log/wtmp, /var/log/lastlog, and similar files. Programs that need to be able to write to them (such as X terminal emulators) are setgid utmp. 
video

    This group can be used locally to give a set of users access to a video device. 
plugdev

    Members of this group can access removable devices in limited ways without explicit configuration in /etc/fstab. This is useful for local users who expect to be able to insert and use CDs, USB drives, and so on.

    Since pmount (the original implementor of group plugdev) always mounts with the nodev and nosuid options and applies other checks, this group is not intended to be root-equivalent in the ways that the ability to mount filesystems might ordinarily allow. Implementors of semantics involving this group should be careful not to allow root-equivalence. 
staff

    Allows users to add local modifications to the system (/usr/local, /home) without needing root privileges. Compare with group 'adm', which is more related to monitoring/security.

    Note that the ability to modify /usr/local is effectively equivalent to root access (since /usr/local is intentionally on search paths ahead of /usr), and so you should only add trusted users to this group. Be careful in environments using NFS since acquiring another non-root user's privileges is often easier in such environments. 
users

    While Debian systems use the user-group system by default (each user has their own group), some prefer to use a more traditional group system. In that system, each user is a member of the 'users' group. 
lpadmin

    Allows a user to add, modify, and remove printers from foomatic, cups, and possibly other printer databases. 
sasl

    Users in this group have read/write access to /etc/sasldb and/or /etc/sasldb2, wich are used to authentication with sasl. This is commonly used by IMAP, POP, and SMTP servers for authentication. 
scanner

    Users in this group can use scanner(s). 
ssh

    ssh-agent is setgid to ssh in order to prevent ptrace attacks. 

Some users have no corresponding group.

sshd

    Unprivileged user used by the privilege-separated sshd when communicating with the network before successful authentication. 
fetchmail

    Used by the fetchmail program. 
cupsys

    CUPS (Common Un*x Printing System) runs as this user. It is in group lp, so it can access printer devices. 

---

### Post by SpinningAround on 2010-06-08
Thanks is a little clearer now, will read through the section in help.

---

