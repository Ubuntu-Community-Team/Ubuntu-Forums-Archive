---
title: "Ubuntu and xp"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by ned3110 on 2008-05-08
Hi all

I have asked this question before but I still haven't managed to resolve the issue. I've been really busy but now feel ready to tackle it again.

I am trying to get my Ubuntu box to network with my three other xp machines. but it just wont work can someone please help me. Someone has told me what to do, and I cut and pasted stuff and installed Samba etc but no joy. 

If I go to places and then network I can see an icon that says windows network but when I click on it, there is nothing there!

I really want this to work because my Ubuntu box is gonna serve as a back up, and maybe print server.

---

### Post by njparton on 2008-05-09
If you need to mount windows partitions or folders in ubuntu you do that via cifs (make sure you have smbfs as well as samba installed).
 
Search this forum for cifs network mounting guides and how to edit your fstab file.
 
You use samba for sharing ubuntu folders (and printers) to windows. This is controlled by the /etc/samba/smb.conf file. Right click on a folder in nautilus and select share and it will add an entry to the bottom of that file which you can replicate with other entries as necessary. Then restart samba:
 
```
 
sudo /etc/init.d/samba restart

```
 
Have a read of the samba section of the online ubuntu desktop guide :wink:

---

### Post by Iowan on 2008-05-09
Try the Places>"Connect to Server"option - that sometimes works better for me than Places>Network.

---

### Post by shazzy on 2008-05-16
My situation is slightly different but hopefully appropriate for this thread:

I'm using an Ubuntu workstation with a WindowsXP file/print server (I haven't gotten around to converting my server to Ubuntu *yet*).

I have the printer drivers installed and Ubuntu sees the printer on the Windows machine.  When I try to print, I select the printer from the print menu and then nothing happens.  The print job stays in the print queue with status "processing".

I tried typing sudo /etc/init.d/samba restart and I get:
sudo: /etc/init.d/samba: command not found

Any guesses?

---

### Post by Gunman1982 on 2008-05-16
> **shazzy said:**
> 
I tried typing sudo /etc/init.d/samba restart and I get:
sudo: /etc/init.d/samba: command not found

Any guesses?
Install the samba package

---

### Post by shazzy on 2008-06-19
Doh!  I had "samba-common" but not "samba" package installed.  I assumed that since the file sharing was working that samba was installed.  Thanks for illuminating the obvious for me. :roll:

---

### Post by timcredible on 2008-06-19
in 8.04, all you have to do to share a folder with windows machine is to right-click on the folder, choose 'sharing options', and click share.  if it's the first time you've done it on that machine, it'll download some packages, then do a reboot, and go back to the 'sharing options', and click share.

to see windows machines, go to Places->Network.  i'm not sure if this works be default, or if the machine needs to install the above mentioned software first.

---

