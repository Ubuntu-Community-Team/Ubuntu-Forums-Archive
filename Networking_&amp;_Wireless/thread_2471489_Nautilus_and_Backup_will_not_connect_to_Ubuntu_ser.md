---
title: "Nautilus and Backup will not connect to Ubuntu server"
date: 2022-01-31
forum: Networking &amp; Wireless
---

### Post by foxsquirrel on 2022-01-31
Client is a Pi 4 on 21.10. Server is a big box Dell running Server 21.10 in a LAMP configuration. 

ssh via console and sftp using filezilla connect fine.

Nautilus and Backup will not connect.

Several other Pi 4 running 21.10 on the same server are able to connect using Nautilus and Backup works to back up files.

---

### Post by TheFu on 2022-01-31
does ping work between all systems?

---

### Post by foxsquirrel on 2022-01-31
Yes, all can be pinged.

Just got it to work, however, I had to log into the 2.4ghz connection instead of the 5ghz that all the other stuff is on. This is odd, ssh and filezilla work when on the 5ghz but not Nautilus. and Backup. Still seems like their is a problem with it, should not matter if the clients are on 5 or 2.4ghz.

---

### Post by TheFu on 2022-01-31
I don't know what "Backup" is. Sorry. I use rdiff-backup for my backup needs.  I haven't used Nautilus in years. I'm not really a GUI user. Mainly servers and terminal/CLI work for me.

---

### Post by foxsquirrel on 2022-01-31
"Backups" is packaged with Ubuntu desktop.

---

### Post by Tadaen_Sylvermane on 2022-02-01
Backups is simplified name for Deja-Dup I believe.

I've had the occasional odd thing with 5g vs 2.4 myself. I never bothered looking into it. I just use 2.4 out of habit because of the sheer randomness of the 5g. I always assumed it was my router. Maybe something deeper?

---

### Post by foxsquirrel on 2022-02-01
Most certainly odd, I opened up the gateway and did not see anything suspicious. 

Just noticed that the "Backups" is not displaying "restore" files. Is it getting lost trying to connect to the backup location?? All the compressed files are at the location specified and can be seen with Nautilus.

All of the pi4 are in the lab and its controlled distance so its not loss of signal. Not sure what to think about this, either if its a router or what ever.

MAC address issue??

---

### Post by TheFu on 2022-02-01
I tested Deja Dup years ago and decided it was the wrong sort of backup tool for my needs. It was terribly slow at the time too.  Did a 100GB backup test using 5 different backup solutions. All the GUI tools based on Duplicity (duplicity is the CLI version, but DejaDup and Duplicati are the GUI tools) were taking over 8 hours.  rsync + hardlinks, Back-in-Time tool about 45 minutes for the first run.  rdiff-backup also took 45 minutes for the first run, but on the 2nd through 50th runs, rdiff-backup was hugely quicker than all the others, usually under 2 minutes.

I don't use wifi unless absolutely necessary. Long ago, I did a corporate wifi design and deployment to over 1200 locations.  That taught me a bunch about wifi.  Always use wired ethernet when possible, then Power-Line networking, then MoCA networking, and lastly, if there isn't any other choice, wifi.  Oh, and never, ever, trust the security of any wifi or BT connections. The public just doesn't know how bad that security is and nobody in the business wants to tell them.  It is basically SS7 all over again - SS7 security issues have been known for 30+ yrs, yet no govts have mandated that it not be used.

---

### Post by foxsquirrel on 2022-02-01
> **TheFu said:**
> I  Always use wired ethernet when possible, 

Yes, most certainly. Our internal critical network is secure and air-gapped from the internet, its all wire. One of these days I will get it all on fiber and it will be much faster. The non-critical stuff and web browsing is on its own network with wire and wifi. 

I do like the "Backups" on the desktop, not sure how to go about debugging this issue. Some of this stuff is getting so complex its nearly impossible to trouble shoot unless it is something you do every day. Its not what we do, so I was hoping some others might have been down this path and have a solution.

---

### Post by deadflowr on 2022-02-01
Out of curiosity check and see if the gvfs-backends package is installed.
```
dpkg -l gvfs-backends
```

---

### Post by foxsquirrel on 2022-02-02
results:

> Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version          Architecture Description
+++-==============-================-============-=======================================
ii  gvfs-backends  1.47.91-1ubuntu1 arm64        userspace virtual filesystem - backends


---

