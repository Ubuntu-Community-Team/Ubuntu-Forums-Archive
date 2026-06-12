---
title: "upgrade 7.10 to 8.04"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by rcbinwi on 2009-07-30
I want to upgrade from 7.10 to 8.04.  When I check for updates, update manager does not give me the option to upgrade to the new(er) version.  How can I get that option to update?

---

### Post by beastrace91 on 2009-07-30
Open your update manager and go to settings, there should be an option for "distribution upgrades" be sure they are enabled.

But just as my 2 pence, I would recommend doing a fresh install of Ubuntu to upgrade because as with any OS the upgrade process does not always go smoothly.

~Jeff

---

### Post by rajeev1204 on 2009-07-30
> **beastrace91 said:**
> Open your update manager and go to settings, there should be an option for "distribution upgrades" be sure they are enabled.

But just as my 2 pence, I would recommend doing a fresh install of Ubuntu to upgrade because as with any OS the upgrade process does not always go smoothly.

~Jeff

Hi
This is not entirely true, and this is the preferred method of upgrading to a newer version.Also the developers want to perfect this and so users are recommended to upgrade this way so any minor bugs can be fixed.A backup is what is important when upgrading any OS and i would suggest backup all important data.


In a terminal, sudo update-manager -d will bring up the upgrade.



regards
rajeev

---

### Post by jerrrys on 2009-07-30
software sources>updates>release upgrade>normal

and thinking about it.  as i recall you need to deactivate some third party sources, please to research this...

---

### Post by starcannon on 2009-07-30
> **rcbinwi said:**
> I want to upgrade from 7.10 to 8.04.  When I check for updates, update manager does not give me the option to upgrade to the new(er) version.  How can I get that option to update?


If you have not already setup a separate /home partition, now would be an excellent time to take care of that safe and sane little chore as well. It will add a bit of tedium to this particular install, but it has the benefit of allowing you to do fresh clean upgrade installs without the mess in the future.

If your interested holler out, I can help walk you through it.

GL and HF

---

### Post by rcbinwi on 2009-07-30
First, I don't have any option for settings on the update manager.

Second, when I run the update manager from a terminal I get a single-line message
warning: could not initiate dbus

So neither solution works, unfortunately.  Any other ideas?

I should have said earlier, a couple weeks ago it asked me if I wanted to upgrade to 8.04, but I said no, as I didn't have time.  It's no longer asking me.

---

### Post by rajeev1204 on 2009-07-30
> **rcbinwi said:**
> First, I don't have any option for settings on the update manager.

Second, when I run the update manager from a terminal I get a single-line message
warning: could not initiate dbus

So neither solution works, unfortunately.  Any other ideas?

I should have said earlier, a couple weeks ago it asked me if I wanted to upgrade to 8.04, but I said no, as I didn't have time.  It's no longer asking me.

OK i understood your problem.The Ubuntu version 7.10 has reached end of life so the servers for upgrade will not work now . It was supported 18 months for updates,so that was over april 2009.

You will need to burn the latest ubuntu CD and install it.


Good luck.

regards
rajeev

---

### Post by rcbinwi on 2009-07-30
That's easy enough.  Thanks for the help!

---

### Post by rcbinwi on 2009-08-04
> **starcannon said:**
> If you have not already setup a separate /home partition, now would be an excellent time to take care of that safe and sane little chore as well. It will add a bit of tedium to this particular install, but it has the benefit of allowing you to do fresh clean upgrade installs without the mess in the future.

If your interested holler out, I can help walk you through it.

GL and HF

I'm ready to set up the partition.  Can you give me a hand, Starcannon?

---

