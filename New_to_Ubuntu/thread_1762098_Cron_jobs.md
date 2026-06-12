---
title: "Cron jobs"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by P=NP on 2011-05-18
I know how to set up a cron job, but how would I run a script that resides in /usr/bin/?

---

### Post by P=NP on 2011-05-18
Update: How do I answer "yes" to said command?

---

### Post by scottstensland on 2011-05-18
crontab -e

will put you into your default command line editor
where you are immediately editing the crontabs defined to your login id,
as opposed to root etc.  Once you type in your job definition, save 
and it ~~immediately~~ becomes active ( within a minute )

crontab -l

will display current crontab definitions

man crontab 

for syntax - these jobs must have some frequency of launch defined
Each cronjob will appear as a single row - left side defines timing - right side
defined the command line syntax of your process to launch

Also - lookup alternatives like startup jobs

---

### Post by rosencrantz on 2011-05-18
I'm not quite sure whether that's your problem, but if you want to automate a 'yes' user input, pipe the script/program through yes.
See this link:
[http://www.computerhope.com/unix/yes.htm](http://www.computerhope.com/unix/yes.htm)

---

