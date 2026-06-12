---
title: "Lightning (Sunbird) &amp; Google 100% CPU"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-09-01
I've installed the Lightning (Sunbird) add-on to Thunderbird.

I added a calendar in Lightning to synchronise with Google, following [Google's instructions for CalDAV and Lightning and Sunbird]("http://www.google.com/support/calendar/bin/answer.py?answer=99358").

The initial sync worked perfectly, taking less than a minute.

However, whenever I start Thunderbird (e.g. after a reboot), Lightning doesn't synchronise, and the CPU hits 100%. It sits there doing what seems like an awful lot of nothing at 100% CPU, until I delete the calendar from Lightning and close Thunderbird. (I've left it for 15 minutes and it's still going.)

(If I restart Thunderbird having deleted the calendar, then Thunderbird behaves properly, but of course I don't have the calendar.)

I've tried this several times, always with the same result.

It's terribly frustrating. Do you have any ideas as to how to solve this?

Linux: Ubuntu Hardy 8.04
Thunderbird: 2.0.0.23
Lightning: 0.9

---

### Post by LowSky on 2009-09-01
try this?
[https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)

---

### Post by Paddy Landau on 2009-09-01
Thank you, I will try that when I get back to my computer, and I'll let you know how well it works.

I see now (I missed it before) that Lightning has a known issue: "The **experimental** support for viewing remote calendars      offline has various known issues in the area of performance and calendar      data display. It does not support the offline editing of events and tasks".

---

### Post by Paddy Landau on 2009-09-02
> **LowSky said:**
> try this?
[https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)
Provider did the trick!

Thank you again.

---

