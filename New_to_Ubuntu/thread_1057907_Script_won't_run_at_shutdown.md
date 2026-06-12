---
title: "Script won't run at shutdown"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Twizzle on 2009-02-02
I have written a simple script that will use rsync to back up my documents folder to my server. I know it runs and does the job when run from the command prompt.

I then placed a symbolic link into /etc/rc0.d using:

sudo ln -s /home/john/daily_backup.sh /etc/rc0.d/

However, when I shut the system down it is not syncing the folders. It has been set so that I have read and write access to the script if that is any reason?

How can I see the errors (if any) or can someone suggest what I should try.

(I would also like to set a script that runs weekly and monthly - any pointers there too would be great :D )

Thanks

---

### Post by lykwydchykyn on 2009-02-02
I've never tried to run anything from rc0.d, I wouldn't be sure what services and environment you'd have at that point.

It might be better to do this from within your desktop environment.  I know KDE has a place to put logout scripts, I'm sure GNOME probably does too.

To set it up weekly or monthly, you can use cron.  From the CLI you want to type: crontab -e
But I know both GNOME and KDE have graphical config tools for cron.

---

### Post by Twizzle on 2009-02-02
Thanks for the quick reply. I was aware of cron being an option but I had a few uncertainties.

It is important to me to have the rsync on every shutdown so I minimise the risk of loosing any files. Also as, over time, the files will become bigger / more and I do not want it happening while I am trying to use the computer and affect the performance.

I was also unsure about what happens if you miss a time slot. Ie it was due to run on a monday but you don't turn the computer on 'till tuesday. Will it run as soon as you turn on or wait until next tuesday?

---

### Post by mdpalow on 2009-02-03
QuickStart could help you with this. See signature in my link below.

---

### Post by schilcha on 2009-02-08
> **Twizzle said:**
> 
sudo ln -s /home/john/daily_backup.sh /etc/rc0.d/


The link's name in rc0.d needs to start with Sxx or Kxx (xx is a 2-digit number indicating the order of scripts). E.g.:
```

sudo ln -s /home/john/daily_backup.sh /etc/rc0.d/S10daily_backup.sh

```
This means that all scripts with lower numbers (S00 to S09) will be executed before and all scripts with higher numbers (S11 to S99) will be executed after your script. Make sure that all services that you need (e.g. network) are still up, when your script is executed. There is no need to have unique numbers (five scripts with S10 is perfectly fine). 

Usually the original copy of these scripts are located in /etc/init.d. I don't know, if this necessary to have the script executed at shutdown. 

Good luck,
   schilcha

---

