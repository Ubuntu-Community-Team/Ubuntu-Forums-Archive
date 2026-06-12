---
title: "Setting CLAMAV to scan root daily"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by CharlesA on 2009-10-11
I was trying to set up clamav to scan the root of my drive every day at midnight.

I can set it up in cron as root so that it can scan everything. That's fine. I was wondering how the updates would work. I checked the options for freshclam, and it says that it can run as a daemon.

I'm wondering how I could get that to start automatically. Should I just setup a cronjob that launches freshclam to update the virus db, or is there another way?

Also, I was going to use clamscan -riv / in cron so that it'll scan everything without problems. Is there a better way to do that as well?

I saw that there is also a clamav daemon, but I'm not quite sure how to set it up, I've got it installed and everything.

Thanks!

---

### Post by Boondoklife on 2009-10-11
For easiest setup just use the crons to do what you are looking for works out great for my download appliance that is linux based. I have a cron to run the update and then have a script that scans now downloads when they are done.

---

### Post by CharlesA on 2009-10-11
> **Boondoklife said:**
> For easiest setup just use the crons to do what you are looking for works out great for my download appliance that is linux based. I have a cron to run the update and then have a script that scans now downloads when they are done.

Thanks! I think freshclam is running in daemon mode, and I'll just use cron to schedule a clamscan.

---

