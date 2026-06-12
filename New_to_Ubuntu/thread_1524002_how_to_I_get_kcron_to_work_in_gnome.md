---
title: "how to I get kcron to work in gnome?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-07-04
Hi Folks:

I run gnome and had a little problem with gnome-scheduler described at: **[http://ubuntuforums.org/showthread.php?t=1523782]("http://ubuntuforums.org/showthread.php?t=1523782")**

So, I installed **kcron**... see the attachment showing synaptic.

I looked for **kcron** and **Kcron** as program under Main Menu and also under applications... couldn't find it.

So, i tried to execute **kcron** from the command line. I got the message 'No command kcron found..' See the second attachment.

**Can somebody please suggest how I might get kcron to work in gnome?**

Thanks!
Phil Smith
Duluth, GA

---

### Post by cariboo on 2010-07-04
The kcron package doesn't really do any thing. From synaptic:

> program scheduler frontend - transitional package

This package helps migrating from the kcron standalone app to the kde
config module in kde-config-cron.

It is a transitional package that can be safely removed.

---

### Post by Old Jimma on 2010-07-04
Hi Cariboo:

Thanks for your reply.

If kcron doesn't do anything and gnome-scheduler has a bug that doesn't allow users to program starting times later in the day for recurring processes because of a documented bug, how are users supposed to schedule jobs on a recurring basis?

Thanks,
Phil

---

### Post by Old Jimma on 2010-07-05
Folks:

After [LIST]
[*]having not any success to get gnome-scheduler to schedule recurrent jobs (there is a documented bug in gnome-scheduler... I could not determine if it has been fixed), and
[*]not being able to get kcron to work,
[/LIST]
I used crontab. :p

crontab works beautifully. It is not a gui, but it works!  :p

I found useful threads at: 
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto"), 
[http://ubuntuforums.org/showthread.php?t=1507361]("http://ubuntuforums.org/showthread.php?t=1507361") (sanderj's comment), and 
[http://ubuntuforums.org/showthread.php?t=1433024]("http://ubuntuforums.org/showthread.php?t=1433024")

In the latter thread, pay close attention to DaithiF's comment #2. It may be that crontab wants to write out error messages to a file in order to work. 

Also, in that thread, pay close attention to the comments of bodhi.zazen, or anything else he writes on the forums for that matter.

I hope this helps somebody!

Phil Smith
Duluth, GA :)

---

