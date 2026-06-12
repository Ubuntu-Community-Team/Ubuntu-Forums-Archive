---
title: "[SOLVED] fstab changes in Hardy?"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by kbailey on 2008-05-13
In order to make my network drive (Windows share) visible to the Mediatomb GUI and to my backup software, I used following fstab entry in Gutsy and it worked flawlessly:

```
//201.80.10.103/Media /home/anne/KNetMedia   smbfs  auto,username=anne,password=,uid=1000,umask=000,user   0 0
//201.80.10.103/OfficeBU /home/anne/OfficeBackup   smbfs  auto,username=anne,password=5566,uid=1000,umask=000,user   0 0
```

Since upgrading to Hardy, these folders no longer mount on startup. After yesterday's round of updates, I can access them manually via "Connect to Server" and by browsing my network, (being unable to do that was a known bug that has since been fixed in this release) but I need them to be mounted as folders on startup in order for other software to "see" them.

Any advice on how to get this working again will be greatly appreciated. :)

---

### Post by njparton on 2008-05-13
Maybe an obvious question, but are the username's, passwords and uid's listed above still correct?

---

### Post by kbailey on 2008-05-13
After having messed up on that one in the past, there are no obvious questions. ;-)

Yes, the usernames, passwords and uids must be correct, as I haven't changed anything on the network drive and the move to Hardy was through an upgrade, not a fresh install.

I can still access the drives through the network icon in "places" or via "connect to server" with no user name or password being entered for the "Media" drive and the old password being entered for "OfficeBU". They just won't mount on startup the way they did before the upgrade.

Thank you very much for the suggestion. :-)

---

### Post by njparton on 2008-05-13
I think fstab is a little different in hardy compared to gutsy as I was helping a guy with a DVD drive problem yesterday after an upgrade.  Removing the DVD entry from his fstab file, the kernel still mounted the drive.  I don't think that would have happened with gutsy (?).

My only suggestions would be to do a clean install or to research this issue on the wider web in relation to the current kernel used by ubuntu.

---

### Post by BlueSkyNIS on 2008-05-13
I think that the HAL is doing all the mounting now, fstab is used only for root, swap partitions (my opinion only).

EDIT: Is there any error message when you try to mount e.g "//201.80.10.103/Media" manually in  terminal?

---

### Post by kbailey on 2008-05-13
Thanks again for the input, nj. A reinstall is usually my solution to everything, though I don't have time for that this week.

BlueSky, I can access the shares via the network icon in "places" and by using the "connect to server" gui. At that point, I can read and write to the drive, but other software (ie. MediaTomb) cannot use it through their guis.

I'm not certain what command to use to mount this drive via terminal and don't have much time today to research and learn. If you could provide a suggestion, I would truly appreciate it and will post my results, hopefully helping others with the same issues.

What a great community!

---

### Post by BlueSkyNIS on 2008-05-13
well, I don't have any experience with network drives in linux, but here it goes: try to manually do the mount, type

```
mount //201.80.10.103/Media
```

and if fstab has all options correct mount will do its stuff, else it will say where the error is.

Maybe, you should also add _netdev option in fstab :?:

---

### Post by wjhobbs on 2008-05-13
I was having similar problems. My smbfs mounts worked in Gutsy but failed after upgrading to Hardy.

After a week or so of tearing out what little hair I have left and searching the forums, I discovered that I needed to install libpam-smbpass for Places > Network to see my Windows network and provide access to the shares. But I was still unable to save mail attachments etc. directly to the shares.

I still needed to have fstab do a proper mount. What worked in Gutsy was something that looks like this:

```
//chryxus-ca/imsig_data /home/jhobbs/chryxus_data smbfs rw,username=jhobbs,password=xxxxxxxx,uid=jhobbs,gid=imsig-mgmt 0 0
```

My samba shares are hosted on a Centos-based system with authentication. (Since I am the sole user on this machine I'm not worried about having the credentials visible. But I'll fix that soon.)

Well some of my forum browsing told me that smbfs had been replaced with cifs, so tried that change. But no change in behavior. I tried a number of different option changes that seemed indicated in different forum posts. But no success.

Then I tried a manual mount as BlueSkyNIS suggested (mount //chryxus-ca/imsig_data). And an error came back to say that the gid "imsig-mgmt" was not valid! But I knew it was valid for my samba server machine because this had worked under Gutsy.

But then it occurred to me that the new functionality in libpam-smbpass might be passing a different set of credentials from Hardy to my samba server. So I added a group "imsig-mgmt" to my Hardy box and added my user id to the group and tried the manual mount again.

It worked!!

Thanks to BlueSkyNIS for showing how to get the diagnostic message that pointed me in the right direction.

I have changed the fstab entries to use cifs instead of smbfs -- but everything else is the same. Adding a matching group to the Hardy machine was all that was needed.

Hope this helps someone.

---

### Post by BlueSkyNIS on 2008-05-13
Well I am glad you solved the problem :)


Cheers \\:D/

---

### Post by TonyS on 2008-05-13
Hi wjhobbs,

Could you detail exactly what you mean by "adding a matching group"?

Thanks!

Tony

---

### Post by kbailey on 2008-05-14
BlueSky, when I try to manually mount the drive, I get:
mount error 20 = Not a directory

After some searching the 'Net, this seems to be a common problem with many recent distributions, though I haven't found the fix yet. wjhobbs gid situation does not seem to apply to me.

Does anybody have an idea WHAT exactly is "not a directory"? Is it referring to the mount point (home/anne/KNetMedia) or the share (201.80.10.103/Media)? Both folders exist.

Thanks again folks!

---

### Post by BlueSkyNIS on 2008-05-14
I think it is reffering to what you have typed into the terminal.

Well I'm lost here, as you know I have no experience with network drives in linux... :(

You may try this [**link**]("http://www.linuxquestions.org/questions/linux-networking-3/mount.cifs-mount-error-20-not-a-directory-443693/"), maybe it helps.

---

### Post by wjhobbs on 2008-05-14
From TonyS:
> Could you detail exactly what you mean by "adding a matching group"?

On my samba server there is user id 'jhobbs' set up. The security for share access is arranged based on group membership -- permission settings. On the server, user 'jhobbs' is a member of group 'imsig-mgmt' and several shares allow rw access to members of that group. 

These credentials were supplied in the fstab entry and were sufficient in Gutsy to allow my shares to be mounted on my Gutsy client box. (Note: I use the names and not the id numbers. The corresponding numbers on the client are not likely to match those on the server.)

When I upgraded to Hardy, it seems that some of these credentials, as specified on the fstab entry, are being ignored. Instead, credentials are being supplied by the new libpam-smbpass package. It gets its information from your userid and password on the Hardy box. It also seems to send gid membership as well.

Since the passed credentials must match what is specified on the server, I set up a group on the Hardy client that was named the same as the relevant group on the server (imsig-mgmt) and made the client user 'jhobbs' a member of that group -- on the Hardy client.

Now when the Hardy client tries to mount the samba share, the credentials on the client match the settings on the server and the share can get mounted.

Hope that helps to clarify.

---

### Post by kbailey on 2008-05-15
Thank you, both wjhobbs and BlueSkyNIS. Your help is truly appreciated and I shall muddle through this as I have time over the next few days.

Cheers.

---

### Post by avpap on 2008-05-15
It is a known bug and Canonical must solve it as faster as possible. Ubuntu is losing points with that one!!

---

### Post by BlueSkyNIS on 2008-05-15
> It is a known bug and Canonical must solve it as faster as possible. Ubuntu is losing points with that one!!

I didn't know this is a bug, I thought they just changed the way how these things work in hardy.

---

### Post by BlueSkyNIS on 2008-05-15
They have similar problem: [**link**]("http://ubuntuforums.org/showthread.php?t=790799")

---

### Post by JonC_6.06 on 2008-05-15
I had a similar problem with fstab mounting a second hard disk. It turned out the upgrade from Gutsy to Hardy removed the directory I made in /media which happened to be where my disk was trying to mount to. After re-creating it and reapplying permissions it worked fine.

Jon

---

### Post by JonC_6.06 on 2008-05-15
Maybe I should have read your previous posts before posting that comment!

---

### Post by kbailey on 2008-05-16
OK, after spending a couple more hours of research and testing, the network drive mounts at startup! :-)

Thank you to everybody who's replied and to [email]jm_wsb@hotmail.com[/email] for posting this [bug report]("http://ubuntuforums.org/showthread.php?t=741124&page=2") which shows the actual fix. Dmizer's [mount windows/samba shares how-to]("http://ubuntuforums.org/showthread.php?t=288534") was also a great help.

Here's my new fstab entry that works:

```
//201.80.10.103/Media    /home/anne/KNetMedia        cifs    guest,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The entry that made things work is "nounix".

The only problem now is that Ubuntu hangs for a while on shutdown because it cannot seem to unmount the network drive quickly. I saw a post and solution for this in dmizer's how-to and will follow up here with the fix for that.

---

### Post by kbailey on 2008-05-16
The following commands (creation of symbolic links to scripts already in Ubuntu) work perfectly to unmount any shares during a shutdown or restart. They were posted [here]("http://ubuntuforums.org/showthread.php?t=293513&page=5") by wyley.r.

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```

You'll need to execute them as "root" or prefix them with "sudo".

Thanks again to everybody who contributes to this community. :-)

---

