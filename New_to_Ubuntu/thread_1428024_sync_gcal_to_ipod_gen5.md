---
title: "sync gcal to ipod gen5"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by DarinB on 2010-03-12
I can put my gcal to my ipod by manually adding the .ics file by exporting the cal to my desktop > extract zip > drag .ics to my ipod. 
is there a way to sync it with ubuntu? i heard of a script for windows but not for ubuntu?? any ideas anybody? NO i do not go online with my phone yes that would be the easiest but the most expensive.

---

### Post by Method X on 2010-03-12
Hello

> Create a script to fetch the Google Calendar and copy it to your iPod:

# download the Google calendar ical file through the private URL
wget -c -N [http://www.google.com/calendar/ical/yourname%40gmail.com/public/basic.ics](http://www.google.com/calendar/ical/yourname%40gmail.com/public/basic.ics)

# copy it to the iPod
cp basic.ics /media/your-ipod-name/Calendars/google.ics
rm basic.ics
Now configure Ubuntu so that this script is run whenever you plug your iPod in. Add the following line to /etc/udev/rules.d/80-programs.rules:

KERNEL=="sdc1", RUN+="/path/to/your/script.sh"
(Replace sdc1 with the appropriate device name, which you can find out by typing “df”.)
;)

---

### Post by DarinB on 2010-03-13
sounds a bit too complicated for my level of expertise, is there an other way?
and have you heard of gcaldaemon?

---

### Post by Method X on 2010-03-13
> **DarinB said:**
> sounds a bit too complicated for my level of expertise, is there an other way?
and have you heard of gcaldaemon?

Well, if i understand you right, you are looking for this? 
[http://gcaldaemon.sourceforge.net/download.html]("http://gcaldaemon.sourceforge.net/download.html")

---

