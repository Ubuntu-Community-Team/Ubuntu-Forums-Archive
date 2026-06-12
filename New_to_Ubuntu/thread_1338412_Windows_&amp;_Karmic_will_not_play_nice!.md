---
title: "Windows &amp; Karmic will not play nice!"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by fleamour on 2009-11-26
I'm dual booting XP with Karmic Ubuntu.  

The problem I come across is when hibernating Ubuntu then booting XP from grub, also hibernated, either the keyboard will not initialise properly or a USB device will malfunction (my mouse.)  I have to reboot Windows each time to get keyboard mouse working.  Most annoying.  I have not verified if this happens without hibernating yet. 

Ideally I'd like to leave both hibernated for quick start up depending which OS suits my needs best.  I would of thought that they should not affect each other but this is a very real problem.

I am booting the latest generic kernel.

Any thoughts?

---

### Post by fleamour on 2009-11-26
I suspected package pysdm back along, as this tries to auto mount both my Windows partitions as I originally told it to.  However after uninstalling the package, it still carries on mounting my Windows partitons.

I guess this is causing the problem when resuming XP from hibernate.  How can I get round this?  Help much appreciated...

---

### Post by fleamour on 2009-11-26
Finally!  Re-installed storage manager & deleted configuration for Win partitions.  Then I can hibernate XP (takes an age to start up otherwise) & just reboot Ubuntu each time (very fast to start up.)  

This keeps both OS's happy!  Cannot hibernate both for some reason but at least it saves investing in Win 7.

---

