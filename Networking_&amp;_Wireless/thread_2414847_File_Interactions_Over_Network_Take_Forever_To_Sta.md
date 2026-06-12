---
title: "File Interactions Over Network Take Forever To Start"
date: 2019-03-16
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2019-03-16
After I went from 16.04 to 18.04, I have been having issues with file interactions over network shares. These delays are inconsistent... I will try to explain what is happening the best I can:

* If I play an .mp4 file from /multimedia drive using VLC, it takes anywhere from 1 to 2 minutes to begin playback.
* If I play the same .mp4 file from the same drive using Videos, playback begins immediately.
* If I play an .mk4 file from the same drive using either Videos or VLC, playback begins immediately.

* If I try to copy a file from my local laptop to any network share, transfer begins immediately.
* If I try to copy a file from any network share to my local laptop using Nemo, transfer takes up to a minute to begin. 
* If I try to copy the same file from the same network share to my local laptop using the cp or rsync, transfer begins immediately.
* If I try to copy a directory from my local laptop to a network share where the same directory exists, merging the two and opting to ignore duplicate files take up to a minute for each file to begin transferring. 

* If I try to add a file to a .zip file that is stored on a network share, the edit fails and the .zip file is corrupted.

I don't have any clue as to why this is occurring. I am including the autofs files text just in case that might be part of the issue? Otherwise, any and all help will be greatly appreciated!!!

auto.master
```

#
# Sample auto.master file
# This is a 'master' automounter map and it has the following format:
# mount-point [map-type[,format]:]map [options]
# For details of the format look at auto.master(5).
#
#/misc	/etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#	"nosuid" and "nodev" options unless the "suid" and "dev"
#	options are explicitly given.
#
#/net	-hosts
#
# Include /etc/auto.master.d/*.autofs
# The included files must conform to the format of this file.
#
+dir:/etc/auto.master.d
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
+auto.master

/mnt   /etc/auto.smb --timeout=300 --ghost

```

auto.smb
```

multimedia -fstype=cifs,rw,uid=derek,gid=derek,file_mode=0775,dir_mode=0775,username=name,password=pass ://192.168.1.15/multimedia

shop_docs -fstype=cifs,rw,uid=derek,gid=derek,file_mode=0775,dir_mode=0775,username=name,password=pass ://192.168.1.15/shop_docs

shop.data -fstype=cifs,rw,uid=derek,gid=derek,file_mode=0775,dir_mode=0775,username=name,password=pass ://192.168.1.15/shop.data

```

---

### Post by SeijiSensei on 2019-03-16
CIFS is not the best technology for streaming.  I don't use VLC, but I've seen other players like SMPlayer display the same behavior you describe when playing files using Windows filesharing. They often make a local copy first before streaming begins.

This never happens to me using [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). If the video files are on a Windows machine, you're probably out of luck.  If they're on a Linux server, with Linux clients, then you should switch to NFS.

---

### Post by rebeltaz on 2019-03-16
This never happened to me back when I was on 16.04. It' only began after switching to 18.04. The reason for samba shares instead of NFS is because the directories have to be accessible via Windows computers as well.

---

### Post by rebeltaz on 2019-04-09
Another clue... VLC will play videos over the network connection just fine until I copy a video from one network directory to another... after that, until I reboot the system, it takes a minute or two before the video will start playing...

---

