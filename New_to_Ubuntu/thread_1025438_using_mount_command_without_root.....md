---
title: "using mount command without root...."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-12-30
I want to create a scenario where I can use the mount command in a terminal without requiring root. I do this because I want to use a script that will automatically mount a few ctfs partitions that I don't want mounted at all times, perform a few backup copies, then unmount said partitions.

I have my current script set with:
```
mount -t cifs -o username=fakeusername,password=fakepassword //192.168.1.224/80gb.wndws /media/wndws
```
to un-mount the drive, then a simple
```
umount /media/wndws
```
type of scenario.

Currently, the script works fine, however I have to open a terminal and run it as root. I would like some way of mounting these partitions (without fstab mounting them at boot) as a regular user so that I can simply execute this script as I save my documents.

---

### Post by scorp123 on 2008-12-30
You could add it to the commands that are available via "sudo". And if you don't want passwords to be asked, you could do that as well. Please see here:
[http://www.linuxquestions.org/questions/slackware-14/visudo-and-granting-access-to-mount-for-a-normal-user-522346/](http://www.linuxquestions.org/questions/slackware-14/visudo-and-granting-access-to-mount-for-a-normal-user-522346/)

---

### Post by scorp123 on 2008-12-30
Here is one "sudoers" example that uses the "NOPASSWD" option on some commands ... maybe you could use these examples and then modify them so they suit your needs (e.g. use the mount command without having to enter the password):

[https://khaidoan.wikidot.com/linux-visudo](https://khaidoan.wikidot.com/linux-visudo)

---

### Post by ushimitsudoki on 2008-12-30
You can add the "user" or "users" option to allow a user to mount an entry in /etc/fstab.

Check the [man entry for mount]("http://linux.die.net/man/8/mount") for details:
> user
    Allow an ordinary user to mount the file system. The name of the mounting user is written to mtab so that he can unmount the file system again. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line user,exec,dev,suid). 
users
    Allow every user to mount and unmount the file system. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line users,exec,dev,suid). 

---

### Post by DoubleMcLovin on 2008-12-30
> **ushimitsudoki said:**
> You can add the "user" or "users" option to allow a user to mount an entry in /etc/fstab.

Check the [man entry for mount]("http://linux.die.net/man/8/mount") for details:

This option would mount the drive at start up wouldn't it? I thought everything in fstab automatically ran at start.

I had a look at the visudo file and I think I found something that works. I'm going to reboot now and see if it works.

---

### Post by AndyCee on 2008-12-30
I know you said no mount at boot, but using the flag "noauto" in fstab it is not mounted at boot, and you can mount it as a regular user.

The sudo option is interesting. I wouldn't have thought of that one though in retrospect that's an obvious choice when changing permissions of a command.

---

### Post by DoubleMcLovin on 2008-12-30
Well, what I tried failed....

Copy of my Visudo file:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# User alias specification
User_Alias	TRUSTED = andy

# Cmnd alias specification
Cmnd_Alias	MOUNT = /sbin/mount,/sbin/umount

# Defaults specification
Defaults:TRUSTED	!lecture
Defaults:andy	!authenticate

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
TRUSTED	ALL = NOPASSWD:MOUNT

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

I read that first link that was given, and from that file I derived my changes here. I receive the error that only root can do that when I try an mount even after a reboot.

---

### Post by ByteJuggler on 2008-12-30
> **DoubleMcLovin said:**
> This option would mount the drive at start up wouldn't it? I thought everything in fstab automatically ran at start.

No, not neccesarily.  Use it in conjunction with the "noauto" option, and it wont be automatically mounted.  However, having the entry in the fstab, will allow a user to simply run:

```
mount /path/to/mount
```

or

```
mount /dev/sdxx
```

without any other options, to mount a filesystem.  All other missing details are then retrieved from the fstab.

---

### Post by DoubleMcLovin on 2008-12-30
> **AndyCee said:**
> I know you said no mount at boot, but using the flag "noauto" in fstab it is not mounted at boot, and you can mount it as a regular user.

The sudo option is interesting. I wouldn't have thought of that one though in retrospect that's an obvious choice when changing permissions of a command.

I suppose this is true, and I will likely be using this in the end. But I am very intrigued by the sudoers file at this point and would like very much so to learn how to manipulate it.

---

### Post by ByteJuggler on 2008-12-30
> **DoubleMcLovin said:**
> I read that first link that was given, and from that file I derived my changes here. I receive the error that only root can do that when I try an mount even after a reboot.

Not having checked your sudoers file yet, I need to just ask, based on the error message: Have you run the command with "sudo" in front?  The error message suggests you may not have.  Putting the command in sudoers doesn't remove the need to actually run a command with "sudo" in front, in order for it to run as root.  It can however remove the need for password authentication etc.

---

### Post by DoubleMcLovin on 2008-12-30
> **ByteJuggler said:**
> Not having checked your sudoers file yet, I need to just ask, based on the error message: Have you run the command with "sudo" in front?  Putting the command in sudoers doesn't remove the need to actually run a command with "sudo" in front, in order for it to run as root.

My intention with the sudoers file was to remove the need to run the command with the sudo prefix. I was hoping that via the sudoers file I would be able to give the user 'andy' access to the commands located in /sbin/mount and /sbin/umount

---

### Post by DoubleMcLovin on 2008-12-30
interestingly enough, even with the proper fstab command with noauto as an option, it wont let me mount unless I'm root. I have tried removing the noauto and running 'sudo mount -a' and the partition mounts fine. I have also tried leaving the file in fstab with noauto specified and run the mount using sudo and it mounts fine. here is my fstab line for the test partition:
```
//192.168.1.224/80gb.wndws /media/wndws   cifs  username=testname,passwords=testpass,noauto,user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by snova on 2008-12-30
Rather than tweaking sudo settings, there is a package called 'pmount' with the following description that may be useful:

> 
Description: mount removable devices as **normal user**

pmount is a wrapper around the standard mount program which permits normal users to mount removable devices without a matching /etc/fstab entry. This provides a robust basis for automounting frameworks like GNOME's Utopia project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some information like device labels and mount options from hal and passes them to pmount. Install the package "hal" if you want to use this feature.

If a LUKS capable cryptsetup package is installed, pmount is able to transparently mount encrypted volumes.


---

### Post by ByteJuggler on 2008-12-30
> **DoubleMcLovin said:**
> My intention with the sudoers file was to remove the need to run the command with the sudo prefix. I was hoping that via the sudoers file I would be able to give the user 'andy' access to the commands located in /sbin/mount and /sbin/umount

I don't think you can remove the need for the sudo prefix -- it's not actually a prefix after all, it's a command, "sudo", which in turn reads its config file and then runs the command specified as *its* paramter according to how its configured (sudoers file).  That said, you can avoid sudo through the use of "user" and "noauto" option in fstab.

---

### Post by ByteJuggler on 2008-12-30
> **DoubleMcLovin said:**
> interestingly enough, even with the proper fstab command with noauto as an option, it wont let me mount unless I'm root. I have tried removing the noauto and running 'sudo mount -a' and the partition mounts fine. I have also tried leaving the file in fstab with noauto specified and run the mount using sudo and it mounts fine. here is my fstab line for the test partition:
```
//192.168.1.224/80gb.wndws /media/wndws   cifs  username=testname,passwords=testpass,noauto,user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Strange, the following works fine for one of my partitions, maybe it gives you a hint:

```
# /dev/sda5
UUID=d0b1a95f-501e-4f65-945c-c6bc493db670 /media/sda5     ext3    defaults,user,noauto        0       2

```

As an aside: I note you have "passwords" instead of "password", presume that's a typo.  Also, I've not tested this with a samba mount - that might have something to do with the problem......

I'll test and get back to you.

---

### Post by ByteJuggler on 2009-01-02
OK, I've now tested mounting a SAMBA share on my Ubuntu box by using the fstab line like this:

```
//machinename/share /local/path/to/mountpoint cifs noauto,user,credentials=/root/.smbcredentials,iocharset=utf8	   0	0
```

I put the credentials used in ".smbcredentials" and marked it so only "root" can read it (chmod 400 /root/.smbcredentials) to add a bit of security.  Anyway, set up with the above, my normal user can mount the share by entering:

```
mount /local/path/to/mountpoint
```

No sudo interaction is required.  BTW it's my understanding that on Windows hosts one should probably not use the iocharset=utf8 as it will treat the filesystem as case-sensitive, which may cause problems when Windows tries to read files as it treats the filesystem as case-insensitive and will then not know how to deal with 2 files with the same name except for a case difference.  (But, I may be wrong on that/am not very sure, so please ignore/respond if you know better.)

Hope that helps.

---

