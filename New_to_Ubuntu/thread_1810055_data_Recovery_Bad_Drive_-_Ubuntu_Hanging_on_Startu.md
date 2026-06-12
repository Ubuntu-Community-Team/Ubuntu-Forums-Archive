---
title: "data Recovery Bad Drive - Ubuntu Hanging on Startup"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by pygmalion7 on 2011-07-22
The original name for this thread was - "[B]data Recovery Bad Drive - Ubuntu Hanging on Startup"
[/B]With hindsight, my main question should have been how long is the recovery going to take - 
The full recovery took - 9 days. Ubuntu had not hung, it just took an hour to start up with the faulty hard drive.
please see the last thread for the outcome to this recovery.

First post here and praying for a miracle - **[ Rescue under way now - Progress Updates Added ]**
Trying to Use Ubuntu Rescue Mix v 11.04 boot cd to recover data from a bad 750Gb WD Caviar Green hard drive. The OS won't start up, just hung on splash screen. When I remove the bad hard drive it starts up ok. Is there any way to get it to ignore the bad drive on boot up so I can start to recover the data on it with ddrescue?

Makes this advice link seem optimistic when it won't boot when bad hard drive is attached. [ A mention that bootup could take hours would be handy. ]
[http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/](http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/)

Any advice on this would be much appreciated. 

Only 2 Hd's in system. Channel 0 - bad drive / Channel 1 - new 1Tb Drive.
I've swopped the drives over but makes no difference. I don't dare connect the drive after powering the system up in case this fries the MotherBoard.

My new 1TB hard drive is ready and waiting to receive the recovered data, but I'm stuck at the starting line. 
Thank you.

Updates are on posts below - Titled - _**Update**_.

---

### Post by sanguinoso on 2011-07-22
The only way I can think of to ignore the drive on boot would be to disable it in the bios, but then of course I don't believe it would be visible to the OS. Can you buy a Sata to usb adapter and then you can attempt to recover?

Also, remember from now on to back up your data.

---

### Post by amjjawad on 2011-07-22
> **pygmalion7 said:**
> First post here and praying for a miracle - 
Trying to Use Ubuntu Rescue Mix v 11.04 boot cd to recover data from a bad 750Gb WD Caviar Green hard drive. The OS won't start up, just hung on splash screen. When I remove the bad hard drive it starts up ok. Is there any way to get it to ignore the bad drive on boot up so I can start to recover the data on it with ddrescue?

Makes this advice link seem optimistic when it won't boot when bad hard drive is attached.

[http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/](http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/)

Any advice on this would be much appreciated. 

Only 2 Hd's in system. Channel 0 - bad drive / Channel 1 - new 1Tb Drive.
I've swopped the drives over but makes no difference. I don't dare connect the drive after powering the system up in case this fries the MotherBoard.

My new 1TB hard drive is ready and waiting to receive the recovered data, but I'm stuck at the starting line. 

Thank you.

Hello and welcome :)

If you're booting from the LiveCD, it shouldn't hung up UNLESS there is something wrong with the CD (bad burn/MD5SUM not the same) or BIOS settings.

As long as you are booting from the CD, it should boot from the bad HDD.

---

### Post by pygmalion7 on 2011-07-22
Finally got the shell prompt. Must have been over an hour. Unbelievable! The cd is fine because Ubuntu - Live boots ok when the bad drive is disconnected. No mention anywhere about this crazy delay! 

The failure to backup was financial not forgetfullness. Though could have bought a backup drive sooner with more discipline. 

Running Arconis Drive Monitor now, because this would have alerted me just before the drive failed.

Data recovery has started and seems to be peeling data off the knackered drive. It's 700Gb of movies and documentaries. 

Sure hope this works. Will keep thread open until the job's done.

---

### Post by sadaruwan12 on 2011-07-22
Same thing happened with a bad HDD I had but luckily I had a sata to usb converter so managed to get the OS working.

Hope god smiles on you and let you recover the files and please do tell us what happened as well before you mark it as solved.

---

### Post by pygmalion7 on 2011-07-24
_**UPDATE**_ ...

At nearly two days runtime so far, looks like there's a good portion of the 750Gb Hard drive rescued to the logfile. Think it's now rummaging over parts of the disk it found problems & nibbling out any further bytes it can salvage. 

How long should I let this run for, or does it terminate itself when it's good and ready?
Anyone know what the ipos and opos numbers mean?
~~~

Rescue started 
Fri 22nd July @ 14:00pm
Update time
Sun 24th July @ 09:31am

~~~
Console text reads ...

Initial Status read (from logfile)
rescued:              0B ,     errsize:         0B ,     current rate:   32768B/s 
rescued:    439582MB,     errsize:     391KB,     current rate:    8192B/s
rescued:    750129MB,     errsize:  27336KB,     current rate:         0B/s
rescued:    750129MB,     errsize:  27299KB,     current rate:    1365B/s
     ipos:     439586MB,     errors:           30,     average rate     5418KB/s
rescued:    750129MB,     errsize:  27215KB,     current rate:          0B/s
     ipos:     439591MB,     errors:           33,     average rate     5364KB/s
rescued:    750129MB,     errsize:  27157KB,     current rate:          0B/s
     ipos:     439591MB,     errors:           35,     average rate     5340KB/s
     opos:     439591MB,      time from last successful read 4.1m
Splitting failed blocks:

~~~
Thanks for any help / advice offered ...

---

### Post by pygmalion7 on 2011-12-26
Hard Drive Data Recovery Completed _**S****uccessfully**_ !!! 9 days later !!! YAY :)
My hard won media files from the past four years were back!

These are a few notes for the benefit of first timers which included me for this recovery:

~Ubuntu took so long to start up with the faulty hard drive, it seemed as if it was hanging.
Full startup took about 1 hour!

~Luckily (Which is probably why the recovery succeeded at all), once Ubuntu managed to start up fully, (Using the recovery comands as detailed here - [http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/](http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/)), the faulty hard drive was detected, and visible.

~The recovery process goes through several stages. The mechanics of this are detailed here ... [http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)
After three days about 90% of the 750Gb drive had been recovered, but after a further six days this tenacious software had whittled at every last recoverable byte on the faulty drive.

~The command that saved the day was - "sudo ddrescue -r 3 /dev/sdb image log"

~9 Days later, the recovery stats were - 978K unrecovered with 169 errors, 
That's less than 1Mb - Amazing!

~The failed drive was a "Western Digital 750Gb- 32MbCache- WD7500AADS- 00M2B0"
It was about ten months old, and had not been used intensively. The only sign of iminent failure was some odd behaviour when copying large video avi files, but it gave no real cause for alarm. The next morning, the pc wouldn't start, and this was a secondary hard drive, not even the boot drive. 

~The Raw log file data was copied to a 
"Western Digital 1.0TB- 64Mb Cache- WD10EARS"
(This did need to be larger than the failed drive.)

~The recovery (replacement) hard drive was a 
"Western Digital 750Gb- 64MbCache- WD7500AARS"

~Recovery from the log file drive to the replacement hard drive took about 10 hours.
The replacement hard drive and partitions were immediately recognized by windows XP, and the data was intact. There may be a few files missing, but they haven't been missed yet, and it's been over 4 months. 

~With a bit of arm twisting, Western Digital agreed to upgrade the replacement to a 1.0Tb Hard drive. I had argued, the recovery hard drive was a higher spec, and I had incurred extra costs in purchasing a larger capacity recovery drive so they matched the larger recovery drive's spec.

~Before returning the failed hard drive to Western Digital, I ran the drive wipe utility using the *secure erase - built in hardware utility. This bricked the hard drive, but I don't trust it wiped the drive properly because of how quickly it seemed to complete.

~I now use "Arconis Drive Monitor". It probably would not have saved the data, but at least if the next failure is more gradual, I should have a bit more time.

---

