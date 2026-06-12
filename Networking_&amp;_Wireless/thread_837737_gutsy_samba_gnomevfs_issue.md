---
title: "gutsy samba gnomevfs issue?"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by FishRCynic on 2008-06-22
asus1@m2npvvm:~$ totem
JACK tmpdir identified as [/dev/shm]
** Message: Error: Could not read from resource.
gstgnomevfssrc.c(703): gst_gnome_vfs_src_create (): /play/source:
Failed to read data: Invalid parameters

after almost a year of totem reading avi files from various sources and playing them over the network on both amd64 and i386 flavours of gutsy,
Suddenly today (could be as long as a week as i don't get to play that much anymore) the above pops up on all of them (read two x64 systems and two i386 sytems) when totem tries to play a file over the network (samba shares).
other files can be accessed without an issue.
creating a mount point, using direct ip address does not change this behaviour.

mplayer works though just fine. 

interestly enough a windows xp share will work.
asus1@m2npvvm:~$ totem
JACK tmpdir identified as [/dev/shm]
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
JACK tmpdir identified as [/dev/shm]

*** just to be clear *.avi will not play 

*.mp3 works
*.vob works



i know i have applied gutsy updates recently (i believe some samba and even gvfs were involved) and this is shall we say more than a little annoying.

it appears that two hardy machines are also exhibiting this behaviour.
are there new configuration settings for samba shares to be invoked?

point of interest - xp machines can read and play files with no problem as well

---

