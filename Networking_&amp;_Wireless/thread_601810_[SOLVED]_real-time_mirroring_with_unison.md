---
title: "[SOLVED] real-time mirroring with unison?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by a_posse_ad_esse on 2007-11-03
I realize that this is a slightly redundant thread, but I have not been able to find a definitive "how-to" on the data mirroring question.

My setup: (all run Ubuntu in some form)
a central server, in this case handling the mirroring.
a workstation that stays on the home network
2 laptops that are used for school

My plan is to have the users home folders on the workstation to be mirrored by the server, which then mirrors to the laptops (and vice-versa, as unison does a two-way sync).  This would keep projects, important files, etc. uniform throughout the system, and would have three potential points of failure as opposed to one.

My thinking is to have the server running fileschanged, which reports when a specific directory has been altered, which would then trigger a unison event which would initiate the mirroring throughout the system.  The [sourceforge page]("http://fileschanged.sourceforge.net/") for fileschanged has instructions to have a command run, but I am not a programmer, so I am unsure how to keep the script running if changes are found after the command is run.

Another, less elegant solution would be to have a cron job that ran every 5 minutes to run the mirroring.  Given the tasks at hand, it seems that this would cost a lot of unnecessary processing, and would detract from other functions, such as transcoding recordings from mythtv, etc.

Any suggestions about how this could be done?  They would be most appreciated.

---

### Post by kevdog on 2007-11-03
Never seen the fileschanged program before, however it seems interesting, however I see a big limitation:

```
The file or directory that you want to monitor must exist at program start.
```

That isnt really good

---

### Post by a_posse_ad_esse on 2007-11-03
Ah, not being able to create new files would be a problem...

I guess that the next question would be whether or not the cron approach would be too taxing on the machine.  It isn't the most elegant solution, but my thinking is that it would be just for the short-term as work will undoubtedly increase toward producing an answer to SyncToy...

---

### Post by kevdog on 2007-11-03
Here is the problem with unison and cron

Sometimes unison hangs for no apparent reason, and other times - depending on how much info you want to sync it would take more than 5 mintues.  If you run a cron job, you would need to make sure that the unison process had stopped (from prior run), and if there is a unison process still running then dont do a unison sync.  This would require checking things either via a script or formal program.  I dont think unison is the best for such frequent backups.  For daily backups I think its great, however for minute to minute backups, this could be a problem.

---

### Post by a_posse_ad_esse on 2007-11-03
That's true.  The number of files and their size will be small, but the complexity of the process could cause some hangups.  It isn't something that could be done easily manually either.

I guess the question that comes now is, can what I proposed even be done given current open-source resources?  I have come across some non-free alternatives, but they are extremely expensive and far beyond the reach of a starving grad student.  lol

---

### Post by a_posse_ad_esse on 2008-01-16
I am working on a [solution]("http://ubuntuforums.org/showthread.php?t=655969") for these problems.  Any feedback would be appreciated.

---

