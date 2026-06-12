---
title: "Completely, Completely Remove MythTV"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by slalomchip on 2010-01-30
I want to completely start over with a brand new MythTV installation.  (I'm running MythTV within Ubuntu, not running Mythbuntu) I have done a complete removal of everything starting with "MythTV" using Synaptic Package Manager.  During the removal, I get the statement that the configuration settings are being removed.  Then I reinstall MythTV and lo and behold - all of my previous settings are still present.

How can I completely, completely remove MythTV, including the database and configuration settings?

---

### Post by baddog144 on 2010-01-30
```

sudo apt-get purge mythtv

```

---

### Post by Jive Turkey on 2010-01-30
I've never used MythTV so bear with me on this.
I would search for the configuration files in /etc/ and the subfolders especially if there is a mythtv directory there.  Also there may be some config files in your home directory look for files and folders possibly named ".mythtv" the "." makes the file/folder hidden so you may need to adjust your nautilus window to show hidden files.  If mythtv uses an actual database like postgresql, or mysql, you will need to log into those services and run a command like "drop database nameofdatabase;"  Search the docs for whatever database system mythtv uses and go from there.

---

### Post by slalomchip on 2010-01-31
Thanks.  I tried the pruge command first, but got the same result.  Also tried the autoremove command, same result.

Success was finally had when I manually deleted the MythTV MySQL database.  First, I did a complete removal of MythTV (including configurations, even though it doesn't clear out the MySQL database) using Synaptic Package Manager.  Then I used line commands to do the rest.  I switched to root access (sudo su) and removed all contents in the /var/lib/mysql/mythconverg/ folder and also removed all the mythconverg backups in /usr/share/mythtv folder.  

After rebooting, I tried to reinstall MythTV, but it failed midway through installation.  I thought I created a big problem deleting the database, but I rebooted and tried reinstalling MythTV again and it installed fine the second time.  Sure enough, I was back to a completely clean installation of MythTV and started all configurations from scratch.

PROBLEM SOLVED!!!

---

### Post by goldshirt9 on 2010-01-31
please tell all 
myth failed for me so any advice is appreciated

---

### Post by slalomchip on 2010-01-31
Just follow the procedures I laid out above.  If there is anything you don't understand, please be specific in your question.

---

### Post by Fire$torm on 2010-01-31
@slalomchip,
Thanks for the update. Good stuff to know.

Peace.

---

