---
title: "Mythbuntu using Shared windows files, how?"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Strandli on 2008-06-18
Hi! I'm a very new Linux user, so I have no clue about what I'm doing... So I hope you guys can help me :)

**Scenario**: I have 2 computers in my room.
Com1: The computer I use all the time, with Windows XP. This computer has all my media files and such.

Com2: A computer which is still usable, but is just collecting dust at the moment. This computer had also Windows Xp, and I used this computer as a MediaCenterPC, connected to my tv and surround system.

The situation is: I used local network between Com1 and Com2 to get the files on the "big screen" (com2). But I didnt like the solution, so I decided to install MythBuntu on com2, hoping that would be much easier (and by looking at videos, it looked very sexy). 

Short: Computer#2 doesnt have a big hdd, so I have to get the media files through sharing. But how do I make MythBuntu find the files shared on Computer#1?

(sorry if the post doesnt make much sense, its getting late for me here in Norway...)

Hope someone can help me :)

---

### Post by Shades404 on 2008-08-25
If you install the samba client (smbclient) you should be able to see any shared folders from the windows machine. Obviously this will mean both have to be on.

You could mount the remote directory somewhere, for example /home/mythtv/media, and then add that path to the list of video location in the mythtv client.

However I'm currently trying to do this and although I can run the media files fine across a network (using a player) the mythtv interface hangs for a long while, possibly processing the files in some way. So my solution only takes you so far, someone else will have to give you the rest, or a better way. (I'm using sshfd not samba mind you so you might be okay)

---

