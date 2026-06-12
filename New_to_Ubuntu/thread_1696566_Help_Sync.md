---
title: "Help Sync"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Tabu.it on 2011-02-27
Hi,
I need a program to automatic backup some folders from different computers (all running windows7) to my Ubuntu home server (10.04 version). Thank you

---

### Post by quixote on 2011-02-28
I don't know if "simplebackup" would do what you need.  Open synaptic (System > Admin > Synaptic) and put that name in the search bar.  You can install it from there.  What I don't know is whether it handles windows files.  I think so, but I'm not sure.

---

### Post by Tabu.it on 2011-02-28
> **quixote said:**
> I don't know if "simplebackup" would do what you need.  Open synaptic (System > Admin > Synaptic) and put that name in the search bar.  You can install it from there.  What I don't know is whether it handles windows files.  I think so, but I'm not sure.


Thank you

I'm reading this [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite) and i find that it could only backup from localhost to Ftp or other pc. I need the opposite thing (windows to ubuntu) running on Ubuntu.

---

### Post by arsenic23 on 2011-02-28
Mount the shares onto your ubuntu system and use rsync.

---

### Post by Tabu.it on 2011-02-28
I found this guide: [https://help.ubuntu.com/community/BackupPC](https://help.ubuntu.com/community/BackupPC)

i'm not an expert user but i think it could backup from windows to ubuntu without installing software on windows pc. Tomorrow i'll try it. :)

---

### Post by KIAaze on 2011-03-01
You could maybe also use online services like dropbox or spideroak (I'm pretty sure daemons for servers are available).

But yes, I think rsync is the most common tool for such tasks.

---

### Post by Tabu.it on 2011-03-01
ok i'm following your advice and start with rsync.

i'm reading this guide [http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/](http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/) .

I'll post here if i found some problems :)

Edit

> 
Create a file named rsyncd.secrets in /etc
sudo nano /etc/rsyncd.secrets
Add the following to rsyncd.secrets, replacing username with your username and password with a password of your choosing:
username:password
sudo chmod 600 /etc/rsyncd.secrets


is the password the ubuntu login password for that username?

---

### Post by quixote on 2011-03-02
BackupPC looks like an excellent choice.  That's new since the last time I was fighting with setting up a backup system.  I may use it myself.

Did you have trouble mounting the Windows shares on the computer controlling the backup?  If not, then I'm not sure you need justinsomnia's rsync server setup.  Rsync scripts work fine without that. As for which password he means, it is rather vague.  He says "of your own choosing" so presumably it's a password just for the rsync daemon.  ??  Not at all sure.

---

### Post by Tabu.it on 2011-03-10
> **quixote said:**
> BackupPC looks like an excellent choice.  That's new since the last time I was fighting with setting up a backup system.  I may use it myself.

Did you have trouble mounting the Windows shares on the computer controlling the backup?  If not, then I'm not sure you need justinsomnia's rsync server setup.  Rsync scripts work fine without that. As for which password he means, it is rather vague.  He says "of your own choosing" so presumably it's a password just for the rsync daemon.  ??  Not at all sure.

I'm testing Backuppc now but i recive this error when i run (with html) the backup: NT_STATUS_BAD_NETWORK_NAME. What does it mean?

---

### Post by KIAaze on 2011-03-10
More backup tools:
[http://ubuntuforums.org/showpost.php?p=10540314&postcount=2052](http://ubuntuforums.org/showpost.php?p=10540314&postcount=2052)
[https://launchpad.net/timevault](https://launchpad.net/timevault)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)
[http://lifehacker.com/?_escaped_fragment_=398775/sync-and-back-up-your-data-with-conduit-for-linux#!398775/sync-and-back-up-your-data-with-conduit-for-linux](http://lifehacker.com/?_escaped_fragment_=398775/sync-and-back-up-your-data-with-conduit-for-linux#!398775/sync-and-back-up-your-data-with-conduit-for-linux)
[http://live.gnome.org/Conduit](http://live.gnome.org/Conduit)

---

### Post by Tabu.it on 2011-03-10
I need help for Backuppc config. In particular about this error 

> 
2011-03-10 23:50:00 full backup started for share \\ANNALISA-PC\Users\Annalisa\Documents
2011-03-10 23:50:02 Got fatal error during xfer (tree connect failed: NT_STATUS_BAD_NETWORK_NAME)
2011-03-10 23:50:07 Backup aborted (tree connect failed: NT_STATUS_BAD_NETWORK_NAME)


I made a shared folder on windows7 and i could enter it with smbclient but backuppc still refuse to work.

---

### Post by Tabu.it on 2011-03-12
*bump*

I could navigate the windows share file from gnome, but i still recive that error with backuppc.I thought that was windows firewall but without it i still recive the same error. Any idea?

---

