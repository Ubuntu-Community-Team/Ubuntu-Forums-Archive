---
title: "Howto disconnect SMB share"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by hornetster on 2008-04-13
Hi All, just wondering if anyone can share the secret of how to disconnect an SMB share, and/or reconnect as a different user, without logging out/rebooting?
Thanks, John.

---

### Post by alenis on 2008-04-13
type in the terminal

sudo umount <mount path>, e.g. sudo umount /media/movies

If you connect to the share through nautilus, right-click on the icon and select "umount volume" or something like that (I have the italian verison and I don't know the exact equivalent of "smonta volume" in english: it should be the second last entry in the menu)

---

### Post by hornetster on 2008-04-13
Hi Alenis, thanks for the reply. What I am wanting to do is disconnect/reconnect a drive which has been connected via Nautilus/Konqueror and doesn't actually have a mount point.
ie going to Network in Nautilus and connecting to a Windows share. I don't believe this mounts it "legally"?? Which reminds me of another question..... if you do connect a share this way, is there then any way to use this in a terminal.....?

Thanks.

---

### Post by alenis on 2008-04-13
Unfortunately, it seems that Nautilus doesn't mount samba shares in the filesystem. See this thread:
[http://ubuntuforums.org/showthread.php?p=1748025#p%20ost1748025]("http://ubuntuforums.org/showthread.php?p=1748025#p%20ost1748025")

So I don't think you can access them through the terminal.

---

