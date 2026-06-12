---
title: "useradd via ssh - struggles to make user profile to work"
date: 2019-06-02
forum: Networking &amp; Wireless
---

### Post by sprinterdriver on 2019-06-02
Hi.

I have currently two computers on my home network.
[LIST]
[*]Laptop with Linux Lite 4.2 
[*]Desktop computer with Ubuntu Mate 19.04 
[/LIST]

I'm in the process of learning to use ssh, so I may not doing it the easiest way.
On the desktop there are currently only one user profile, and I want to make another user - using SSH when sitting in front of the laptop - ADN this user will have its home folder encrypted.
Previous to this I have make SSH to work properly, and I have already tested rsync between the computers to function just well.

Here is detailed steps of what I have done so far (Already logged in on desktop via ssh as main user) :

**Adding new user**
~$ sudo useradd -G lager littlebrother
~$ passwd littlebrother


**Installing ecryptfs package**
~$ sudo apt-get install ecryptfs-utils cryptsetup
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  cryptsetup-bin cryptsetup-initramfs cryptsetup-run keyutils libecryptfs1
Suggested packages:
  zescrow-client
The following NEW packages will be installed:
  cryptsetup cryptsetup-bin cryptsetup-initramfs cryptsetup-run ecryptfs-utils
  keyutils libecryptfs1
0 upgraded, 7 newly installed, 0 to remove and 65 not upgraded.
Need to get 481 kB of archives.
After this operation, 2&#8239;015 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://no.archive.ubuntu.com/ubuntu disco/main amd64 cryptsetup-bin amd64 2:2.1.0-1ubuntu1 [108 kB]
Get:2 http://no.archive.ubuntu.com/ubuntu disco/main amd64 cryptsetup-run amd64 2:2.1.0-1ubuntu1 [150 kB]
Get:3 http://no.archive.ubuntu.com/ubuntu disco/main amd64 cryptsetup-initramfs all 2:2.1.0-1ubuntu1 [25,5 kB]
Get:4 http://no.archive.ubuntu.com/ubuntu disco/main amd64 cryptsetup all 2:2.1.0-1ubuntu1 [4&#8239;436 B]
Get:5 http://no.archive.ubuntu.com/ubuntu disco/universe amd64 libecryptfs1 amd64 111-0ubuntu5 [42,7 kB]
Get:6 http://no.archive.ubuntu.com/ubuntu disco/main amd64 keyutils amd64 1.6-6 [44,6 kB]
Get:7 http://no.archive.ubuntu.com/ubuntu disco/universe amd64 ecryptfs-utils amd64 111-0ubuntu5 [106 kB]
Fetched 481 kB in 1s (868 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package cryptsetup-bin.
(Reading database ... 243271 files and directories currently installed.)
Preparing to unpack .../0-cryptsetup-bin_2%3a2.1.0-1ubuntu1_amd64.deb ...
Unpacking cryptsetup-bin (2:2.1.0-1ubuntu1) ...
Selecting previously unselected package cryptsetup-run.
Preparing to unpack .../1-cryptsetup-run_2%3a2.1.0-1ubuntu1_amd64.deb ...
Unpacking cryptsetup-run (2:2.1.0-1ubuntu1) ...
Selecting previously unselected package cryptsetup-initramfs.
Preparing to unpack .../2-cryptsetup-initramfs_2%3a2.1.0-1ubuntu1_all.deb ...
Unpacking cryptsetup-initramfs (2:2.1.0-1ubuntu1) ...
Selecting previously unselected package cryptsetup.
Preparing to unpack .../3-cryptsetup_2%3a2.1.0-1ubuntu1_all.deb ...
Unpacking cryptsetup (2:2.1.0-1ubuntu1) ...
Selecting previously unselected package libecryptfs1.
Preparing to unpack .../4-libecryptfs1_111-0ubuntu5_amd64.deb ...
Unpacking libecryptfs1 (111-0ubuntu5) ...
Selecting previously unselected package keyutils.
Preparing to unpack .../5-keyutils_1.6-6_amd64.deb ...
Unpacking keyutils (1.6-6) ...
Selecting previously unselected package ecryptfs-utils.
Preparing to unpack .../6-ecryptfs-utils_111-0ubuntu5_amd64.deb ...
Unpacking ecryptfs-utils (111-0ubuntu5) ...
Setting up cryptsetup-bin (2:2.1.0-1ubuntu1) ...
Setting up libecryptfs1 (111-0ubuntu5) ...
Setting up cryptsetup-run (2:2.1.0-1ubuntu1) ...
Setting up keyutils (1.6-6) ...
Setting up cryptsetup-initramfs (2:2.1.0-1ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Setting up cryptsetup (2:2.1.0-1ubuntu1) ...
Setting up ecryptfs-utils (111-0ubuntu5) ...
Processing triggers for systemd (240-6ubuntu5) ...
Processing triggers for man-db (2.8.5-2) ...
Processing triggers for libc-bin (2.29-0ubuntu2) ...
Processing triggers for initramfs-tools (0.131ubuntu19) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-15-generic
cryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries 
    nor crypto modules. If that's on purpose, you may want to uninstall the 
    'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs 
    integration and avoid this warning.
I: The initramfs will attempt to resume from /dev/sdb6
I: (UUID=333dd958-cc2f-493d-a821-019ad17e3ef4)
I: Set the RESUME variable to override this.
```


**Trying to encrypt the new users home dir**
~$ sudo ecryptfs-migrate-home -u littlebrother
```
INFO:  Checking disk space, this may take a few moments.  Please be patient.
du: cannot access '/home/littlebrother': No such file or directory
df: /home/littlebrother: No such file or directory
INFO:  2.5x the size your current home directory is required to perform a migration.
INFO:  Once the migration succeeds, you may recover most of this space by deleting the cleartext directory.
ERROR:  Not enough free disk space.
```


Sign of trouble. After some searching on internet I learned that the useradd command probably don't create a home dir for the new user. So I found a recipee on how to **manually add the user home dir**.
```
~$ sudo mkdir /home/littlebrother
~$ sudo cp -rT /etc/skel /home/littlebrother
~$ sudo chown -R littlebrother:littlebrother /home/littlebrother
~$ exit
logout
Connection to 192.168.0.14 closed.
```


**Trying to login as the newly created user - expect this to work now, but**
ssh littlebrother@192.168.0.14
```
littlebrother@192.168.0.14's password: 
Welcome to Ubuntu 19.04 (GNU/Linux 5.0.0-15-generic x86_64)
. . . . .  strips away same lines that appear here every login
Last login: Mon Jun  3 00:17:57 2019 from 192.168.0.16
-sh: 2: [: x: unexpected operator
-sh: 2: [: x: unexpected operator
$ 
exit
```

When logged in as the other user, it seemed like any other commands other than "exit" have no effect. How comes?
Is it because there are no shell? Can this be fixed without deleting the user?

---

### Post by #&amp;thj^% on 2019-06-02
SSH is very picky about the directory and file permissions. Make sure that:
[list]
    [*]The directory /home/username/.ssh has permission "700" and is owned by the user (not root!)
    [*]The /home/username/ssh/authorized_keys has permission "600" and is owned by the user[/list]

Copy your public key into the authorized_keys file.
```

sudo chown -R username:username /home/username/.ssh
sudo chmod 0700 /home/username/.ssh
sudo chmod 0600 /home/username/.ssh/authorized_keys
```

There is NO need to add the user to /etc/ssh/ssh_config.
**I'd also recommend using "adduser" (instead of "useradd") for adding new users; it is a little more friendly about various default account settings.**

As long as the user is not part of the admin group, they will not be able to sudo to root. For them to use su, you will need to set a root password (passwd root), after which I recommend setting PermitRootLogin=no in /etc/ssh/sshd_config.

---

### Post by sprinterdriver on 2019-06-03
Thanks for answer, but I seeminly had ssh login working perfectly.

It is the user creation that I'm struggling with.

[spending time deleting user and re-adding with adduser command]
Problem solved, I apparently have a working user profile

I logged in as primary user, then removed the second user using userdel -r.
```
~$ sudo userdel -r littlebrother
```

Ahh - got to find a _very useful information in the adduser man page_ - It support natively encrypting the home dir with the                --encrypt-home option.
So I did managed to create that user in one single command:
```
~$ sudo adduser --encrypt-home littlebrother
```

There is a weird thing. I did a ssh login as littlebrother imediately after creating it. The ls command returned nothing.
I logged out of ssh session.

Then I walked the few steps to the desktop computer, log in as "littlebrother", and then logged out again.

And then returned to the laptop.

Logged into the desktop as "littlebrother" via ssh. When running ls command now, it outputs the default directories: Desktop  Documents, etc...

How comes?

---

### Post by sisco311 on 2019-06-03
> **sprinterdriver said:**
> 
And then returned to the laptop.

Logged into the desktop as "littlebrother" via ssh. When running ls command now, it outputs the default directories: Desktop  Documents, etc...

How comes?

They are created by xdg-user-dirs:
[https://www.freedesktop.org/wiki/Software/xdg-user-dirs/](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/)
[https://wiki.archlinux.org/index.php/XDG_user_directories](https://wiki.archlinux.org/index.php/XDG_user_directories)

---

