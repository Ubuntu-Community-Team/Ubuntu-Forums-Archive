---
title: "Streaming from storage drive"
date: 2020-04-04
forum: Networking &amp; Wireless
---

### Post by Davethehedgehog on 2020-04-04
I have a new computer withe two hard drives - a smallish SSD for system files and regularly accessed documents and a conventional larger hard drive for storage of (mainly) media files. Ubuntu 19.10 came with a sharing/streaming option which I can use successfully for files on the SSD, but not for files on the storage drive, even though I have added the relevant folders to the list to be shared. These folders are all showing as shared and the storage drive is mounted, but I can't see them on either of my smart TVs.
Anyone got any ideas?

---

### Post by CelticWarrior on 2020-04-04
Try changing the mount point. Generally speaking it doesn't work if under /media.

---

### Post by TheFu on 2020-04-04
What protocols do your "smart/dumb TVs" support?  That will be key.  Get out the manual.  Most will support DLNA.

Have you setup a media server to stream the files? Perhaps **miniDLNA** or Kodi or **Plex**?
Have you shared the storage on the network using NFS or CIFS?  CIFS/Samba is usually the best supported. NFS is usually a little easier for Unix-to-Unix connections, but not really supported by TVs.

For example, my Roku has a Plex application, but it won't mount network storage of any sort. No CIFS. No NFS.  Plex is a DLNA server.  My kodi machines running on Raspberry Pi hardware can mount NFS, CIFS, or use DLNA, but I have to setup each connection.  NFS tends to be faster and more stable, so I've set that up in the r-pi /etc/fstab for family photos and videos.  For recorded TV and movies, the DLNA is prettier / more flashy, so people tend to like it.

Our android tablets won't deal with NFS, but they will use DLNA or CIFS. On Android, the programs are either VLC or BubblePnP. Both support CIFS or DLNA.

Our TV tuners are networked, so any device can use any tuner. These are DLNA devices too. 

Ok ... so with all that garbage said. If I were to buy a HDD from Best Buy today, bring it home, connect it to an Ubuntu system to provide network storage for a dumb TV, I'd
[LIST=1]
[*]Let it sit inside the house for a day to become the same temperature
[*]Unbox it, connect it up with dedicated power and USB to the system; USB power is never enough.
[*]Run **sudo -H gparted**  The -H is needed to prevent future issues.
[*]Create a new GPT partition table, at least 1 partition, then format the partition ext4 and give it a LABEL "my-new-8tb"
[*]Close gparted.
[*]Modify the fstab to mount this new storage
```
LABEL=my-new-8tb  /mnt/new-8tb ext4  noatime,errors=remount-r o 0 2
```
[*]**sudo mount -a** to mount it
[*]sudo apt install samba
[*]sudoedit /etc/samba/smb.conf
[*]Add to the bottom of the file:
```
[new-8tb]
  comment = Movies, TV, Music
  hosts allow = 127.0.0.1 192.168.99.0/24
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = yes
  writable = no
```
[*]Restart samba - sudo systemctl restart smbd.service
[*] Go to the TV, see if it shows up in 3 minutes. Probably need to enter the static IP address of the computer, however.
[/LIST]

LABEL= is easier for mounting USB stuff and not as funky as using UUIDs.  Just be certain that the LABEL is unique to the system.
If there are any issues accessing the new storage using the IP address, then I'd run **testparm** on the system to see what settings, exactly, the samba subsystem is seeing.

Newer versions of Windows10 and Samba stopped broadcasting "I'm here, I'm here" about a year ago.  There's something called "zeroconf" which many home devices support. On Ubuntu, that is implemented with **avahi** and should be pre-installed on any ubuntu desktop flavor.  The name broadcast should be "hostname.local", so if your hostname is "hadar", then the avahi/zeroconf name would be "hadar.local".  I vaguely remember seeing a 60-90 second period for the broadcasts to be sent out onto the LAN, but don't quote me. I'm probably wrong.  I don't use avahi.

---

### Post by Morbius1 on 2020-04-04
Are you talking about Settings > Sharing > Media Sharing? 

I have my money on          CelticWarrior's answer at the moment. If you have the second partition mounted under /media/your-user-name that may be an issue since only "your-user-name" will get access. Change your mount point.

---

### Post by Davethehedgehog on 2020-04-05
Thanks for taking the time to reply all. 
Re. Morbius1's question, the answer is yes.
Plenty for me to think about.

---

### Post by TheFu on 2020-04-05
[https://www.omgubuntu.co.uk/2019/10/ubuntu-dlna-media-sharing-server](https://www.omgubuntu.co.uk/2019/10/ubuntu-dlna-media-sharing-server)
says there are issues with the built-in Media Sharing (which uses DLNA). From the article:
> I was able to play a standard def video file (with audio) just fine using VLC on a Chromebook. But HD and FHD videos stuttered a lot, with dropped frames and lost snatches of audio.

Some people where unhappy that media was being shared on an entire subnet: 
[https://www.omgubuntu.co.uk/2019/11/rygel-autostart-media-sharing-bug-ubuntu](https://www.omgubuntu.co.uk/2019/11/rygel-autostart-media-sharing-bug-ubuntu) But that's what DLNA does. It shares media to anyone on the subnet. There isn't any login, no way to setup authentication.

---

