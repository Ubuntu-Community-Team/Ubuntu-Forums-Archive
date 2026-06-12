---
title: "When CIFS shares mounted Ubuntu is super slow and unresponsive"
date: 2014-11-12
forum: Networking &amp; Wireless
---

### Post by ch1mp on 2014-11-12
Hi,

I'm mounting CIFS shares over LAN like this...

```
#!/bin/bash/
sudo mount -t cifs -o "username=uname,password=passw,uid=nnnn,gid=nnnn" //192.168.1.96/Home /media/nas/NAS_Home
sudo mount -t cifs -o "username=uname,password=passw,uid=nnnn,gid=nnnn" //192.168.1.96/Download /media/nas/NAS_Download
sudo mount -t cifs -o "username=uname,password=passw,uid=nnnn,gid=nnnn" //192.168.1.96/Media /media/nas/NAS_Media
```

...where in visudo I'm letting the user run /bin/mount w/o password.

When the shares are mounted launching any application takes more than 20 seconds from either unity launcher, keyboard shortcut, HUD or terminal. If I then unmount the shares everything goes back to being instant (ivy bridge i5 3570K, 8Gb RAM, SSD). 

Anyone have any idea why this might be happening and what I can do to solve this problem?

Thanks,

Tom.

---

### Post by bab1 on 2014-11-13
> **ch1mp said:**
> Hi,

I'm mounting CIFS shares over LAN like this...

```
#!/bin/bash/
sudo mount -t cifs -o "username=uname,password=passw,uid=nnnn,gid=nnnn" //192.168.1.96/Home /media/nas/NAS_Home
sudo mount -t cifs -o "username=uname,password=passw,uid=nnnn,gid=nnnn" //192.168.1.96/Download /media/nas/NAS_Download
sudo mount -t cifs -o "username=uname,password=passw,uid=nnnn,gid=nnnn" //192.168.1.96/Media /media/nas/NAS_Media
```

...where in visudo I'm letting the user run /bin/mount w/o password.

When the shares are mounted launching any application takes more than 20 seconds from either unity launcher, keyboard shortcut, HUD or terminal. If I then unmount the shares everything goes back to being instant (ivy bridge i5 3570K, 8Gb RAM, SSD). 

Anyone have any idea why this might be happening and what I can do to solve this problem?

Thanks,

Tom.

Is this a script?  Why is the shebang line )#!/bin/bash/) up there?  If it is a script that line should not end in a /.

I don't think you should use quotes around the options (-o) parameters.  It is enough to use```
mount -t cifs -o username=uname,password=passw,uid=nnnn,gid=nnnn //192.168.1.96/Home /media/nas/NAS_Home 
```...in a script.  There is no need to use sudo in the script either.  The script should be owned by *root:root * and thus need *sudo <script>*.

Visudo edits the sudoers file.  Are you saying you edited the sudoers file to allow the user to mount the partition?  You can use the option user(s) in the fstab file and mount the partition by a script available to all with no need for sudo at all.  See below re the user(s) option from the man pages```
 The non-superuser mounts.
              Normally, only the superuser can mount filesystems.  However, [B][COLOR="#0000FF"]when  fstab  contains
              the user option on a line, anybody can mount the corresponding system[/COLOR][/B].

              Thus, given a line

                     /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

              any user can mount the iso9660 filesystem found on his CDROM using the command

                     mount /dev/cdrom

              or

                     mount /cd

              For  more  details,  see  fstab(5).   Only  the  user that mounted a filesystem can
              unmount it again.  [B][COLOR="#FF0000"]If any user should be able to unmount, then use users instead of
              user  in  the fstab line.[/COLOR] [/B] The owner option is similar to the user option, with the
              restriction that the user must be the owner of the special file. This may be useful
              e.g.  for  /dev/fd  if  a login script makes the console user owner of this device.
              The group option is similar, with the restriction that the user must be  member  of
              the group of the special file.

```

So what are you trying to do?  Create a script or mount a partition via the terminal by a non-root user or ...?

---

### Post by ch1mp on 2014-11-14
Hi Bab1,

Thanks for the reply and the bash tips :)

I am calling this script and an unmount script from upstart to moutn and unmount NAS shares as different users log in and out. The shares change depending on the account you log in to the NAS on in terms of Home folder, quota and obviously permissions too. The upstart scripts run as the user, which means I can be sure I'm logging them in using the right account but also means I have to allow mount and umount to run as sudo w/o password for the users.

That all works fine. Apart from switching users doesn't seem to run the unmount script, but that's a different question. My problem with the system running slowly was in the end due to just one account having fonts cached (lots of them) from the remote location which just brought ubuntu to it's knees. 

I found this after seeing the NAS_Home would not unmount, then asn lsof | grep NAS_Home brought up tons of fonts being used by different apps all on the NAS share. Not sure how that happened but I "fixed" it by changing the mount location and clearing the fontconfig cache folders and doing fc-cache -f -v. Everything seems back to normal for that user now.

So, long story short, this issue is solved and it was to do with fonts over the LAN, not how the shares were mounted.

Thanks again,

Tom.

---

