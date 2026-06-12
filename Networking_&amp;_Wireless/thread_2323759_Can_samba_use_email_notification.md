---
title: "Can samba use email notification"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by detox2 on 2016-05-07
Hello All!

i would like to set up a samba server for a small office, but the office manager wants owncloud.  I feel samba is safer and have much better admin controls.
However, the office manager wants staff to receive an email when ever a file is added to a specific folder.  Here is the example:
The office has 4 staff (Bob, Sam, Joe, Ted) and office manager (Bubba).  Each staff has their own samba folder and there is an "office folder" named "Staff_Stuff".  When the office manager (Bubba) places a file in "Staff_Stuff", he wants an automated email notification to be sent to each person.

Can this be done?

Thanks for any input

---

### Post by SeijiSensei on 2016-05-08
I don't know of any way to do this with Samba itself, but you could write a bash script and run it from cron that would check the timestamps of the files and send a notice whenever a new one appears.  Cron jobs run at most once per minute, so if you need more immediate notifications, that won't work.

---

### Post by detox2 on 2016-05-08
Thanks for the input!  i will try that approach

---

