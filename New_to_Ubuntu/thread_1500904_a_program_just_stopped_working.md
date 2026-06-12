---
title: "a program just stopped working ??"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by ave2 on 2010-06-03
Hi I have been using the program "scheduled tasks" which allows you to schedule commands to be run in the terminal. I hear its a front end for "cron" but I have no idea how to use cron. 

anyway It was working perfectly, until I scheduled about 5 tasks, and suddenly all the tasks disappeared form the list. So I closed the program, opened it up again and the program no longer starts. 

I then uninstalled, and reinstalled, still wont start. 

I ran it in terminal and get the following:

brad@brad-desktop:~$ /usr/bin/gnome-schedule
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 308, in schedule_reload
    data = self.at.read ()
  File "/usr/share/gnome-schedule/at.py", line 514, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/at.py", line 174, in parse
    if script[-1] == "\n":
IndexError: string index out of range

---

### Post by LowSky on 2010-06-03
see if it has a hidden file in your /home folder, maybe named .gnome-schedule

delete that folder and try to reopen the program.

---

### Post by ave2 on 2010-06-03
no, there dont appear to be any hidden files by that name

---

### Post by AnThoMan on 2010-08-18
I am having a similar problem - installed gnome-schedule, uninstalled, reinstalled etc etc but no GUI displays..terminal shows similar messages:

```
andrew@andrew-laptop:~$ /usr/bin/gnome-schedule
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 304, in schedule_reload
    data = self.crontab.read ()
  File "/usr/share/gnome-schedule/crontab.py", line 452, in read
    data.append([title, self.__easy__ (minute, hour, day, month, weekday), preview, line, linecount, time, self, None, job_id, "", "","", _("Recurrent"), "crontab", output, time])
  File "/usr/share/gnome-schedule/crontab.py", line 717, in __easy__
    return lang.translate_crontab_easy (minute, hour, day, month, weekday)
  File "/usr/share/gnome-schedule/lang.py", line 159, in translate_crontab_easy
    return translate_crontab_easy_common (minute, hour, day, month, weekday)
  File "/usr/share/gnome-schedule/lang.py", line 191, in translate_crontab_easy_common
    return (_("On every day at %(time)s") % { "time": lc_time(hour, minute) } )
  File "/usr/share/gnome-schedule/lang.py", line 135, in lc_time
    hour = "%02d" % int(hour)
ValueError: invalid literal for int() with base 10: '2*'
```Any ideas? The message is beyond me...

---

### Post by AnThoMan on 2010-08-18
OK, I typed "crontab -e" in the terminal and displayed all the scheduled tasks I have... which I didn't realise.

```
0 9 * * * /usr/bin/clamscan --detect-pua -i -r / --exclude-dir=/proc --exclude-$
47 2* * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourceforg$
47 2* * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourceforg$
47 2* * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourceforg$
47 2* * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourceforg$
47 */4 * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourcefor$
47 */4 * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourcefor$
47 */4 * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourcefor$
47 */4 * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourcefor$
47 */4 * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourcefor$
47 */4 * * * wget -q -O ~/.backgrounds/clouds_2048.jpg http://xplanet.sourcefor$
```

As you can see, there are numerous of the backgrounds/clouds as I was trying to get a live Earth image as my desktop. During these attempts the gnome-schedule part of this link:
[http://www.njl.us/rotating-picture-of-the-earth-as-ubuntu-wallp](http://www.njl.us/rotating-picture-of-the-earth-as-ubuntu-wallp)
did NOT appear to be working for me i.e. the schedule list wasn't updating, in fact, it went blank and the clamscan task also disappeared.

Do I simply delete the duplicates to ease the program? I assume it is very confused with what I have asked it to do..?

Any help is much appreciated,

Andrew

---

### Post by silverglade00 on 2010-08-18
Yes, if you do crontab -e, you are in edit mode. Just delete the lines you don't want. crontab -l is list mode.

---

### Post by AnThoMan on 2010-08-18
Excellent, gnome-schedule GUI now loads. Thanks.

Hope this solves ave2's problem too.

---

### Post by wynand2020 on 2010-08-18
Install Windows

---

