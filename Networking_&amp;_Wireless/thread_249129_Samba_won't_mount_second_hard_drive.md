---
title: "Samba won't mount second hard drive?"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2006-09-02
I have an edubuntu server, to make use of LTSP, with LAMP also installed to serve up some php pages. I use Samba to access the shares and directories from my Ubuntu box. I just added another two hard drives to the server. These show up in fdisk as hdc and hdd. They are both formatted as ext3 on logical partitions creating hdc5 and hdd5. On the server I can mount these as /media/apps and media/video, and can access and read write fine on the server.

On my main hard drive on the server, hda, I have three partitions hda6, hda7, and hda8. I can mount these fine via samba on my Ubuntu box and read write, so samba working all OK for this. By trying to mount either hdc5 (/media/apps) or hdd5 (/media/video) draws a blank, and gives me an error of "Invalid Share Name"

> 6309: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

I mount the shares manually, using this syntax:

>  sudo mount //edubuntuserver/music /media/music -o username=user,password=pass,dmask=777,fmask=777
and this same syntax falls over for the 2nd and 3rd drives
> sudo mount //edubuntuserver/media/apps /media/apps -o username=user,password=pass,dmask=777,fmask=777

My smb.conf is setup like this for the additional drive shares:
> [NewApps]
  comment = Apps Folder
  path = /media/apps
  available = yes
  public = yes
  browseable = yes
  valid users = user
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

I know this is all "wide open" but once I can get it working I can then tie things down a bit

Is there anything special about mounting additional hard drives on the server that I need to attend to, in order to be able to access these paritions on my client Ubuntu? I sense this is less to do with Samba and more to do with filesystems and links?

---

### Post by Jose Catre-Vandis on 2006-09-02
SOLVED!

Why oh why is it that when ever I hit a problem, spend hours searching for the answer, give up, post here, and then a short while later have the cloak of darkness removed from my eyes! You can't see it, but at this very moment, even while typing I am subjecting myself to self harm, in the hope that I will learn from my mistakes and do better next time.:lol:

Anyway, the solution to my problem might help others so I will outline where I had gone wrong, and what I did to fix things. What i was not really aware of, and is not clearly documented in the wikis and howtos is the importance of the SHARE NAME and its connection to the path you indicate in smb.conf. Whenever I have set up samba shares in the past, I have tended to use the same SHARE NAME as the direct path, e.g. [Data] and /Data. So when mounting the share I just use //server/Data and it works. As you will see from my original post I have [NewApps] and /media/apps. When you look up Samba shares in the Shared Folders gui, it tells you the share by the path, i.e. /media/apps, but actually when mounting you need to use the SHARE NAME and not the path (cloak of darkness and idiocy removed :lol:)

So samba works just like Apache aliases in this respect. The mount syntax that didn't work:
> sudo mount //edubuntuserver/media/apps /media/apps -o username=user,password=pass,dmask=777,fmask=777
is changed to:
> sudo mount //edubuntuserver/NewApps /media/apps -o username=user,password=pass,dmask=777,fmask=777
and "hey presto!" I have my share on my Ubuntu Box

This revelation (to me) now seems to obvious, and my backside is now quite sore from the self harm :lol:, but at least I now know what to do next time.

A few useful links to go with this:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html)
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing)
[http://www.ubuntuforums.org/showthread.php?t=244166](http://www.ubuntuforums.org/showthread.php?t=244166)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

---

