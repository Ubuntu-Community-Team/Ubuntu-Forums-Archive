---
title: "Ubuntu 8.04 cannot see Windows XP shares"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by roadrawts on 2008-12-02
Was using Ubuntu 7.10 and was able to see windows shares on an XP machine.  Also was able to share printer.  Recently upgraded to 8.04.  Now cannot see any shares or printer on the XP machine.

Tried:
sudo smbclient -L name_of_windows_box -U useraccount_windows.  

It listed all shares on it so I think the Windows box networking and firewall is set up properly.  But from Places->Network I can see the box but not the shares or printer.  I can see the Ubuntu shares from the Windows box.  

I have restarted samba and even rebooted the box.  No difference.

Need help?

Thanks.

---

### Post by superprash2003 on 2008-12-02
try this way [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by roadrawts on 2008-12-02
> **superprash2003 said:**
> try this way [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)
Thanks. I'll try this tonight when I get home.  I'll reply later with results.

---

### Post by roadrawts on 2008-12-02
Tried the process in the article but to no avail.  Still does not show the shares or printer.  When I use Places->Network the Windows Network icon displays.  Clicking it shows an icon for the workgroup on the windows box.  Clicking that icon displays the computer alias icon.  Clicking on that icon shows 0 items.  Actually, this scenario is the same as the one in the article.  So, I still cannot see any shares on the windows box.

---

### Post by roadrawts on 2008-12-03
Later I tried Connect to Server instead of Places->Network.  Once the server was mounted as E$@192.168.1.101 I was able to see the shares.  I don't understand what the difference could be????

---

### Post by joker535 on 2008-12-04
Did you find a solution for this. My 8.04LTS lost its ability to see/access windows shares yesterday so I re-loaded it with a complete fresh install of 8.04LTS. It didn't fix it. Can't figure out what changed. I may reload again later and not run the updates.

Thanks

Bob

---

### Post by roadrawts on 2008-12-04
I cannot see the shares using Places->Network-><workgroup>-><server name> but I can use Places->Connect to Server and put in smb://<servername>/<drive>$ and that mounts the drive with all shares visible and useable.  I found the names to use by going to a terminal and: sudo smbclinet -L <servername> -U <user> and it lists all of the shares.  

I just can't, for the life of me, figure out why if I can mount the drive and do the smbclient stuff why I can't get to it from Places->network?????

Good luck.

---

