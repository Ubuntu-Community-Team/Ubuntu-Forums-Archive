---
title: "can't make $USER own $HOME ?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by tlroche on 2009-07-10
summary:

$ echo $USER
tlroche
$ ls -ald $HOME
drwxrwxrwx 1 root root 24576 2009-07-10 16:00 /home/tlroche

and I am unable to save my ubuntu and application sessions. However I can't fix this via chown/chgrp, even from recovery mode. How to fix?

details:

I have a box with 1 physical HD and 1 DVD. It came with winXP, so I made separate partitions for windows (c:) and everything else (e:, since the DVD is d:). For historical reasons one backed-up path on e: gets subst-ed to t:. I immediately put cygwin on the box. My cygwin and winXP (and ubuntu, below) usernames are all 'tlroche' and my cygwin mounts are all like /[drivename] (e.g. "/c", "/e", "/t"), hence my cygwin $HOME==/home/tlroche==/t/tlroche==t:\tlroche==e:\...\tlroche

Awhile back I heard about wubi, so I used that to install xubuntu on this box, but I haven't used that install much. Recently I decided to try to migrate from cygwin to ubuntu. (My cygwin is pretty extensively customized, and I'd like to be able to reuse that work.) Accordingly in xubuntu I

0 made paths (more about this below), e.g.

root@tlroche-laptop:/root# mkdir -p /t/tlroche

  which worked

1 mounted those paths, e.g.

root@tlroche-laptop:/root# mount --bind "/media/e/tlroche/backups/t_drive/tlroche" "/home/tlroche"

  which worked

2 automounted those paths: added those paths to my fstab, tail of which is like

/media/e/tlroche/backups/t_drive /t none bind 0 0
/media/e/tlroche/backups/t_drive/tlroche /t/tlroche none bind 0 0
/media/e/tlroche/backups/t_drive/tlroche /home/tlroche none bind 0 0

3 restarted (`shutdown -fr now`)

After logging in, I

0 was warned

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

1 was required to relogin to my wireless

2 was required to reset the password on my keychain

3 ran `emacs`, which picked up my .emacs

On verifying my automounts, I noticed

tlroche@tlroche-laptop:~$ ls -ald $HOME
drwxrwxrwx 1 root root 24576 2009-07-10 16:00 /home/tlroche

(which no doubt resulted from making the paths as root) as well as other problems. I assumed the cause of my problems was that my $HOME needed to be owned by me, so I initially tried to fix that via

root@tlroche-laptop:/root# chown -R tlroche /home/tlroche
root@tlroche-laptop:/root# chgrp -R tlroche /home/tlroche
root@tlroche-laptop:/root# ls -ald /home/tlroche/
drwxrwxrwx 1 root root 24576 2009-07-10 14:54 /home/tlroche/

I then rebooted and tried doing the same thing from recovery mode, with no difference in outcome.

What am I doing wrong? How can I fix this?

---

### Post by tlroche on 2009-07-10
some additional notes:

* I network-upgraded my ubuntu to 9.04 before attempting the above.

* my cygwin is up-to-date as of a week ago.

* cygwin still works (I'm using it now), and reports

$ ls -ald $HOME
> drwxrwxrwx+ 53 tlroche None 0 Jul 10 17:35 /home/tlroche
$ cygpath -w $HOME
> t:\tlroche

---

### Post by Mornedhel on 2009-07-10
You're mounting a directory without the user option, which means it will automatically be owned by root. It's possible that even if you do manage to chown it back to tlroche somehow, it will be back to being owned by root when you reboot.

Disclaimer : I am not an fstab expert, may be completely wrong as to why it's owned by root, and adding the "user" option may not solve your problem.

---

### Post by JillSwift on 2009-07-10
It appears to me that you are mounting an NTFS volume as your home directory.

This won't work, as NTFS does not support Linux's security/access control. Any NTFS mounted on your linux filesystem volume will appear to be owned by root:root and have full global permissions (777).

I suggest mounting the NTFS partition as a sub-directory in your home folder, ie:

/home/tlroche/DriveT/

And have your linux home directory just for your linux config & preferences stuff.

---

### Post by tlroche on 2009-07-17
> **JillSwift said:**
> It appears to me that you are mounting an NTFS volume as your home directory.

Almost correct: I'm just mounting _part_ of an NTFS filesystem.

> **JillSwift said:**
> This won't work, as NTFS does not support Linux's security/access control.

I assumed part of 'NTFS support' involved working around this--doh!

> **JillSwift said:**
> I suggest mounting the NTFS partition as a sub-directory in your home folder, ie:

/home/tlroche/DriveT/

And have your linux home directory just for your linux config & preferences

Thanks! This seems to be working. I mounted the cygwin:/home/tlroche as linux:/home/tlroche/DriveT, and then

[LIST=1]
[*]got emacs working. The easy part was symlinking ~/.emacs.d -> ~/DriveT/.emacs.d, but some of emacs (notably bookmarks and desktop) really wants to have files in ~, so I made additional symlinks in ~/ as required.
[*]got firefox working. This would have been trivial, except that I had already firefox-3.5 on XP, but 3.5 is not yet fully supported on Jaunty. After getting Shiretoko setup on my xubuntu, I just symlinked ~/.mozilla/firefox-3.5/myFirefoxProfile to ~/DriveT/.../myFirefoxProfile and added to ~/.mozilla/firefox-3.5/profiles.ini the stanza

> [Profile1]
> Name=myFirefoxProfile
> IsRelative=0
> Path=/home/tlroche/.mozilla/firefox-3.5/tlrocheOnT
> Default=1
[/LIST]

Now I'm working pretty much full time on xubuntu wubi, but I can still bail occasionally.

---

### Post by iamkrazee on 2009-07-17
Just out of curiosity, how'd you get onto root? Do you have that enabled? 

IMO, ntfs not supporting the ext-fs security features makes it better for you in particular. Because anything and everything is accessible when you're using the right driver.

---

### Post by JillSwift on 2009-07-17
> **tlroche said:**
> Almost correct: I'm just mounting _part_ of an NTFS filesystem.



I assumed part of 'NTFS support' involved working around this--doh!



Thanks! This seems to be working. I mounted the cygwin:/home/tlroche as linux:/home/tlroche/DriveT, and then

[LIST=1]
[*]got emacs working. The easy part was symlinking ~/.emacs.d -> ~/DriveT/.emacs.d, but some of emacs (notably bookmarks and desktop) really wants to have files in ~, so I made additional symlinks in ~/ as required.
[*]got firefox working. This would have been trivial, except that I had already firefox-3.5 on XP, but 3.5 is not yet fully supported on Jaunty. After getting Shiretoko setup on my xubuntu, I just symlinked ~/.mozilla/firefox-3.5/myFirefoxProfile to ~/DriveT/.../myFirefoxProfile and added to ~/.mozilla/firefox-3.5/profiles.ini the stanza

> [Profile1]
> Name=myFirefoxProfile
> IsRelative=0
> Path=/home/tlroche/.mozilla/firefox-3.5/tlrocheOnT
> Default=1
[/LIST]

Now I'm working pretty much full time on xubuntu wubi, but I can still bail occasionally.
Yay! Hope you find it fun and useful =^_^=

---

