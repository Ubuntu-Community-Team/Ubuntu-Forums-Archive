---
title: "NFS mounts post upgrade to ubuntu 14.04 LTS"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by Flaggmann on 2014-07-01
I have a home network that I have set up to have a main server for most server functions and shares. This is serverhost1. The backup server is actually a workstation, host1 but it is set up to function as a backup server since it sees little use as a workstation on a daily basis. I use a common fstab file for all workstations and only customize it when absolutely necessary. All workstations run nfs-kernel-server and export a single misc workstation nfs share. host 1 has a number of extra shares to serve as backup share server. Host1 is also where the main home folder is fo all w/s's to eliminate duplication. As an example a single email local folders file is maintained there and any other w/s use that share as a common email local folder so that no matter what w/s in what part of the house is being used the same local folders make emails available anywhere by the main user.

All workstations use a common /media/nfs-client/host  folder structure to mount the shares in. All also mount their own shares to prove the export is working.

It all worked well until I changed to ubuntu 14.04 LTS on the host1 (backup server workstation). To this point I have managed to get host1 to mount and serve data 
to itself, however I am unable to see/use any data when in the mounted /media folders of shares in other workstations on the network. For example I can mount -a in any other host (host2 and above) and the root prompt will return to normal, the newly mounted icons will show on the desktop (all with no error messages) but only one export will have data in it. All the rest are blank. The linking of the home video files to the /OPT folder allows minidlna to run and keep running but is unable to serve data files as none show. If I change the mindlna conf file to look and the video share mount then it complains of user/group/ownership permission errors.
The only way I am able to get any of the shares to mount successfully is by changing the exports file by commenting all shares out except one, then changing the "nohide" property to "fsid=0" and then service nsf-kernel-server restart. Then remounting the client host in question. It then works normally but only for the single share.
Setting it up as shown below in EXPORTS and exportfs section, will not mount any except the one.

according to posts using google I am supposed to export the root virtual export folder with fsid=0 and read only, then all other shares with the nohide option; and although they appear to mount and show icons on desktop, there is no data provided.


the individual host mounts at the end mount sporadically some do and others simply time out or produce the must be mounted by root error when mount -a is even done by root.

the last two serverhost1 mounts appear to create a mounted icon with folders within yet no files are mounted and the file folders don't match what is set up by that pc's exports file. 

The problem seems to be related to either the fsid=0 spec or else the fact that the original bind mounts are done with ntfs-3g; but they all worked in the original ubuntu 12.04 LTS setup prior to upgrade.
[SIZE=5][COLOR=#0000ff][I][B]
UPDATE symptom clue:[/B][/I][/COLOR][/SIZE]

dolphin gives error indication "unable to enter folder" when accessing files. mounts appear normal but no data



Any help would be appreciated; thanks

all cpus are 64 bit ubuntu 12.04 LTS save one Linux Mint 15 Olivia; and the new host1 ubuntu 14.04 LTS; main server is ubuntu server also 64 bit all have minimum 2GB RAM
and at least i3 CPU
 
 



> 
**#HOST1(BACKUP NFS SERVER W/S;  (serverhost1 is main server) NFS CLIENT /ETC/FSTAB**

# /dev/sda3
UUID=ident1 /media/ntfs-shares     ntfs-3g defaults 0 0
# /dev/sdb1
UUID=ident2 /media/nfs-client/host1/sdb_500gb_ntfs     ntfs-3g defaults 0 0        #{mounts drive to it's host1 filesystem media folder location}
# /dev/sdc1
UUID=ident3 /media/nfs-client/host1/sdc_300gb_ntfs     ntfs-3g defaults 0 0        #{mounts drive to it's host1 filesystem media folder location}
# /dev/sdd1
UUID=ident4 /media/nfs-client/host1/sdd_1tbNTFSvids     ntfs-3g defaults 0 0        #{mounts drive to it's host1 filesystem media folder location}

/srv/nfs/host1                  /exports/host1      nfs rw,bind 0 0     #{Misc host1 export share}
/home/userID                      /exports/userID     nfs rw,bind 0 0     #{links user home directories so export does not export home directly}
/media/nfs-client/host1/sdd_1tbNTFSvids     /exports/videos     nfs rw,bind 0 0     #{linked to media folders by direct UUID mounts above & linked to exports}
/media/nfs-client/host1/sdb_500gb_ntfs         /exports/sdb_500gb_ntfs nfs rw,bind 0 0        #{linked to media folders by direct UUID mounts above & linked to exports}
/media/nfs-client/host1/sdc_300gb_ntfs         /exports/sdc_300gb_ntfs nfs rw,bind 0 0     #{linked to media folders by direct UUID mounts above & linked to exports}
/media/nfs-client/host1/sdd_1tbNTFSvids      /opt             nfs rw,bind 0 0     #{copies vid files to default minidlna folder to alleviate minidlna 
                                                #user/groups permissions problem}

192.168.120.10:/exports/userID                    /media/nfs-client/host1/dadhome               nfs defaults 0 0
192.168.120.10:/exports/client-host1                /media/nfs-client/host1/host1                nfs defaults 0 0

> **BACKUP SERVER HOST 1 /ETC/EXPORTS**
/                            192.168.120.0/24(ro,fsid=0,insecure,no_subtree_check,async)    #NFS4 virt server root
/exports/userID/               192.168.120.0/24(rw,nohide,insecure,no_subtree_check,async)
/exports/client-host1/        192.168.120.0/24(rw,nohide,insecure,no_subtree_check,async)
/exports/sdb_500gb_ntfs/        192.168.120.0/24(rw,nohide,insecure,no_subtree_check,async)
/exports/sdc_300gb_ntfs/        192.168.120.0/24(rw,nohide,insecure,no_subtree_check,async)
/exports/videos/                192.168.120.0/24(rw,nohide,insecure,no_subtree_check,async)

> 
**BACKUP SERVER HOST 1 exportfs  return**
/                 192.168.120.0/24
/exports/userID
        192.168.120.0/24
/exports/host1  
        192.168.120.0/24
/exports/sdb_500gb_ntfs
        192.168.120.0/24
/exports/sdc_300gb_ntfs
        192.168.120.0/24
/exports/videos
        192.168.120.0/24


> [B]##FSTAB addons For Other W/S's NFS CLIENT ##
[/B]
192.168.120.10:/exports/userID                        /media/nfs-client/host2/dadhome                   nfs defaults 0 0
192.168.120.10:/exports/host2                          /media/nfs-client/host2/host2                     nfs defaults 0 0
192.168.120.10:/exports/sdb_500gb_ntfs                /media/nfs-client/host2/sdb_500gb_ntfs            nfs defaults 0 0
192.168.120.10:/exports/sdc_300gb_ntfs                /media/nfs-client/host2/sdc_300gb_ntfs            nfs defaults 0 0
192.168.120.10:/exports/videos                        /media/nfs-client/host2/sdd_1tbNTFSvids           nfs defaults 0 0

192.168.120.11:/srv/nfs/host3                /media/nfs-client/host3/host3                    nfs defaults 0 0
192.168.120.12:/srv/nfs/host4                 /media/nfs-client/host4/host4                  nfs defaults 0 0
192.168.120.3:/srv/nfs/host6                 /media/nfs-client/host6/host6                   nfs defaults 0 0
192.168.120.18:/srv/nfs/host5                /media/nfs-client/host5/host5               nfs defaults 0 0
192.168.120.4:/srv/nfs/host7                 /media/nfs-client/host7/host7               nfs defaults 0 0
192.168.120.16:/srv/nfs/host8                 /media/nfs-client/host8/host8                 nfs defaults 0 0
192.168.120.2:/opt                         /media/nfs-client/serverhost1/serverhost1media        nfs defaults 0 0
192.168.120.2:/srv/nfs/serverhost1                /media/nfs-client/serverhost1/serverhost1         nfs defaults 0 0

---

### Post by TheFu on 2014-07-02
Have you tried manually mounting from the shell to troubleshoot?

What about simplifying the config for 1 server and 1 client?

What do the log files say on both the client and server? There must be errors, right?

Don't have any 14.04 NFS servers here ... just clients. The client is working, unchanged to a 12.04 server with autofs.  I use autofs for remote mounts.

I don't like putting my mounts under /media ... that is where temporary stuff that the OS handles gets placed, isn't it? Anyway, never wanted to tempt fate by mixing my control with the OS.

Not that I'm going to be any more help, but if you could wrap all that file data in  "code tags", things would line up better and it would be easier to read (for me at least).

---

### Post by Flaggmann on 2014-07-02
does that help; I wasn't aware of the quote/code tags protocol. Thanx for that tip. 

As for comments about 1 server and one client; as I indicated at the outset single mounts worked; when I go to multi mounts is when the troubles begin to show. Unless someone from nfs project comes out and states one can't do what I do because it is not possible I should be able to do it and not have to do workarounds because they are simpler.

 As for the /media comments, that is where ubuntu defaults to mount new shares or USB drives etc. I just continued the custom as it makes it easier to relate to ubuntu help forums using their defaults

---

