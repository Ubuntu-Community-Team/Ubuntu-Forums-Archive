---
title: "Can I make Cron show it is working?"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-08-24
I have setup a cron job to automate a [repository download]("http://ubuntuforums.org/showthread.php?t=352460") that I usually do manually. Doing it manually has unfortunately caused me to reach my ISPs download limit and now my speed has been throttled to 64kb/s for the next 14 days. I will survive the slower speed :lolflag: but have decided to try to automate the process to occur during my ISPs "Off-Peak" time for when I have my full speed back.

I have an executable txt file which works manually and even works when manually running the task in Gnome Task Scheduler. The problem is it only partially works as a cron job and I am unable to see any indication of progress like I would if I did it manually.

This brings me to my question. Is there a way to get the cron job to show its progress so I know whats happening? All I want is for the Terminal to open and show the jobs progress as it would if I clicked on the executable txt file manually.

Thanks in advance.
Michael.

---

### Post by kpkeerthi on 2009-08-24
You can direct the output from your cron job to a file and then inpect the file later. Or have the cron email you the output of the job.
```

* * * * /my/cron/job > /home/<user-id>/some-log-file.log 2>&1

```

```

* * * * /my/cron/job | mail -s 'My cron output' <user-id>

```
* In most cases, setting the MAILTO variable in the crontab alone would suffice. Google to find out more.

---

### Post by Paddy Landau on 2009-08-24
You want the terminal to open. That means that you don't want to execute your script; instead, you want to execute the terminal, and instruct the terminal to execute your script.

Let's say that your script is called *downloadrepository* in your home directory and you want it to run at 2 a.m. every day.

Tell cron to load gnome-terminal and execute your script, as follows (I've assumed that your username is *k3lt01*):
```
00 02 * * * gnome-terminal -e '/home/k3lt01/downloadrepository'
```Note that when the script finishes, the terminal will close. If you don't want that, then put as your last line in *downloadrepository* the following command. This will cause your script to pause with the indicated prompt.
```
read -p 'Press Enter to close.'
```

---

### Post by k3lt01 on 2009-08-24
kpkeerthi, thanks for your input. I wasn't looking for a log output but can see its value so I will play around with the idea later on.

Paddy Landau, this is exactly what I am looking for. However, I am still having much the same problem. I can do it all manually using gnome task scheduler's run task button but the cron job wont automate it properly with a terminal appearing. I played around with the syntax a bit after giving your code quite a few attempts but still no automation of the terminal.

---

### Post by mkrahmeh on 2009-08-24
i remember trying to invoke the gnome-terminal with a command argument -e directly from another terminal (konsole), but an error message kept popping up, which says that the gnome-terminal cannot establish a child process. 

it seems to me that your cron job ddnt work with the gnome-terminal for the same reason, there was a problem in creating a child process for the gnome-terminal, which is the download repos in your case !! am not sure as its based on past experience, but try a simple command in the shell like
```
gnome-terminal -e `ls /`
```
and see what happens

---

### Post by k3lt01 on 2009-08-24
mkrahmeh, I got the message in a txt box telling me "there was an error creating the child process for this terminal". Does this mean it wont do what I want then?

---

### Post by Paddy Landau on 2009-08-24
> **k3lt01 said:**
> Paddy Landau, this is exactly what I am looking for. However, I am still having much the same problem.
Sorry, when I posted I hadn't had the time to test. Oops.

It seems that cron can't open the display. So, you'll have to have some other way to display your progress.

Using a log, as kpkeerthi said, would work fine, provided that the log regularly updates; you can spool the output to the log and use another terminal to watch it (use *tail -f*).

The only other way that I can think of is to write a never-ending script that wakes itself up at the required time and goes to sleep when it's finished. Start that script in a terminal as part of your boot-up process. Start it minimised or in another workspace so that it's not in your way (you can use a combination of the title (*gnome-terminal -t*) and devilspie to control where and how it opens).

---

### Post by Paddy Landau on 2009-08-25
New information, thanks to [kpkeerthi]("http://ubuntuforums.org/showthread.php?p=7843435#post7843435")...

cron can open a terminal.

Read the [Cron Community Documentation]("https://help.ubuntu.com/community/CronHowto").

The command in crontab would be:
```
00 02 * * * env DISPLAY=:0 gnome-terminal -e '/home/k3lt01/downloadrepository'
```Regarding the error message that you posted, "There was an error creating the child process for this terminal." That means that the command for gnome-terminal (i.e. the bit after -e) could not be understood. That would happen if you misspelled the command, or gave the wrong path. It could also happen if you used a built-in command such as *read*, for example:
```
gnome-terminal -e 'read -p "Boo!"'
```If you want to use these commands, put them inside a script.

---

### Post by k3lt01 on 2009-08-25
Paddy and kpkeerthi, thanks for your help I will give this new code a try tonight after work.

---

