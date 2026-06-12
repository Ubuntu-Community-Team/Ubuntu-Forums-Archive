---
title: "[SOLVED] networking computer beginner question"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by AnLGP on 2008-07-07
I have two comupters.  A newer one and an older one.  The old one has a 200 gig HD that I'd like to use to send backup files from the new one to.  The newer computer is a 

**Gateway GT5018E**

[http://support.gateway.com/s/PC/R/GTModels/5454/5454sp2.shtml](http://support.gateway.com/s/PC/R/GTModels/5454/5454sp2.shtml)

and the old one is a

**Compaq Presario 5240**

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00190905&lc=en&cc=us&dlc=en&product=93149](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00190905&lc=en&cc=us&dlc=en&product=93149)

I took apart the old one (removing the HD) and tried to just connect it to the new one but it didn't work.  I'd like to either network them or figure out what I didn't do right to connect them.  If I can say anything else to help you let me know.  Thanks!

---

### Post by pytheas22 on 2008-07-07
If you want to use the old one only for backup, you can do it just with rsync and ssh.  You need to install an ssh server on the old computer:
```

sudo apt-get install ssh
```

Then, on the new computer, run an rsync command to backup your files over the network, e.g.:
```

rsync -e ssh /directory/to/backup [ more ... ] username-on-old-computer@IP.of.old.computer:/destination/for/backed/up/files
```

You can run the rysnc command as a cronjob to do the backup every minute, hour, day or whatever you like.  rsync is great for backups because it only copies over differences in files and directories--in other words, it doesn't recopy the whole mass of files each time--saving tons of bandwidth and time.

I hope my example rsync command is clear, but if you have questions, ask.  [This]("http://www.crucialp.com/resources/tutorials/server-administration/how-to-copy-files-across-a-network-internet-in-unix-linux-redhat-debian-freebsd-scp-tar-rsync-secure-network-copy.php") is also a nice guide for rsync.

---

### Post by AnLGP on 2008-07-07
Thanks for your reply.  I found out what I did wrong with the HDs.  The old one is PATA.  The new one is SATA and there's no way I can connect the PATA to my new mobo.  I'll have to network if I want to use the HD.  A quick glance at your commands (and having never used it before) seem to make sense but I suppose I'll cross that bridge when I get there :)

---

### Post by The incredible bulk on 2008-07-07
I have another idea...

what about something like this?

[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3855109&Sku=D15-2052&SRCCODE=PRICEGRABBER&CMP=OTC-PRICEGRABBER](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3855109&Sku=D15-2052&SRCCODE=PRICEGRABBER&CMP=OTC-PRICEGRABBER)

Just pop your HD in there and put it on your new comp via USB... and then get a Memory Card reader for your trouble...

Just a thought.

---

### Post by AnLGP on 2008-07-07
That's a fantastic idea.  Would that work with this?

[IMG]http://i297.photobucket.com/albums/mm213/musicauniversalis/0706081811.jpg[/IMG]

---

### Post by AnLGP on 2008-07-08
Solved.  View:

[http://ubuntuforums.org/showthread.php?t=852928](http://ubuntuforums.org/showthread.php?t=852928)
[http://ubuntuforums.org/showthread.php?t=852699](http://ubuntuforums.org/showthread.php?t=852699)

---

