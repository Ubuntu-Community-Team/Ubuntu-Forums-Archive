---
title: "file server"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by sNNooPY on 2008-03-29
Hello!

I made a file server at home based on WinXP:

AMD Sempron 64 3200+
ASUS M2N-MX(nForce 430/GeForce 6100)
Patriot 1GB (PSD21G6672) DDR2@667MHz
Samsung SpinPoint T166 500GB SATA-II (HD501LJ)
Seagate 7200.7 160GB (ST3160023AS)
Pioneer DVR-212
Fortron FSP-60THNP 350W

It's used a file server/media server (streaming to HTPC)/downloader/torrentbox

I'm thinking of installing Ubuntu instead of WinXP because of stabilty and security.

So...
1. how do I setup file share? I'm assuming Samba protocol or what since all other machines are on windows?
2. I need a way to remote control it from other computers (I use UltraVNC with Windows) since I would be removing the keyboard/monitor, etc. and leave it connected to network only.

---

### Post by insineratehymn on 2008-03-29
Sounds like you've got a good idea.

Samba will allow your files to be viewed on your windows machines.

UltraVNC should work, or you could download the standalone Vncviewer (thats the only one I can confirm works well). Just install the vnc software on the ubuntu box and you should be GTG.

---

### Post by Belnoctourne on 2008-03-29
setting up samba is very simple, just apt-get install samba it'll have a few dependencies go ahead and say yes to install them I can't access my server at the moment due to work firewalls to tell you the locations of the config files but theres plenty of guides out there for configuring samba, if you dont feel like getting in the guts of it I would go ahead and just install webmin (apt-get install webmin) makes server administration very very simple and takes out the need to memorize stuff (good to do just a lot at first) you can either manage your samba shares to that and grant rights very easily or you can edit the samba.conf (I beleive thats the config file) and add your shares manually. Ubuntu ships with vnc by default you just need to go (from memory I beleive it's) administration>desktop sharing and enable remote connections make sure you set a password and disable the pop up allow box in the options and you'll be in good shape

---

### Post by superprash2003 on 2008-03-29
check this out [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by nickoli_02 on 2008-03-29
I recently set up a minimal system doing exactly what you want it to do (file server + torrents). Samba sharing is the clearcut choice for sharing with Windows machines, but if you just need to access the file server from unix-based machines you also have the option of setting up an NFS share instead. 

The easiest way to connect to the box remotely is through SSH. Simply install open-ssh on the server and you're all set. SSH combined with screen and rtorrent will give you a command line system with a very slim and powerful bittorrent client. You can configure rtorrent to monitor your download directories for new torrent files, and start downloading them automatically. For me, rtorrent was the key discovery in building my file server.

Anyway, to summarize:
1. Samba for sharing
2. SSH for remote connections
3. rtorrent (with screen for resumable sessions) for P2P 

Those three tools will get you a minimal server without a GUI doing exactly what you need it to do. Its working perfectly for me :)

---

### Post by Iowan on 2008-03-30
[This]("http://ubuntuforums.org/showthread.php?t=202605") might be helpful.  Also, check the Samba file server setups at [howtoforge.com]("http://www.howtoforge.com/howtos/samba").

---

### Post by sNNooPY on 2008-04-04
ok, it's me again. :)

Currently all my partitions are NTFS, when I migrate to Ubuntu I wish to make the two Ubuntu partition (main and swap) to be ext3, but leave NTFS on the other partitions...
will that have an impact on performance, etc.?

---

### Post by superprash2003 on 2008-04-04
well normally ntfs and ubuntu dont go well together.. better use ext3

---

### Post by sNNooPY on 2008-04-04
> **superprash2003 said:**
> well normally ntfs and ubuntu dont go well together.. better use ext3
can I convert NTFS to ext3 without losing or corrupting my files?

---

### Post by nickoli_02 on 2008-04-05
No, there is no "conversion" between NTFS and ext3. You'll have to reformat, which will wipe your partition clean of all data. If you can, move your documents and important files to another location.

---

### Post by sNNooPY on 2008-04-06
> **nickoli_02 said:**
> No, there is no "conversion" between NTFS and ext3. You'll have to reformat, which will wipe your partition clean of all data. If you can, move your documents and important files to another location.
unfortunately that's not possible.
I have abandonded this project since I have 500+160GB of data on NTFS partitions and I don't have "spare space" to move them, and recording them on DVDs makes no sense...
Guess I'm stuck to Windows for a while...
thanks anyway,
bye

---

