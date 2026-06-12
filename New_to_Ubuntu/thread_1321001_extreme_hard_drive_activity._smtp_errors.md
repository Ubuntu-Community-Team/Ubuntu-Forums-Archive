---
title: "extreme hard drive activity. smtp errors?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-11-09
Hi, I noticed over the past couple of days that my HDD is going crazy with activity, so I checked my logs.

My mail.log file is filling up very fast with the following:

Nov  9 17:30:05 bryan-desktop nullmailer[5327]: smtp: Failed: Connect failed
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Sending failed:  Host not found
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Starting delivery: protocol: smtp host: mail. file: 1257719401.17831
Nov  9 17:30:05 bryan-desktop nullmailer[5328]: smtp: Failed: Connect failed
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Sending failed:  Host not found
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Starting delivery: protocol: smtp host: mail. file: 1257736501.16029
Nov  9 17:30:05 bryan-desktop nullmailer[5329]: smtp: Failed: Connect failed
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Sending failed:  Host not found
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Starting delivery: protocol: smtp host: mail. file: 1257738001.19458
Nov  9 17:30:05 bryan-desktop nullmailer[5330]: smtp: Failed: Connect failed
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Sending failed:  Host not found
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Starting delivery: protocol: smtp host: mail. file: 1257713401.8471
Nov  9 17:30:05 bryan-desktop nullmailer[5331]: smtp: Failed: Connect failed
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Sending failed:  Host not found
Nov  9 17:30:05 bryan-desktop nullmailer[2624]: Delivery complete, 138 message(s) remain.

This happens thousands of times over.

Any idea what I should do? I would like to get this solved soon to calm my hard drive down a bit. Thanks

EDIT:
I sudo su'ed into /var/spool/nullmailer/queue
In there is the list of all of those files it is trying to send. Should I delete them? They are crontab message errors from when I was playing around with cron. Are they safe to simply delete?

---

### Post by jbrown96 on 2009-11-09
It should be safe. You could always just move them somewhere else, and see if the problem goes away. If something else breaks, simply move them back, and then we can try to come up with a better solution.

---

### Post by bnhrobotics on 2009-11-09
Ok, I deleted them and that fixed it. Yay! Was not sure how to delete them all via command line. So I chown'ed the directory to my user name so I could open the folder. Then deleted them all and chowned it back to the orignal state. Any tips for deleting a few hundred files with rm?

---

### Post by jbrown96 on 2009-11-09
If you are deleting everything in a folder, ```
rm /folder/*
``` The * is a wildcard, so you can match partial file names ```
rm /folder/*.mp3
``` will delete all files that end in .mp3 ```
rm /folder/11-9-*
``` would delete all files that start with 11-9-. 

You can go much further than this, but I can't explain all of it. Basically, if a human could be taught to delete files, then there's a unix command to do the same. The question is: will it take you longer to come up with the command, then to manually delete them? 

Changing the ownership is probably not the best way to go about it, but it's not that bad. It works, and you made sure to change it back. No harm, no foul.

---

