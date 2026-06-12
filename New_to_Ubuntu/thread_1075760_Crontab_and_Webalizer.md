---
title: "Crontab and Webalizer?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by thomsonm on 2009-02-20
I'm running Ubuntu Server 8.10 (logged in as root) and I've got Squid installed and configured to work with Webalizer just fine. I can manually run webalizer and add the new data to my charts. My problem is trying to get get Webalizer to run every hour using crontab so that it updates automatically. It seems no matter what I try it just won't run.

At Terminal I type:
crontab -e
Then I've tried all the different lines below:
0 * * * * /usr/bin/webalizer
0 * * * * /usr/bin/webalizer -p
0 * * * * /usr/bin/webalizer -c /etc/webalizer/webalizer.conf
(the last line was reported to work in the Ubuntu forums but it doesn't for me)
And I've tried many combinations of minutes and hours. I even read that you need a carriage return at the end of the last line of code (sounded sketchy but I've tried everything so why not), this didn't solve the issue either.

In crontab after my webalizer line I also have the line:
59 23 * * * /etc/squid/rotate.sh
This works perfectly fine. It rotates my logs to another directory and renames them (based on the date), creating a new blank log for the next day.

Any help/suggestions would be greatly appreciated.

---

### Post by Hospadar on 2009-02-20
Who's crontab are you running it it?  your crontab or root's?
Which user needs to run it?
If you run some program in cron that produces known output, does that work? (like /usr/bin/touch /wherever/somefile/temp)

Cron will email errors to whichever user owns the crontab the jobs ran on.  try ```
sudo apt-get install mailutils
mail
```

---

### Post by thomsonm on 2009-02-20
I'm running it as root and only root needs to run it. I'm using Webalizer to monitor network traffic accessing the internet. I do not have any mail accounts setup on the machine. I guess I can try setting up an account (on  Monday) to see what errors it throws at me. Any other thoughts or suggestions?

---

### Post by dcstar on 2009-02-20
> **thomsonm said:**
> I'm running Ubuntu Server 8.10 (logged in as root) and I've got Squid installed and configured to work with Webalizer just fine. I can manually run webalizer and add the new data to my charts. My problem is trying to get get Webalizer to run every hour using crontab so that it updates automatically. It seems no matter what I try it just won't run.

At Terminal I type:
crontab -e
Then I've tried all the different lines below:
0 * * * * /usr/bin/webalizer
0 * * * * /usr/bin/webalizer -p
0 * * * * /usr/bin/webalizer -c [B]/etc/webalizer/webalizer.conf
(the last line was reported to work in the Ubuntu forums but it doesn't for me)[/B]
And I've tried many combinations of minutes and hours. I even read that you need a carriage return at the end of the last line of code (sounded sketchy but I've tried everything so why not), this didn't solve the issue either.

In crontab after my webalizer line I also have the line:
59 23 * * * /etc/squid/rotate.sh
This works perfectly fine. It rotates my logs to another directory and renames them (based on the date), creating a new blank log for the next day.

Any help/suggestions would be greatly appreciated.

Are you **sure **that is correct?

---

### Post by thomsonm on 2009-02-23
My crontab looked as such on Friday and over the weekend:
**25 15 * * * /usr/bin/webalizer -c /etc/webalizer/webalizer.conf**

Now this did not run by itself when I had changed the times to test it on Friday (at least it appeared that way), but this morning I checked my webalizer charts and they had all the updated data from over the weekend. I changed my times to 45 and 23 so it runs at the end of the day. I'm going to let it run the rest of the week to make sure. It must have been an error on my part when testing on Friday. Thanks for the replies. Issue solved.

---

