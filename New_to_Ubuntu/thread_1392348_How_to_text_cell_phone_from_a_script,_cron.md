---
title: "How to: text cell phone from a script, cron"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Rayve on 2010-01-28
All,

I had a few requests to post the script I created to text my cell phone with a reminder to take my medicine, which I then put into a cron job... at the risk of putting out TMI, here it is (I called it "cellreminder"):

```

#!/bin/bash
echo 'Take birth control!' | mail -s 'Birth control' <myphonenumber>@txt.att.net <secondphonenumber>@txt.att.net

```

Note: My steps for getting this working were posted here: [http://ubuntuforums.org/showthread.php?t=1331974](http://ubuntuforums.org/showthread.php?t=1331974)  in case anyone else has similar troubles.

This sends a text message to my phone, from my gmail account, with a subject of "Birth control" and a message to "Take birth control!".  I put it in a cron to run every night at 9 p.m., EST, and this came in really handy while I was traveling over Christmas because no matter what time zone I was in, it was always 9 p.m. EST when I got my message and it helped stay on time.

I've now put similar cron jobs in the future, to remind me of appointments that occur once every six months, and so forth.

Here is an excerpt of my crontab:
```

# m h  dom mon dow   command
00 21 * * *    /home/candice/cellreminder
00 12 1 May,Nov *    /home/candice/jewelryreminder 
```

What this does is runs the script "cellreminder" (see above) at 9 p.m. (2100 hours) every day.  It will run the "jewelryreminder" script at noon (1200 hours) the first of May and the first of November, every year.

There are excellent resources out there about cron and how to utilize this great tool (see [http://www.linuxhelp.net/guides/cron/](http://www.linuxhelp.net/guides/cron/) for instances), but the brief over view is:

Minute  Hour  Day of Month  Month  Day of Week  Command to run/Script location (you can see this abbreviated in crontab itself)

With an asterisk "*" to indicate "all" for that section.  For example:

30 12 * * Mon-Fri  /home/candice/lunchtime

would execute a script called "lunchtime" at 12:30 p.m. every Monday through Friday, no matter what month it is, whereas:

30 12 * June-Sept Mon-Fri  /home/candice/lunchtime

would only execute at 12:30 p.m. Mon-Friday for the months of June-Sept... hopefully, you get the idea, and are intrigued enough to read more information.  :)

Questions?  I'm by no means an expert at either cron or bash scripts, but discussion is always good!  This is my first time trying to post an explanation of anything rather than a question, so if anything isn't clear, please let me know!

---

### Post by CrusaderAD on 2010-08-25
I setup something similar, but the texts come through extremely slow, sometimes several hours later. Is there some trick to getting them sent and received faster?

---

### Post by CharlesA on 2010-08-25
I don't know of any trick, I've got something similiar set up and I get the text within a few minutes.

---

### Post by LowSky on 2010-08-25
> **raptormanad said:**
> I setup something similar, but the texts come through extremely slow, sometimes several hours later. Is there some trick to getting them sent and received faster?

if all you want are reminders, set up a Google calendar account and you can use that to SMS reminders. This way if the PC is ever off or goes down you will still get the reminders.

---

### Post by CrusaderAD on 2010-08-25
Must just be At&t that's slow. It's terribly slow. It's not just reminders with me. I setup alerts for some web development.

---

