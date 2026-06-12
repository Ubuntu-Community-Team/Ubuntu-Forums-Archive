---
title: "request for help with &quot;Scheduled Tasks&quot; program"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-07-04
Hi Ubuntu Community:

I'm having trouble using "Scheduled Tasks" in gnome to run a script recurrently, ie automatically at specified times on specified days of the week.

The script is /scripts/JazzClassics and:
[LIST=1]
[*]uses mplayer to record streaming audio to a wav file, and then
[*]uses lame to encode the wav file to mp3, and then
[*]removes the wave file.
[/LIST]

Here is what the /scripts/JazzClassics looks like:
[PHP]#!/bin/sh 
NOW=$(date +"%b-%d-%y")
mplayer "http://pba-ice.streamguys.org:80/wabe" -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null ;
lame -m s /tmp/mystream.wav -o "/home/philipsmith/Music/Jazz_Classics_with_H_Johnson/Jazz Classics - $NOW.mp3" ;
rm /tmp/mystream.wav ;[/PHP]

The script is owned by me because I did a:

[PHP]chown philipsmith /scripts/JazzClassiscs[/PHP]

Also, the script is executable because I did a:

[PHP]chmod 700 /scripts/JazzClassics[/PHP]

This script was suggested by: [http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/]("http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/")

I've tested each line of the script separately, and they work nicely.

Also, I've successfully used "Scheduled Tasks" to run the script as a task that launches one time.

However, I'm having trouble getting "Scheduled Tasks" to execute the text recurrently in a way that I want. 

The attachment shows the screenshot of how I set up "Scheduled Tasks" to execute /scripts/JazzClassics every Sunday at 7:31am. The 2nd attachment shows that I added the task to be executed and was scheduled.

The suggested code at the URL listed above suggested using Kcron. However, I use gnome... I loaded kcron using synaptic and can't get it to work, so I'm stuck with "Scheduled Tasks" and am struggling with it.

Thanks for your help, Ubuntu Community!

All the best,
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2010-07-04
Sorry, folks.

Any assistance will be very appreciated.

Phil

---

### Post by Old Jimma on 2010-07-04
Hi Ubuntu Community:

I found the following bug report for gnome-scheduler: [COLOR="Red"]**[https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/370754]("https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/370754")**[/COLOR]



While that thread reports the bug to be fixed as of August 2009, there is another report of it not working on November 2009 at: **[http://forum.linuxmint.com/viewtopic.php?f=47&t=36137&start=0]("http://forum.linuxmint.com/viewtopic.php?f=47&t=36137&start=0")**

I don't want to point fingers. More likely than not it is my error in some way or another. However, I'm offering this to the community as a part of my original thread that I hope will soon be solved.

Thanks!
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2010-07-05
Folks:

After

    * having not any success to get gnome-scheduler to schedule recurrent jobs (there is a documented bug in gnome-scheduler... I could not determine if it has been fixed), and
    * not being able to get kcron to work,

I used crontab.

crontab works beautifully. It is not a gui, but it works!

I found useful threads at:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto),
[http://ubuntuforums.org/showthread.php?t=1507361](http://ubuntuforums.org/showthread.php?t=1507361) (sanderj's comment), and
[http://ubuntuforums.org/showthread.php?t=1433024](http://ubuntuforums.org/showthread.php?t=1433024)

In the latter thread, pay close attention to DaithiF's comment #2. It may be that crontab wants to write out error messages to a file in order to work.

Also, in that thread, pay close attention to the comments of bodhi.zazen, or anything else he writes on the forums for that matter.

I hope this helps somebody!

Phil Smith
Duluth, GA

---

### Post by Drenriza on 2010-07-05
> every Sunday at 7:31am

```
crontab -e
```
```
31 7 * * * 0 /path/to/script
```

press : wq enter
to save the changes

---

