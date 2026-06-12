---
title: "running a command automatically???"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by rocka on 2010-09-04
Hi,
I'd like to run a command in a terminal at, say, 8AM for 7 days in a row, then stop.
Can anyone please tell me how to do this?

for example:
streamripper [http://radio1.internode.on.net:8000/133](http://radio1.internode.on.net:8000/133) -r -a -A -l 36000

I've had a bit of a poke around and I've read conflicting advice about using cron or a batch file, but I haven't yet seen an explanation of how to write the command(s), or where to save them, and then how to set them to run.

any help will be appreciated, as always :)

---

### Post by nagaprathyush on 2010-09-04
You can use something called crontab and achieve it! For more details read this blogpost.....
[http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

---

### Post by llamabr on 2010-09-04
Except cron won't stop after 7 days.  If you don't mind remembering to edit the crontab next week, it's the best option.

---

### Post by rocka on 2010-09-04
is there a way to specify that it should only run once, at a specific date/time? That way, I could just write it on 7 lines, and edit the date for each instance...

---

### Post by nagaprathyush on 2010-09-04
@rocka
the link i have posted earlier explains everything in clear ;) You can make crontab to run on one particular week of a month(7 days or particular days of a week), at a specific time(mins,hrs) and many other options..... please go through.....;)

---

### Post by xircon on 2010-09-04
Gnome-schedule is in the repos and should do it.

---

### Post by rocka on 2010-09-05
> **nagaprathyush said:**
> @rocka
the link i have posted earlier explains everything in clear ;) You can make crontab to run on one particular week of a month(7 days or particular days of a week), at a specific time(mins,hrs) and many other options..... please go through.....;)

Hi,
I have read through that page a few times now, but I am still having some trouble. I do not believe [unless I have missed it...] it says what to call the file, or, specifically where to save it?

I ran the command as it said at the top of that page and got this:

```
merlin@merlin-desktop:~$ crontab -e
no crontab for merlin - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.gnome
  4. /usr/bin/vim.tiny

Choose 1-4 [2]:
```

so far so good.
I chose 2, and then added the line
30 8 * * * streamripper [http://radio1.internode.on.net:8000/144](http://radio1.internode.on.net:8000/144) -r -a -A -l 36000
to the end.

But where to save it?
From the page:
```
All individual user must must use crontab command to install and edit their jobs as described above. /var/spool/cron/ or /var/cron/tabs/ is directory for personal user crontab files
```
but trying to save in /var/spool/cron results in a permissions error and /var/vron/tabs doesn't exist...

---

### Post by Paqman on 2010-09-05
> **llamabr said:**
> Except cron won't stop after 7 days.

No, but you could use it to run a script that only ran seven times (or on certain dates).

---

### Post by rocka on 2010-09-05
> **xircon said:**
> Gnome-schedule is in the repos and should do it.

Hi,
I ran "Ubuntu software center" off the "applications" menu, and did a search for Gnome-schedule. It found "Scheduled tasks", which I installed. Everything seemed to go just fine, there was no error message or anything, but when I run it nothing happens.

---

### Post by d3v1150m471c on 2010-09-05
cron **can **read the day. so it will not run after the 7th day if you specify that, unless of course you're running a process that lasts more than 24 hours. on that note you could always send a kill signal to the script with cron on the 8th day ;)

---

### Post by xircon on 2010-09-05
> **rocka said:**
> Hi,
I ran "Ubuntu software center" off the "applications" menu, and did a search for Gnome-schedule. It found "Scheduled tasks", which I installed. Everything seemed to go just fine, there was no error message or anything, but when I run it nothing happens.

From a terminal:

sudo apt-get install gnome-schedule

then run from menu (yes it is scheduled tasks) or press alt-f2 and run gnome-schedule.

Also you will probably have to make a script out of the command and run as:

gnome-terminal -e /pathto/myscript.sh

Cheers
Steve

---

### Post by rocka on 2010-09-05
> **xircon said:**
> From a terminal:

sudo apt-get install gnome-schedule

then run from menu (yes it is scheduled tasks) or press alt-f2 and run gnome-schedule.

Also you will probably have to make a script out of the command and run as:

gnome-terminal -e /pathto/myscript.sh

Cheers
Steve

Hi Steve,
still nothing I'm afraid:
```
merlin@merlin-desktop:~$ sudo apt-get install gnome-schedule
sudo: unable to resolve host merlin-desktop
[sudo] password for merlin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-schedule is already the newest version.
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4 libqimageblitz4 libkscreensaver5
  libsolidcontrolifaces4 plasma-widgets-workspace libplasma-geolocation-interface4 libksgrd4
  kdebase-workspace-bin libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4 kdebase-workspace-data
  ksysguardd libplasmaclock4 libweather-ion4 kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
merlin@merlin-desktop:~$
``` 

I've tried running from the menu, and also from that shift-F2, but all that happens is the mouse briefly turns to the turning wheel thing, then back again. Nothing is started, there are no error messages.

---

### Post by xircon on 2010-09-05
Weird, open a terminal type gnome-schedule press enter and post the output here (highlight with mouse then ctrl+shift+c)

BTW I said alt not shift!!!

Do you have universe repo selected?

Need coffee back shortly

---

