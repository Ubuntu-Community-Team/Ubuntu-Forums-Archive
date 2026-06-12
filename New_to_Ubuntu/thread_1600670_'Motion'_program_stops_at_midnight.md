---
title: "'Motion' program stops at midnight"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by canam101 on 2010-10-19
I am running 'motion', and making an avi file which is added to whenever motion is detected; a regular webcam picture which refreshes every 5 seconds, and a stop-motion mpg file which takes a picture every 60 seconds. An impressive piece of software.

The one problem I have is that it shuts down at midnight. I have played with every setting in the motion.conf file that seemed relevant, but the thing still shuts down at midnight.

I get around it by having a scheduler job start the program at 12:05am, but it would be a lot better if it would just keep running.

Does anyone know of a solution to this?

Thanks.

---

### Post by SuaSwe on 2010-10-19
Have you checked if there are any applications that start running at 00:00, like a cron job ([https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)) for example? Maybe something's kicked into gear at midnight that disrupts motion as it's running? Could also be worth looking through the system logs ([https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)) to see if you spot anything suspect. :)

---

### Post by no2498 on 2010-10-19
? what time does your sys look for updates

---

### Post by canam101 on 2010-10-20
Thank you for the replies. There is nothing scheduled for 00:00, and I did not see anything in the logs that looked likely.

An update took place this morning around 8, so I guess that isn't involved.

The only suggestive thing I found is a variable called ffmpeg_timelapse_mode. This supposedly tells it when to start a new output file for the time lapse video. The default is 'daily', ie, midnight, but that shouldn't shut the whole program down unless there is a bug.

I changed it to monthly and will see what happens. In the meantime, re-starting at 00:05 seems to keep things in motion.

---

