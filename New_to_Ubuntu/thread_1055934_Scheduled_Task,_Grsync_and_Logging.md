---
title: "Scheduled Task, Grsync and Logging"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by kennyschiff on 2009-01-31
I've set up a Scheduled Task in 8.10 that should fire a Grsync operation daily @ 4 am. I have verified that the Grysync profile is able to fire manually from the Grsync GUI. I am also able to verify that the task fires correctly when executed from the "Run Task" from the "Scheduled Task" GUI.

I don't believe the scheduled task is running and want to trouble shoot why.

The task was created by the default user, who remains logged in when it's supposed to fire.

How and where can I log Grsync? and how and where can I log the "Scheduled Task" execution?

Any help is appreciated.

---

### Post by kennyschiff on 2009-02-03
As a Windows user I was using Grsync as a crutch for masking the seeming complexities of rsync. It seemed as I researched this that others have had issues with "Scheduled Tasks" (really CRONTAB) with running GUI driven program like Grsync. After a bunch of experimentation, I used "Scheduled Tasks" to run rsync alone with various "switches" properly set, the rsync events fired properly.

The benefit of Grsync is that it actually allows you to select the parameters for your sync process using the GUI, and writes the proper switches for you by default (assumes the the Grsync preference "Show rsync output by default" is set). Once I got the output tweaked to meet my needs, I just copied this to the "Scheduled Task" interface and was good to go. And of course, I could just have written this directly to a crontab file (as detailed here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)), but "Scheduled Task" GUI just made this easier.

---

