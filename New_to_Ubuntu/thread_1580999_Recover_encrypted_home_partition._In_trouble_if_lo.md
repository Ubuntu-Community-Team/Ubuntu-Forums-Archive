---
title: "Recover encrypted home partition. In trouble if lost"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by ojireland on 2010-09-24
Hello, 

Complete noob running ubuntu 10.04.    Never any major problems.  This is work and personal pc.

I am despartly assistance and hope one of you fellows can help. I even offer complete access to my pc if that helps

I needed to install windows on free space at start of hard drive (needed to try use photoshop). Installed and now have serious problems.

I have trawled and tried many solutions but am only getting frustrated and lost (when I have used terminal before i always just copy and paste from solutions i find online). 
Here are the related threads that relate to my problem but trying them is not working and I am totally confused.

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)
[http://ubuntuforums.org/showthread.php?t=1521023](http://ubuntuforums.org/showthread.php?t=1521023)
[http://ubuntuforums.org/showthread.php?t=1463392](http://ubuntuforums.org/showthread.php?t=1463392)
[http://ubuntuforums.org/showthread.php?t=1471961](http://ubuntuforums.org/showthread.php?t=1471961)
[http://ubuntuforums.org/showthread.php?t=1320687](http://ubuntuforums.org/showthread.php?t=1320687)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually")
[http://ubuntuforums.org/showthread.php?t=1337693](http://ubuntuforums.org/showthread.php?t=1337693)
[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
[http://ubuntuforums.org/showthread.php?t=1437015](http://ubuntuforums.org/showthread.php?t=1437015)


So here is the problem.

After I installed the windows xp on free partition I booted from live usb to fix the grub.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Rebooted and got this message
[U]Serious errors were found while checking the disk drive for home.
Press I to Ignore S to Skip mounting or M for Manual recovery[/U]

If I press Ignore and then skip nothing gets loaded and somewhere this error comes up.

There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

Anyway I thought this was something to do with grub and spent ages trying to fix this but I actually done care now about even fixing the OS, I just need access to the home partition for work reasons.
[U]If I don't get into it in a few hours I will be in some serious, serious trouble with job.


[/U]I am nearly sure that 
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709)
and especially
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709/comments/3](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709/comments/3)

Can fix my problem.

But I am stressing and can't figure it out.

I don't know there's any problem with this but I want to ask if it's possible to get someone to take control of the PC with _Teamviewer_ or something and have a go.

I am truly in trouble here, Is there someone who can please help me.

I have the encrypted passphrase and managed to get the other sig code thing

Many thanks in advance

---

### Post by robsoles on 2010-09-24
Boot from a live CD

Look under 'places' for your file-system, if you see it there then click it to open it out of places there.

Double click 'home' and look for your own home directory, double click it and you should be looking at a couple of file regarding your encrypted files.

Pretty sure you double click one of the files you can see at this point and will soon be challenged for the passphrase hash. Haven't tried it myself so am probably wrong - have a go and tell me how you get on.

---

### Post by ojireland on 2010-09-24
Hi,

Thanks for responding.

When I double any of the files in my encrypted home partition (they all have an X on them), This is the message shown.

This example is for the Private folder
[B]
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of ".Private".Thanks again
[/B]

---

### Post by robsoles on 2010-09-24
the one time I navigated to my /home folder, on a machine where I used encrypted home folder(s), I found only two files on display.

It entirely looked to me as if one of the files was a launcher to allow access to the encrypted file-space.

Sorry if that isn't helping yet.

Have a look at [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

also [http://www.google.com/search?q=access+encrypted+home+directory+in+ubuntu](http://www.google.com/search?q=access+encrypted+home+directory+in+ubuntu)

---

### Post by ojireland on 2010-09-24
I have checked this stuff out.

Any brave takers on the control my Pc suggestion?

---

### Post by KIAaze on 2010-09-24
Hi,

I only have an encrypted "Private" directory, not a fully encrypted home.
But I think the procedure is pretty similar.

I just successfully tested a recovery procedure on my PC using a Lubuntu 10.04 Live-CD (should work the same way with any ubuntu live-CD supporting your filesystem (ext4 in my case)).

Here are the commands I ran in a terminal **after mounting the partition using the graphical browser** (which is easier and safer than trying it by command-line):
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo ecryptfs-add-passphrase --fnek
Passphrase: 
ubuntu@ubuntu:~$ cd /media/e81ca359-a0ee-4357-9748-972b95db85a7/
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ ls
guest  lost+found  KIAaze  pierre
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ cd KIAaze/
bash: cd: KIAaze/: Permission denied
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ ls
guest  lost+found  KIAaze  pierre
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ cd KIAaze/
bash: cd: KIAaze/: Permission denied
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ su
Password: 
su: Authentication failure
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ sudo cd KIAaze
sudo: cd: command not found
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ sudo passwd
Enter new UNIX password: 
Retype new UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ sudo su
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cd KIAaze/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls .Private/
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxAR4zh4KMkZKlfT4v-eHm.3Ok--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARb8M4-4fLKfW2YoXfb8rlkk--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARdvb8KlxuBWGay-O.qob4fE--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARFTlX4rNWJI-cIiylQ9wKs---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARfwzFY3-er6GJ9SFXV2O9ak--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxAR.GvE.hhVSv17jyBaUtedmk--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARH0in5xhoPEzOiLfAbc9K4U--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARorQZXBdzoJLtQybJ2vhiJE--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARpMVwI7tO4lAEdg2h8hQir---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARQ8NP4fiqoXyO7ZfnjkiuSE--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARthdnMUOn7tqn5L8jpEwqF---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARwgeffLTVvVkcWcnLMUwbR---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARXjcdv-kyo4B4efC0xT.BXU--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARyfGglQpnjgIvoNLLD0mf8---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARZVyCVc7IAOHTXF4LDXqx6k--
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls Private
Access-Your-Private-Data.desktop  README.txt
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# cat Private/Access-Your-Private-Data.desktop 
[Desktop Entry]
_Name=Access Your Private Data
_GenericName=Access Your Private Data
Exec=/usr/bin/ecryptfs-mount-private
Terminal=true
Type=Application
Categories=System;Security;
X-Ubuntu-Gettext-Domain=ecryptfs-utils
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls .ecryptfs/
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls .ecryptfs/wrapped-passphrase 
.ecryptfs/wrapped-passphrase
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase
Passphrase: 
PASSPHRASE
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# 

root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [2b511591c079c7e9] into the user session keyring
Inserted auth tok with sig [ac71f571150d4822] into the user session keyring
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# mount -t ecryptfs ./.Private/ ./Private/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [2b511591c079c7e9]: ac71f571150d4822
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=ac71f571150d4822
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=2b511591c079c7e9
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [2b511591c079c7e9] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls Private/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls -A Private/
.amsn    .dropbox       .gnupg       .mozilla  .purple  .SpiderOak  .sylpheed-2.0  .xchat2
.config  .dropbox-dist  .macromedia  .opera    .Skype   .ssh        .wicd
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# cat ./Private/.config/autostart/xchat.desktop 

[Desktop Entry]
Type=Application
Name=xchat
Exec=xchat
Icon=system-run
Comment=
Name[en_US]=xchat
Comment[en_US]=
X-GNOME-Autostart-enabled=false
NotShowIn=LXDE;
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# 


```

I'm on IRC (#ubuntu@freenode) right now if you want to chat.

---

### Post by KIAaze on 2010-09-24
Cleaned and commented version:
```

# after mounting the partition, I cd into it:
ubuntu@ubuntu:~$ cd /media/e81ca359-a0ee-4357-9748-972b95db85a7/

# list of contents (partition = home directory here)
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ ls
guest  lost+found  KIAaze  pierre

# cd into my home fails
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ cd KIAaze/
bash: cd: KIAaze/: Permission denied

# so I switch to root
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ sudo su

# now it works :)
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cd KIAaze/

# checking contents of encrypted partition: filenames are encrypted
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls .Private/
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxAR4zh4KMkZKlfT4v-eHm.3Ok--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARb8M4-4fLKfW2YoXfb8rlkk--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARdvb8KlxuBWGay-O.qob4fE--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARFTlX4rNWJI-cIiylQ9wKs---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARfwzFY3-er6GJ9SFXV2O9ak--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxAR.GvE.hhVSv17jyBaUtedmk--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARH0in5xhoPEzOiLfAbc9K4U--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARorQZXBdzoJLtQybJ2vhiJE--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARpMVwI7tO4lAEdg2h8hQir---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARQ8NP4fiqoXyO7ZfnjkiuSE--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARthdnMUOn7tqn5L8jpEwqF---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARwgeffLTVvVkcWcnLMUwbR---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARXjcdv-kyo4B4efC0xT.BXU--
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARyfGglQpnjgIvoNLLD0mf8---
ECRYPTFS_FNEK_ENCRYPTED.FWagQTJl3Ep66UQlWWWJ5yUc-aBdjpC2nxARZVyCVc7IAOHTXF4LDXqx6k--

# checking what's in the "Private" folder, where .Private usually gets mounted
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls Private
Access-Your-Private-Data.desktop  README.txt

# searching for wrapped-passphrase
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls .ecryptfs/
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase

# found it in default location
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls .ecryptfs/wrapped-passphrase 
.ecryptfs/wrapped-passphrase

# I decrypt it. It asks for your login password (used when you created the encrypted directory/partition)
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase
Passphrase: 
PASSPHRASE

# Ok, now we really start the procedure.
# Here it asks for the PASSPHRASE I just got above
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [2b511591c079c7e9] into the user session keyring
Inserted auth tok with sig [ac71f571150d4822] into the user session keyring

# Mounting the encrypted dir located at ".Private" into "Private"
# First asks for PASSPHRASE, then for result "ac71f571150d4822" from previous command.
# Everything was ok by default (just press enter), except "encrypted filenames", where I had to choose "y".
# I also answered "yes" for proceeding with mount. Not sure if just pressing enter works
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# mount -t ecryptfs ./.Private/ ./Private/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [2b511591c079c7e9]: ac71f571150d4822
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=ac71f571150d4822
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=2b511591c079c7e9
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [2b511591c079c7e9] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs

# checking if it worked
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# ls -A Private/
.amsn    .dropbox       .gnupg       .mozilla  .purple  .SpiderOak  .sylpheed-2.0  .xchat2
.config  .dropbox-dist  .macromedia  .opera    .Skype   .ssh        .wicd

# yep, files present and readable :)
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/KIAaze# cat ./Private/.config/autostart/xchat.desktop 

[Desktop Entry]
Type=Application
Name=xchat
Exec=xchat
Icon=system-run
Comment=
Name[en_US]=xchat
Comment[en_US]=
X-GNOME-Autostart-enabled=false
NotShowIn=LXDE;


```

---

### Post by ojireland on 2010-09-24
Hi KIAaze,

Had to go away for a little bit.

This looks great. I really appreciate the effort you have put into this to make it clear for me.

I am going to give it a go now and I will post back to let you know how it goes.

Thanks again

---

### Post by KIAaze on 2010-09-24
I created a new user with encrypted home directory to see how it works then. :)

The main difference is that the wrapped passphrase and encrypted data are then located in /home/.ecryptfs instead of in the user's home dir.

Here are the results:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ cd /media/e81ca359-a0ee-4357-9748-972b95db85a7
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ ls
guest  jamesbond  lost+found  KIAaze  pierre
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ sudo -i
root@ubuntu:~# ll
total 4
drwx------  2 root root   46 2010-04-30 14:00 ./
drwxr-xr-x 31 root root  280 2010-09-24 14:40 ../
-rw-r--r--  1 root root 3106 2010-04-23 09:45 .bashrc
-rw-r--r--  1 root root  140 2010-04-23 09:45 .profile
root@ubuntu:~# pwd
/root
root@ubuntu:~# cd /media/e81ca359-a0ee-4357-9748-972b95db85a7/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cd jamesbond/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ls
Access-Your-Private-Data.desktop  README.txt
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# cat Access-Your-Private-Data.desktop 
[Desktop Entry]
_Name=Access Your Private Data
_GenericName=Access Your Private Data
Exec=/usr/bin/ecryptfs-mount-private
Terminal=true
Type=Application
Categories=System;Security;
X-Ubuntu-Gettext-Domain=ecryptfs-utils
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# cd ..
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls
guest  jamesbond  lost+found  KIAaze  pierre
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cd jamesbond/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# /usr/bin/ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ls -A


Access-Your-Private-Data.desktop  .ecryptfs  .Private  README.txt
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# 
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# 
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ls -A
Access-Your-Private-Data.desktop  .ecryptfs  .Private  README.txt
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase
Passphrase: 
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase
Passphrase: 
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# tail /var/log/syslog 
Sep 24 14:07:30 ubuntu kernel: [ 1625.789760] sd 2:0:0:0: [sdb] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
Sep 24 14:07:30 ubuntu kernel: [ 1625.790493] sd 2:0:0:0: [sdb] Write Protect is off
Sep 24 14:07:30 ubuntu kernel: [ 1625.790501] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
Sep 24 14:07:30 ubuntu kernel: [ 1625.790505] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep 24 14:07:30 ubuntu kernel: [ 1625.805827] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep 24 14:07:31 ubuntu kernel: [ 1625.805848]  sdb: sdb1
Sep 24 14:07:31 ubuntu kernel: [ 1626.584642] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep 24 14:07:31 ubuntu kernel: [ 1626.584656] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Sep 24 14:08:00 ubuntu kernel: [ 1655.776281] EXT4-fs (sda3): mounted filesystem with ordered data mode
Sep 24 14:16:08 ubuntu ecryptfs-unwrap-passphrase: Error attempting to open [.ecryptfs/wrapped-passphrase] for reading
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ll .ecryptfs 
lrwxrwxrwx 1 1002 1002 35 2010-09-24 13:34 .ecryptfs -> /home/.ecryptfs/jamesbond/.ecryptfs
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# cd ..
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls
guest  jamesbond  lost+found  KIAaze  pierre
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls -A
.ecryptfs  guest  jamesbond  lost+found  KIAaze  pierre
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/
jamesbond
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/.
./         ../        .ecryptfs/ .Private/  
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/.ecryptfs/
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase 
.ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ecryptfs-unwrap-passphrase .ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase
Passphrase: 
1a2571c22480d6c840f2d739029fd7e1
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [d1f18e68e1a7719d] into the user session keyring
Inserted auth tok with sig [8378660ef042249e] into the user session keyring
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls jamesbond/.Private 
jamesbond/.Private
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ll jamesbond/.Private 
lrwxrwxrwx 1 1002 1002 34 2010-09-24 13:34 jamesbond/.Private -> /home/.ecryptfs/jamesbond/.Private
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/.Private/
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG10GeDOaNQVNufc89eG1foU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG1zWHFNhTzBJSgvgLdgdTZk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG2dalhAuNIcxGR9ruOdNClU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG2MpvdUAc8S2vU7P9AWvKvE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG6yWh-bCrTnXiuDKM6JVkl---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGal4B8Z2G9CIv6nL6u-vuNk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGaTLK7ik0Tj7PpUqLAlZmuU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGBSHlF2g90IoPfPLYpVsl8U--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGfiLyLWdKaLpJTR0n50dgkE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGGZAtsfzqB0Qy9lYooCxluk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGH9F19Evas6unv9ghmATaFE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGjXrJrCuj8ACa4PDQVxlMIE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGkJxa-wlpzZmtIi62kvbGSk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGM-ufX6iIhLMflxoWcRMLOE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGnV6FgftXErpnZV0Pg-s3J---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGPJ..o9jNBwp6XPEsKzif8---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGQ3pFQcHcF-uyauKMBD1ipk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGQvKjIUkThSnBZ7kg9iIx1k--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGRrUsJtPvd5QfkjbBLoc0iE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGskxoYhulIuelAB3ybRzUzk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGsz7Gu6CSPZ96elaChqET.E--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGt5Crz.lMa9s3kPhuJi3wBU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGTq4nwFI.6tossSiACcV2ZU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGtzUru156thNlcjYaYN9Yt---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGwmEMMlKS8sNiMmebZoAcRk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGX6ecRnN0ArLCUkkLBse7iU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGXKYDGG04yChUQPKCMCjhhE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGyCAJQhEt15WXYXvdnmCvRE--
ECRYPTFS_FNEK_ENCRYPTED.FXa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGKfbD9K6FYCHeNmUIGE4Bp.DDJwtsp1YOr94RT2bVW1Q-
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# #mount -t ecryptfs .ecryptfs/jamesbond/.Private/ 
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls /mnt/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# mount -t ecryptfs .ecryptfs/jamesbond/.Private/ /mnt/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [d1f18e68e1a7719d]: 8378660ef042249e
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=8378660ef042249e
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=d1f18e68e1a7719d
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [d1f18e68e1a7719d] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls /mnt/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls /mnt/
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# mkdir /mnt/Private
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# mount -t ecryptfs .ecryptfs/jamesbond/.Private/ /mnt/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [d1f18e68e1a7719d]: 8378660ef042249e
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=8378660ef042249e
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=d1f18e68e1a7719d
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [d1f18e68e1a7719d] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls /mnt/
Private
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls /mnt/Private/
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  topsecret.txt  Videos
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cat /mnt/Private/topsecret.txt 
Hello world!
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# 

```

---

### Post by KIAaze on 2010-09-24
Cleaned and commented version again:
```

# mount using GUI and cd into it
ubuntu@ubuntu:~$ cd /media/e81ca359-a0ee-4357-9748-972b95db85a7

# checking we're in the right place
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ ls
guest  jamesbond  lost+found  KIAaze  pierre

# using officially recommended way of getting root shell :)
ubuntu@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7$ sudo -i

# oops, we landed in root's home
root@ubuntu:~# ll
total 4
drwx------  2 root root   46 2010-04-30 14:00 ./
drwxr-xr-x 31 root root  280 2010-09-24 14:40 ../
-rw-r--r--  1 root root 3106 2010-04-23 09:45 .bashrc
-rw-r--r--  1 root root  140 2010-04-23 09:45 .profile
root@ubuntu:~# pwd
/root

# changing into partition with encrypted dir again...
root@ubuntu:~# cd /media/e81ca359-a0ee-4357-9748-972b95db85a7/

# changing into user dir
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cd jamesbond/

# mmh, no "Private" dir this time
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ls
Access-Your-Private-Data.desktop  README.txt

# looking for hidden files. Aha, .ecryptfs and .Private!
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ls -A
Access-Your-Private-Data.desktop  .ecryptfs  .Private  README.txt

# but they are symbolic links. Trying to unwrap the passphrase from here will fail since the links are broken due to using a Live-CD.
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# ll .ecryptfs 
lrwxrwxrwx 1 1002 1002 35 2010-09-24 13:34 .ecryptfs -> /home/.ecryptfs/jamesbond/.ecryptfs

# going back up
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7/jamesbond# cd ..

# and here is the real .ecryptfs dir!
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls -A
.ecryptfs  guest  jamesbond  lost+found  KIAaze  pierre

# and here's the wrapped-passphrase we need
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase 
.ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase

# Decrypting it using login password of "jamesbond"
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ecryptfs-unwrap-passphrase .ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase
Passphrase: 
1a2571c22480d6c840f2d739029fd7e1

# starting the real recovery procedure
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [d1f18e68e1a7719d] into the user session keyring
Inserted auth tok with sig [8378660ef042249e] into the user session keyring

# here's where the real encrypted data is stored (good to know if you want to back it up: It's NOT in "/home/jamesbond", but in "/home/.ecryptfs/jamesbond/.Private/"!!!)
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls .ecryptfs/jamesbond/.Private/
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG10GeDOaNQVNufc89eG1foU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG1zWHFNhTzBJSgvgLdgdTZk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG2dalhAuNIcxGR9ruOdNClU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG2MpvdUAc8S2vU7P9AWvKvE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWG6yWh-bCrTnXiuDKM6JVkl---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGal4B8Z2G9CIv6nL6u-vuNk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGaTLK7ik0Tj7PpUqLAlZmuU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGBSHlF2g90IoPfPLYpVsl8U--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGfiLyLWdKaLpJTR0n50dgkE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGGZAtsfzqB0Qy9lYooCxluk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGH9F19Evas6unv9ghmATaFE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGjXrJrCuj8ACa4PDQVxlMIE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGkJxa-wlpzZmtIi62kvbGSk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGM-ufX6iIhLMflxoWcRMLOE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGnV6FgftXErpnZV0Pg-s3J---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGPJ..o9jNBwp6XPEsKzif8---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGQ3pFQcHcF-uyauKMBD1ipk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGQvKjIUkThSnBZ7kg9iIx1k--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGRrUsJtPvd5QfkjbBLoc0iE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGskxoYhulIuelAB3ybRzUzk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGsz7Gu6CSPZ96elaChqET.E--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGt5Crz.lMa9s3kPhuJi3wBU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGTq4nwFI.6tossSiACcV2ZU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGtzUru156thNlcjYaYN9Yt---
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGwmEMMlKS8sNiMmebZoAcRk--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGX6ecRnN0ArLCUkkLBse7iU--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGXKYDGG04yChUQPKCMCjhhE--
ECRYPTFS_FNEK_ENCRYPTED.FWa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGyCAJQhEt15WXYXvdnmCvRE--
ECRYPTFS_FNEK_ENCRYPTED.FXa1S4MCw26YbUQjQrAdRRDJAHsZObFAnsWGKfbD9K6FYCHeNmUIGE4Bp.DDJwtsp1YOr94RT2bVW1Q-

# creating a place to mount
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# mkdir /mnt/Private

# Finally mounting the encrypted dir
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# mount -t ecryptfs .ecryptfs/jamesbond/.Private/ /mnt/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [d1f18e68e1a7719d]: 8378660ef042249e
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=8378660ef042249e
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=d1f18e68e1a7719d
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [d1f18e68e1a7719d] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs

# And here's the decrypted data! :D
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# ls /mnt/Private/
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  topsecret.txt  Videos

# James Bond's secret diary has been compromised!
root@ubuntu:/media/e81ca359-a0ee-4357-9748-972b95db85a7# cat /mnt/Private/topsecret.txt 
Hello world!

```

---

### Post by ojireland on 2010-09-24
Hi KIAaze,

Running in to problems.

bash: cd: /media/e81ca359-a0ee-4357-9748-972b95db85a7/: No such file or directory
ubuntu@ubuntu:~$ cd /media/276bb0d7-095a-4d6c-ad20-75a292b46823/
ubuntu@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823$ 
ubuntu@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823$ cd len/
bash: cd: len/: Permission denied
ubuntu@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823$ sudo su
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# cd len/
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# .Private/
bash: .Private/: No such file or directory
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# ls .Private/
ls: cannot access .Private/: No such file or directory
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# cd .ecryptfs/len/.private/
bash: cd: .ecryptfs/len/.private/: No such file or directory
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# 

Is this because of the structure of the files in the home partition?
Please see this-
[http://ubuntuforums.org/attachment.php?attachmentid=170414&stc=1&d=1285339340](http://ubuntuforums.org/attachment.php?attachmentid=170414&stc=1&d=1285339340)

"118 GB Filesystem" is the /home partition that is encrypted

Thanks again

---

### Post by KIAaze on 2010-09-24
Ok, I'm assuming "/media/276bb0d7-095a-4d6c-ad20-75a292b46823/" is the 118 GB partition. (You can verify this by pressing "ctrl+L" in nautilus I think. Or some method to show the filepath instead of the "breadcrumb system".)

Try (in a new terminal, to keep things clean):
```

sudo -i
cd /media/276bb0d7-095a-4d6c-ad20-75a292b46823/.ecryptfs/len/
ls -A /media/276bb0d7-095a-4d6c-ad20-75a292b46823/.ecryptfs/len/.Private
ls -A /media/276bb0d7-095a-4d6c-ad20-75a292b46823/.ecryptfs/len/.ecryptfs
ls /media/276bb0d7-095a-4d6c-ad20-75a292b46823/.ecryptfs/len/.ecryptfs/wrapped-passphrase

```

If those commands work, you should be able to proceed with:
_**1) Get the passphrase (unless you already have it)**_
```
ecryptfs-unwrap-passphrase /media/276bb0d7-095a-4d6c-ad20-75a292b46823/.ecryptfs/len/.ecryptfs/wrapped-passphrase

```
It will ask for the **login password** of "len" and give you the **passphrase**.
Then:

_**2) Get the filename encryption key (if you have encrypted filenames)**_
```
ecryptfs-add-passphrase --fnek
```
It will ask from the **passphrase** you got from the previous command and give you 2 keys. Note the 2nd key, which is the **filename encryption key**.

_**3) Mount the encrypted directory**_
Now you can mount the encrypted home dir on /mnt/Private:
```
mkdir /mnt/Private
mount -t ecryptfs /media/276bb0d7-095a-4d6c-ad20-75a292b46823/.ecryptfs/len/.Private/ /mnt/Private

```
It will request the **passphrase** first and then the **filename encryption key** you got from "ecryptfs-add-passphrase".
All options can be left on default (just press enter), except "filename encryption", the "filename encryption key", the mount confirmation and the warning disabling question.

Example:
```
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [d1f18e68e1a7719d]: 8378660ef042249e
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=8378660ef042249e
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=d1f18e68e1a7719d
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [d1f18e68e1a7719d] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs
```

_Note:_ If you have not encrypted the filenames (but that's default since Ubuntu 9.04), you don't need step 2 apparently and can answer "no" to the filename encryption question.

---

### Post by KIAaze on 2010-09-24
accidental duplicate post

---

### Post by ojireland on 2010-09-24
Hi KIAaze,

I got a few lines from the end of your super clear instructions, almost jumping for joy, any idea what went wrong?

I have highlighted in red where I think things went bad, but really no notion.


ubuntu@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823$ sudo su
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# -A
-A: command not found
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# cd len/
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# -A
-A: command not found
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# ls
Access-Your-Private-Data.desktop  README.txt
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# ls -A
Access-Your-Private-Data.desktop  .cache  .ecryptfs  .Private  README.txt
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# ll .ecryptfs
lrwxrwxrwx 1 1000 1000 29 2010-09-14 21:56 .ecryptfs -> /home/.ecryptfs/len/.ecryptfs
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823/len# cd ..
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# ls -A
.ecryptfs  len  lost+found
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# .ecryptfs/len/.ecrypts/bash: .ecryptfs/len/.ecrypts/: No such file or directory
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# .ecryptfs/len/.ecrypts/.ecryptfs/len/.ecryptfs/wrapped-passphrase
bash: .ecryptfs/len/.ecrypts/.ecryptfs/len/.ecryptfs/wrapped-passphrase: No such file or directory
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# ls .ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase
ls: cannot access .ecryptfs/jamesbond/.ecryptfs/wrapped-passphrase: No such file or directory
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# ls .ecryptfs/len/.ecryptfs/wrapped-passphrase
.ecryptfs/len/.ecryptfs/wrapped-passphrase
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# ecryptfs-unwrap-passphrase .ecryptfs/len/.ecryptfs/wrapped-passphrase
Passphrase: 
4b5181e43399feb68abb945fe3a4baee
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [20b203e10c7d07b7] into the user session keyring
Inserted auth tok with sig [cfd18f21d6828f63] into the user session keyring
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# ls .ecryptfs/len/.Private/
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP1pr3gE4rV.oblJsfpKG-WE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP3fpNh7TAnV9E5j3s646PLE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP4Hy1AMJsIHF3iOU4QIHyvk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP4wHBxQAmSyGGUfF-dlQ2JU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP5qgoV6qPy-6389tQV7xXzk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP6jUXS75YfA9vTTalRhZrAE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP6.kk6PNOuPXdvd5MDiBssE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP7wr00zMQnOZy9IdaXYhuh---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP9WzHxBrGMjASXAeqeVvkmk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPa2AqGq7C.1OLoZc9E5WyLE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPADL2ml5IfjVkTUefSUJD1U--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPAUjaiog50oPvyaicEI6u.---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPc4jPFZ6TGus6dM0wNLyEN---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPCf8l15XqUjHK1JKBxFXDfk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPcfpdZHYsElQN.S2EX0ZJ1---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPCOQYNYjQs2kd4sRIV9OYEE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPcXN9.622ywQ03mRvt.nnPE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPDv8Vqt0Qg-S2YwxqjorIsE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPEFkdQtklgKj-xb0Qk9wUGU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPF3NQnuXhSOT5iN-oakNdrE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPFABBZufhLRgzkwyMQvnu3U--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPG1hefLyE5otT-0zkPWFkkU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPgIJ5hFU7i-UJNLK8k2y55E--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPhFZJo5IbPwF5n0qVfhiLR---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPhKpJafenB4OE7xwtDw9Iak--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPif-4CcC3ROkd0.3YTZoHZk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPIjAArFbnrZwtpZ1Y4BqeRE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPis4PC8gKrzGGLd.SbmZyHE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPjPmJtrtNbhnAoLsA8TCOO---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPKF5l650jmiFfD99W0QLdaE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPkH2zDAEiswiLPfzp51e8T---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPL9uveK0jreB4rx.sLH1cbk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPlEql3lgB.-qsgRkQWhkc2U--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPM-cvyrIWEtVUI79B6eRNvk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPMGfyjmZ3FI3AYtY2VSqbEU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPmiqkz-TPhsXM3aa5M3wN7E--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPMzcjn3bTXC3NV0UoGDOdg---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPNbQVKomef2ZQ766R6h3Nlk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPOFW8tVywWLzYMo146uInHk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPoMclsAAa2ugYa7okskrsK---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPoVqB-5-TVMg9EUL0qCtam---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPq97XpsmJo-HhuC8xVWRA1k--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP.qody5m-NCPJqF4cZg3oyU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPQwXJqbEtCKKyCm6ayValsU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPQYV85NVi9MKSXmi2zJ7a2U--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPRJzpaXCyYc24zSuRb4sATE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPrNQp31TUAOOhZyFRttVwkU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPtSwbcwejZ5lE8nYCUTr4ZE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPTX2uZV0dBUUOOPmJ0g5z4---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPUte0bxuZsa07fPQteM3Xp---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPV2hfKUffmn.OtGJ9HBcREE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPvG5IcdgMXs4a0JZjUiauZU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPVW8MpFth5aXSbGtwBhixDk--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPwjbf7VWkKRcfAvX09QXwaE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPx8qzjUVZTkhkVlDg3I6b8E--
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPy456fM5I01vcZIuaLvLat---
ECRYPTFS_FNEK_ENCRYPTED.FWZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPZqUDEXHpRqutcLzyZ0fMJU--
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZP6sqa1BYHM1rHB.q24NeDXUgTiFnIDRZZ327S9DWNzhA-
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPs7VYJZDt9ln2-ZxxpL6AlpubwyWeNThmRlgSUv6dZ9I-
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPvjMBdYRBLXRU-cfJTINiQIxsQ0cR4-G6T3LxPw.gtWY-
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPzKPB5.TVn4bCtXWNweGo4EtsMPqt-WAQ0Loq.l1q1r--
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPzKPB5.TVn4bCtXWNweGo4M-U0mgg0.nV--kVTJv1NjA-
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPzKPB5.TVn4bCtXWNweGo4PQdiljBF.JVYm3bjSzy5mc-
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPzKPB5.TVn4bCtXWNweGo4QN62pUHjCXlitnfhFu2htk-
ECRYPTFS_FNEK_ENCRYPTED.FXZ16Jew45yud-R.xg3Itpbw-59C4zfPuAZPZRDHXJBwKNIPEgHMjFjDnRI3dI7z0K0V3594HTkelsA-
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# mkdir /mnt/Private
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# mount -t ecryptfs .ecryptfs/len/.Private/ /mnt/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
[COLOR=Red]Filename Encryption Key (FNEK) Signature [20b203e10c7d07b7]: [/COLOR]
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=20b203e10c7d07b7
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=20b203e10c7d07b7
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Aborting mount.
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# 

Many many thanks again

---

### Post by KIAaze on 2010-09-24
You forgot to enter the filename encryption key ("cfd18f21d6828f63" in your case) and used "y" instead of "yes" to answer the last question.

_Tip:_ You can select the passphrase and filename encryption key by double-clicking on them and paste them using the middle-button of the mouse.
This avoids errors. The pasting will not be visible (just like when you type it by hand, at least for password-like things), but it will work.
(standard copy/paste using the context menus works too)

Here's what you should have entered:
```
root@ubuntu:/media/276bb0d7-095a-4d6c-ad20-75a292b46823# mount -t ecryptfs .ecryptfs/len/.Private/ /mnt/Private
Passphrase: **4b5181e43399feb68abb945fe3a4baee**
Select cipher: 
1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
1) 16
2) 32
3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: **y**
Filename Encryption Key (FNEK) Signature [20b203e10c7d07b7]: **cfd18f21d6828f63**
Attempting to mount with the following options:
ecryptfs_unlink_sigs
ecryptfs_fnek_sig=20b203e10c7d07b7
ecryptfs_key_bytes=16
ecryptfs_cipher=aes
ecryptfs_sig=20b203e10c7d07b7
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : **yes**
Would you like to append sig [20b203e10c7d07b7] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : **no**

```

P.S.: I improved my previous post in case you still have problems. ;)

P.P.S.: Since you posted your passphrase here in clear text, you should probably change it once everything is OK again. I don't know about the filename encryption key. (I currently have no idea how to do this.)

For backing up or copying the data you can use the "cp" command.
ex:
```
cp -r /mnt/Private/* SAFE_LOCATION
```

Alternatively you can launch a file browser with root permissions using:
```
gksudo nautilus
```
or, if you are still as root in the terminal:
```
nautilus
```

---

### Post by ojireland on 2010-09-24
Mr KIAaze,

You are truely a superstar.

I am now your biggest fan and intend to hunt you down and follow you where ever you may go.

No really man, I am so grateful for your help, copying everything over to an ext drive as i type now.

Problem well and truly SOLVED.

Many many thanks to you.

oj

---

### Post by KIAaze on 2010-09-24
Glad it worked. And I also learned a few things from it. :)

Please mark the thread as "solved" ("Thread tools"->"Mark this thread as solved").

_A few tips for the future:_

-**Make external unencrypted backups** of such important data, so you don't loose your job. ;)
(Unless the data is national security stuff or so, it's probably reasonably safe on an external HD or USB stick at home or at work. Put it in a safe if necessary.)

-Make sure you **never loose your passphrase** (which is actually more important than the login password to decrypt it). If you hadn't had it this time, you would probably have been unable to recover the data!
The login password only serves to "unwrap" the wrapped passphrase. Changing the login password does not change the password necessary for unwrapping!
You can get your passphrase with this command:
```

# encrypted home directory
ecryptfs-unwrap-passphrase /home/.ecryptfs/username/.ecryptfs/wrapped-passphrase
# encrypted Private directory
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase

```
To change your passphrase, see "Change your passphrase to mount your encrypted private directory or home" on this page:
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

-You can **encrypt only what's necessary** instead of the whole home directory by creating a private encrypted directory:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

P.S.: I'm still under the Live session actually. I think I never used it for so long before. ^^

---

### Post by thynk on 2010-09-27
I'm having much the same problem, with a small difference.  My /home partition has been set up on a separate mount.  I don't ever recall encrypting /home - but it seems that when upgrading / to 10.10 it's become encrypted.  It's very possible I encrypted the last time I did a new install, probably at 9.04.  

I've gone through this [section]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually") with every possible key phrase I can imagine that I could have used.  

There is no way (that I can tell) to recover what it thinks the pass phrase was as .encryptfs is a link .ecryptfs -> /var/lib/ecryptfs/<user> which would no longer exist.  

Am I borked or is there another way?

---

### Post by KIAaze on 2010-09-27
Looks bad. :(
If you didn't store the passphrase (wrapped or not) elsewhere and your home partition is really encrypted, I don't see how it's recoverable. (You can try to undelete the wrapped-passphrase file, but it will probably not work...)

Are you sure your home partition got encrypted? Is it clearly encrypted when you mount it from a Live-CD?
I find it strange that it would become encrypted by itself. Encryption is not part of a default installation I believe.
It's more likely you did it by yourself when installing 9.04 as you suggested.

"/var/lib/ecryptfs/" indeed seems to have been used for storing the wrapped passphrase in Ubuntu 9.04:
[http://dustinkirkland.wordpress.com/2009/08/06/moving-your-encrypted-home-meta-data-out-of-varlibecryptfs/](http://dustinkirkland.wordpress.com/2009/08/06/moving-your-encrypted-home-meta-data-out-of-varlibecryptfs/)
(I'm no expert, but this Dustin Kirkland looks like the guy to ask if you want to be sure.)

---

### Post by Ryland on 2010-10-27
I want to thank KIAaze for his solution, it saved me a lot of trouble.

I had a file a desperately needed locked in an encrypted home folder and Ubuntu had broken with the "gconfig-sanity-check2 status 256" problem. 

At least now I can reinstall Ubuntu, but I think I will backup before ANY updates!

Thanks again, it's people like you KIAaze that make Linux so great.

---

### Post by ponsel on 2011-04-25
Hey KIAze, you are a genius and you made my day. Thanks a ton dude!

Your steps worked like a charm. I had a confusion as to which passphrase to use for steps after the "starting the real recovery procedure". Finally I used the "wrapped-passphrase" obtained from the previous step and it worked wonders.

thanks again. and again.

---

