---
title: "Cronjob malfunctions."
date: 2009-04-30
forum: New to Ubuntu
---

### Post by drumnmachn19 on 2009-04-30
So my suite mate wrote a really awesome bash script that he gave to me, and I'm working on a back up script.  He runs 8.04lts and I run 9.04.  He doesn't have any issues with his script by I can't seem to get it to run on my setup.  The script detects inactivity at the keyboard and mouse then submits to the website Twitter whether to turn mobile device updates on or off.  The script is placed in /usr/local/bin/  Then I create a cronjob for it by:
sudo crontab -e
* * * * * /usr/local/bin/twitteridler

I was wondering if anyone has any advice on how to get the script to run?  Like I said my friend has no issues in 8.04 using the same exact setup.  Thank you very much for all of your assistance.

---

### Post by jazzgossen on 2009-05-01
Does it work if you run "sudo /usr/local/bin/twitteridler" from the command line?

---

### Post by wizard10000 on 2009-05-01
> **drumnmachn19 said:**
> So my suite mate wrote a really awesome bash script that he gave to me, and I'm working on a back up script.  He runs 8.04lts and I run 9.04.  He doesn't have any issues with his script by I can't seem to get it to run on my setup.  The script detects inactivity at the keyboard and mouse then submits to the website Twitter whether to turn mobile device updates on or off.  The script is placed in /usr/local/bin/  Then I create a cronjob for it by:
sudo crontab -e
* * * * * /usr/local/bin/twitteridler

I was wondering if anyone has any advice on how to get the script to run?  Like I said my friend has no issues in 8.04 using the same exact setup.  Thank you very much for all of your assistance.

I've had some cron issues with Jaunty as well - I reinstalled cron with synaptic and the problem went away.  Can't explain it other than to say jobs in /etc/crontab weren't running and when I reinstalled cron they started working.

---

### Post by drumnmachn19 on 2009-05-01
I uninstalled it using Synaptic, but I am still having the same problem.  Do I need to remove any hidden files in /etc/?

---

