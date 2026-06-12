---
title: "error: 2 or more installers running at same time"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2009-03-28
I'm using the getdeb package installer to install songbird. But just as songbird was about to install, I got the following error: 

"only one software management tool is allowed to run at the same time. Please close the other application e.g. update manager, aptitude or synaptic first."

I cannot see any of those software management/update tools open on my computer. I even rebooted my computer and tried again but I received the same error. 

How do I find out which of those are running and to close all of them except for the .deb package installer?

Thanks

Brian

---

### Post by BOZG on 2009-03-28
> **Brian_Newbie said:**
> I'm using the getdeb package installer to install songbird. But just as songbird was about to install, I got the following error: 

"only one software management tool is allowed to run at the same time. Please close the other application e.g. update manager, aptitude or synaptic first."

I cannot see any of those software management/update tools open on my computer. I even rebooted my computer and tried again but I received the same error. 

How do I find out which of those are running and to close all of them except for the .deb package installer?

Thanks

Brian

Go to System->Admin and look for System Monitor.  That should give you a list of all active processes.  Kill anything that says Synaptic or Apt and try again. 

Also, make sure that you don't have any available updates.  If you have auto-updates, the auto-update notifier will start up even after a reboot.

---

### Post by Brian_Newbie on 2009-03-28
Thanks BOZG. Just before I came back to this thread, I ran the following commands I saw posted in another thread:

sudo dpkg --configure -a
sudo apt-get update

They worked! I remember the error message did say to run in terminal "dpkg --configure -a" so it turned out to be the right thing to do.

---

### Post by designateduser on 2009-08-12
this was my same problem and that did the trick for me too, thanks!

---

