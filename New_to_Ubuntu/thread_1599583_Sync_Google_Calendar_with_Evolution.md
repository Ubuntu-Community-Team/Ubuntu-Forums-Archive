---
title: "Sync Google Calendar with Evolution?"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-10-18
Hey everyone,
Does anyone know how to sync my Google calendar with the Evolution calendar? I'd really like to work from my desktop as much as possible. Thanks!

---

### Post by blazemore on 2010-10-18
Google Calendar integration used to be hard to set up with Evolution. You could either do a read-only calendar or use [GCalDaemon]("http://www.linux.com/articles/60231"), which most non-Evolution users still use. But read-only was pointless and GCalDaemon could be slow.


Then, [Ebby Wiselyn]("http://ebbyw.wordpress.com/") hacked Google Calendar support for Evolution during the Google Summer of Code, and the code eventually made it into Evolution.


To  add a Google Calendar, first go to the Calendars section of Evolution  and create a new calendar with File -> New -> Calendar.
Change the  type to Google, give it a name, put in your username (not your email),  then click Retrieve List.
Select the calendar you wish to add from the  drop-down list, and optionally assign a colour.
You can also choose  whether to cache the calendar offline. Your calendar should then show up  under the Google folder.
[URL="http://www.linux.com/var/uploads/Image/articles/154875-2.png"]
[/URL]Support  for Google Calendar isn't perfect, however. Evolution doesn't currently  support repeating or all-day events (though that may be coming soon).  Also, you can't sync your tasks or memos with Google Calendar, since  GCal supports neither.

---

### Post by Ranger_Joe on 2010-10-18
Blazemore,
You're awesome. Totally worked and is awesome. I'll calling this one solved! 

Thanks!

---

### Post by bombz on 2010-11-11
I had it working well before upgrading to Maverick, using the CalDAV method. After the upgrade, when I click the gnome-clock applet, it takes forever to show the calendar, and the google calendar events don't even show. Besides that, I can't edit the events in Evolution anymore.
I tried to erase the calendar and make a new one following this new method, but with no success. It works well until the next reboot.
I suspect that it's related to the cache folders. I noticed that a folder with a name starting with "caldav___" was created in the cache folder (.../.evolution/cache/calendar), by the time the problem first happened (after the reboot). In the cache folder there's still the folder created when setting up the sync (that worked for a while). I suspect that Evolution is trying to read a file from the wrong location.

Does anyone have a similar problem? Thanks!

---

### Post by bombz on 2010-11-11
After a new google search I found that the bug was already reported:
[LEFT]**[[SIZE=1]https://bugs.launchpad.net/bugs/642830[/SIZE]]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/642830")**[/LEFT]

---

### Post by willix on 2010-11-13
I've just installed Ubuntu 10.10, got my gmail acccount up and trying to sync my calendar and contacts. 
However when I try and create a new calendar, I dont have the google type (only display "On this Computer", "On the web" and "weather")
What do I need to get the google type?

---

### Post by vangelas on 2010-11-18
I am on ubuntu 10.10 64 bit. I get the error message "Cannot read data from Google server.
Cannot resolve hostname (www.google.com)":o

---

### Post by mannih2001 on 2010-11-25
> **willix said:**
> What do I need to get the google type?

Install the evolution-plugins package and you should be fine. At l
east it worked for me.

---

### Post by sinisterstuf on 2010-11-25
^ I have the same problem as you, vangelas!

I'm using Ubuntu 10.10 32-bit, I've typed my username only in the username field, not [email]username@domain.com[/email] , I get the same error for trying to sync contacts, but the e-mail works fine using IMAP or POP3, both work.

What are we supposed to do?!

---

### Post by wvzamora on 2010-12-07
I had the same problem, but updating/upgrading Evolution, then restarting it, solved the problem...

---

### Post by masood_mj on 2011-02-03
Actually non of the above solutions worked for me. Ubuntu 10.10
I installed libopensync1exp7 library and it worked

---

### Post by ohdung on 2011-02-09
> **masood_mj said:**
> Actually non of the above solutions worked for me. Ubuntu 10.10
I installed libopensync1exp7 library and it worked

This worked for me as well.

---

### Post by topler on 2011-02-23
I have been suffering the same/ similar issue which was due to a classic user error.

In my case, I could successfully create a new Google calendar but the calendar never showed the entries/ appointments. Though, I have been able to create new calendar entries from within Evolution but they never ever showed up in Evolution itself.

Now, I noticed that Evolution has a feature which allows to filter the calendar entries. In my case the filter was set to "Personal". (Wonder if this is the default filter to trap users?)

This **filter** option is called "Show" with a drop down menu right next to it. It's located right between the calendar grid and the menu bar at the top. After I switched it to "**Any Category**" I could see the calendar entries as are present on Google.

Hope this come in handy for other users!

---

