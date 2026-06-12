---
title: "Sbackup isn’t making scheduled backups"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2009-05-20
I have Sbackup set to hourly backups, but nothing new/incremental is appearing in the destination folder. Everything else seems to be working — every time I hit “backup now” I get the right files in the right directory (i.e., those that I've altered). In Webmin’s “Scheduled Cron Jobs” module, /etc/cron.hourly/sbackup is reported active. 

However, though I’ve let Sbackup sit open on the desktop for over an hour and closed for over an hour, in neither case did it create the next batch of files. In both cases, as soon as I reclicked “backup now” it sent the correct files to the backup location. 

How do I start diagnosing this problem? I’m awfully new to Linux, so am not sure where to start. 

Thanks, 

Rhythm

---

### Post by NimoTh on 2009-05-24
Hi, AFAIK the problem is a known one and it stems from sbackup not saving new configuration settings. For example, I always set my backup schedule to 10pm, but sbackup sets it back to 1pm. Also, I tell sbackup to quit if the device is not available (and this actually works) but everytime I open the configuration panel, the hook is gone again.

I am currently going manual - edit /etc/sbackup.conf. But I cannot find where the backup job is scheduled. Can you help me where to look for it, please? I'm not a Linux pro.

TIA
Martin

look here: [http://ubuntuforums.org/showthread.php?t=977344](http://ubuntuforums.org/showthread.php?t=977344)

---

### Post by callan79 on 2009-05-24
> **NimoTh said:**
> I am currently going manual - edit /etc/sbackup.conf. But I cannot find where the backup job is scheduled. Can you help me where to look for it, please? I'm not a Linux pro.



Hi Martin,

The scheduling is done by CRON. I'm not an expert on CRON but perhaps we can both learn something.

I have my system set to just do a backup daily, no specific times or anything. All I get is the following in /etc/cron.daily

```
lrwxrwxrwx 1 root root   26 2009-05-24 21:23 sbackup -> /usr/share/sbackup/sbackup
```

So it looks like my system just has a link to the actual sbackup program.

If you were to put more specific times etc into the settings, I think this would need a proper CRON entry.

You can LIST a user's cron jobs via:

```
sudo crontab -u username -l
```

You can EDIT a user's cron jobs via:

```
sudo crontab -u username -e
```

Can you please list your cron jobs, and also cron jobs for 'root' and post back here so we can find out how Sbackup works?

Thanks :)
Callan

---

### Post by NimoTh on 2009-05-25
Hi Callan,

I already checked the crontab but the strange thing is, I don't get any jobs listed on root, nor on my username. I do "sudo crontab -u username -l". (Actually, you don't need the "sudo" when you check the crontab for yourself.)

Sbackup is only in /etc/cron.d/ on my system. It executes sbackup, but there is no time specified. This is where I got stuck.

Cheers,
Martin

---

