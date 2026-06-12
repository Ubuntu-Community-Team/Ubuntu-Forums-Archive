---
title: "Automatic Evolution Back-up Question"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-04-17
Hi Ubuntu Community:

In Evolution, if you want to do a back up manually, you do:

file > backup settings.


This requires you to have Evolution open, and requires you to do the 'work.'


I want a shell script that will back up Evolution settings automatically. I will use crontab to execute the shell script once a week.

[COLOR="Red"]**However, how to I write that shell script??**[/COLOR]

Thanks,
Phil Smith
Duluth, GA

---

### Post by Zimmer on 2011-04-17
I think you will find that the Evolution backup utility just copies and tars the .evolution folder existing in your home directory.

So, automation is not far away....

---

### Post by Old Jimma on 2011-04-17
Hi Community:

I did a little more digging to find out how to automatically back up Evolution... and found a [COLOR="Red"]**2005**[/COLOR] thread about this at: [http://ubuntuforums.org/showthread.php?t=75859]("http://ubuntuforums.org/showthread.php?t=75859")

I wonderer if the information at that 2005 thread is still accurate...

The thread recommends the following:

#!/bin/bash
#
gconftool-2 --shutdown
evolution --force-shutdown
cd ~
tar -cvzf evolution.tar.gz .evolution .gconf/apps/evolution .spamassassin .gnome2_private/Evolution

There were reports in the 2005 thread that this didn't backup everything... For example, smtp settings were not saved.

[COLOR="Red"]**Does anyone know what would be a complete list of files that Evolution must backup for a COMPLETE Evolution backup?**[/COLOR]

Thanks!
Phil Smith
Duluthistan, GA

---

### Post by tnc on 2011-07-18
So, wouldn't it be lovely to have an informed reply to this question.

---

