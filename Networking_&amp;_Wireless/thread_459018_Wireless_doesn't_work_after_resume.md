---
title: "Wireless doesn't work after resume"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by CycleGeek on 2007-05-30
I'm running an Inspiroon 700m with the intel 2915ABG wireless card - it's been using the ipw2200 driver with no issues except for the fact that it randomly doesn't log on after resuming from hibernate.  Very frustrating since I'm not a big fan of restarting.

When I click on the network widget I see the wireless network I'm trying to attach to but nothing can make me actually attach to it - I right click and the connection never works.

Any help?  It doesn't happen all the time but when it does it's very annoying.  Could this be an issue with my wireless router?

---

### Post by tommie74 on 2007-06-17
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

