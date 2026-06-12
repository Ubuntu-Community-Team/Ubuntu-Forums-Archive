---
title: "Vista/Natty sharing local files/folders"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by DancesWithRobots on 2011-07-21
I can't be the only person who wants to do this--

After running Ubuntu under wubi on my Vista 64 computer and running out of space, I decided to take the plunge and set up a dual boot system.

I backed up my music, documents, pictures, etc to an external drive.  Then I split a 512 drive between Natty and Vista.  Now I have a nice dual booting setup on NT partitions.

I have another 512gig drive installed in the box that both Vista and Natty can see and use.

WHAT I WANT TO DO--

Is set things up so that both OS's can use the media/data folders that are "common" to both.  In other words, both OS's have applications that "know enough" to save/load their files to an appropriate folder--for example, a word processor like MS Word, or LO Writer will typically save, and try to open new documents to "Documents."  Photoshop and Gimp will both attempt to use "Pictures."

I know that attempting to merge Linux Home with MS Users/My_Account would be an exercise in futility and/or madness, but would it be possible to get both OS's to share say, Documents, Pictures, Videos and maybe Downloads?

I know I can cut the user folders in Vista and paste them elsewhere and Vista will take care of the rest.  I've seen, (but not attempted)  a howto that will move my home folder to another drive--But I have my doubts about being able to just drop Windows folders into it afterward.

Can anyone point me to other information?

---

### Post by oldfred on 2011-07-21
I just posted the same info in this thread (#11)

[http://ubuntuforums.org/showthread.php?t=1808634](http://ubuntuforums.org/showthread.php?t=1808634)

You have to mount the partition with fstab and link the folders into /home.

I have some links in the above thread and some do not like (probably including me) do not like making you follow many links. But there are useful other comments also.

[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

Using Firefox or Thunderbird profile.ini
Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by DancesWithRobots on 2011-07-21
THANKS!

I just saw your reply and I haven't even tried the links yet, but I'm about to.

---

### Post by DancesWithRobots on 2011-07-22
OK. . .I must be missing something fundamental here.

oldfred's links led me to here: [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

THAT article described exactly what I wanted to do.

Following the steps with diligence and attention to detail, I find that I don't get 
a "Storage" (quotes mine.  I followed the article except I capitalized my drives, and used the UUID number I got for my "Media" partition.)

But when I boot into Windows, I DO see a "Storage" folder under Media.

When I edit .config/user-dirs.dirs, my changes get saved to .config, but when I reboot, the changes don't take effect, and the edited lines in user-dirs.dirs change to my home folder.

Can someone shine another light on me?

---

### Post by oldfred on 2011-07-22
I have used links not editing of  .config/user-dirs.dirs. 
More like this but Music has to be renamed or deleted first:
ln -s /media/Storage/Music

Post your  .config/user-dirs.dirs and fstab.

---

### Post by DancesWithRobots on 2011-07-22
I know you suggested using symlinks, but while exploring your links I found the how to geek article and since it described exactly what I was looking for step by step, I went with it.

Anyway, here's fstab

[B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d9588364-0326-4df4-bfb0-7ee8f4b3e3cd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aca476c7-c2ae-4da6-8359-676cb0d32336 none            swap    sw              0       0
# storage mount
UUID=4348919C5968822A /Media/Storage/    ntfs-3g        auto,user,rw 0 0 
[/B]
and user-dirs.dirs

[B]# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="/Media/Storage/Download"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="/Media/Storage/Public"
XDG_DOCUMENTS_DIR="/Media/Storage/Documents"
XDG_MUSIC_DIR="/Media/Storage/Music"
XDG_PICTURES_DIR="/Media/Storage/Pictures"
XDG_VIDEOS_DIR="/Media/Storage/Videos"[/B]

---

### Post by oldfred on 2011-07-22
I see you followed their example. I have some minor changes but not sure if they will make any difference.

Note that I do not have / at end of shared and just use defaults as the parameters.
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

After any changes to fstab, run this:
sudo mount -a

If it returns then there are no issues.

I think you did everything the way the example says. Not sure then if newer versions of Ubuntu have changed something.

Do folders you are refering to Music, Documents already existing in /Media/Storage?

That may be it. Did you create a new mount /Media/Storage? The example uses the existing /media note no caps. But you still have to create /media/Storage.

---

### Post by DancesWithRobots on 2011-07-22
No change oldfred, but thanks for trying.

I'm going to do some research on fstab and user-dirs.dirs and symlinks.  (Already did some.  Guess I'll do some more.)  When I manage to solve this, I'll come back and post my solution.

Heh.  Maybe I should flatter myself that I manage to ask the hard questions.

Thanks again oldfred.  You rock.

---

### Post by DancesWithRobots on 2011-07-27
What finally worked for me.

I copied the Windows shortcuts to the ntfs formatted, mounted, storage partition, deleted the links in places, and went through my (so far, very few) applications and set them to use the folders on the storage drive.  Tested by creating, opening and editing documents both ways between both OS's.

---

