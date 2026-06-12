---
title: "Sharing tool creates incompatible permissions"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by swerdna on 2008-01-24
Hello, I'm a newbiu Ubuntu user. I configure Samba - goes well. I use Nautilus to share my Music folder from /home/steve/Music by R-click --> select the icon "Share Folder" and choose options "Windows SMB" and also make it writeable by unticking "Read only". That works I can see it from my vista and xp and Suse boxes and play over the network  the music files in the Music folder.

I can add music across the network from other machines into the Ubuntu collection with simple copy/paste in network browser AFTER I change permissions on the folder Music to drwrwxrwx - fine and good.

The problem comes with ownership of the files added to the music folder across the network from Suse and Ubuntu: When I add a music file from windows it takes up ownership user=steve and group=steve, which is just fine. BUT when I add a music file from Suse or Ubuntu it takes up ownership user=nobody and group=nobody. This is very difficult from an administrative perspective because the owner of the Music folder, steve, cannot alter the file in any way, except to delete it.

Can you show me how to get the files added from other Linux machines to the Ubuntu share to arrive with permissions (gid=steve, uid=steve) that are compatible with Ubuntu.

Thanks
Swerdna

---

### Post by swerdna on 2008-01-25
OK I found the answer. The non-standard permissions used in Ubuntu (where a user's primary group is not "users" but rather is named for the user's username) cause the permissions problem. It's fixed by adding this line into the definition for the share:
```
force user = steve
```
Then the group becomes by default "steve" also, which makes the files and folders under the share fully compatibile with the share's owner (steve) for administration purposes.

Swerdna

---

