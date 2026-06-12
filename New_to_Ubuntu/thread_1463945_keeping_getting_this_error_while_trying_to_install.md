---
title: "keeping getting this error while trying to install"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-27
I keep getting this error while trying to install stuff and I can not figure out how to fix it....any ideas?

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_karmic_partner_binary-i386_Packages)

---

### Post by bodhi.zazen on 2010-04-27
Are you running another soft ware management application such as add/remove , synaptic, or the softwware center ?

You may only run one such application at a time.

Are you running the application with sudo ?

sudo apt-get ....

In terms of a duplicate source, it does not matter. If you want to fix the message, edit /etc/apt/sources.list and remove duplicates.

---

### Post by Hospadar on 2010-04-27
I find this happens to me sometimes when I open the update window, forget about it, and then try to install some things.

---

### Post by joenewtzie on 2010-04-27
Got it, thanks everyone again! You guys are great, I just made the switch to Ubuntu today from Windows 7 and have been trying to grasp this learning curve! Thanks again!

---

### Post by ac7nj on 2010-04-28
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

I also have this error with update mamager, however I have nothing else running.

I tried doing "sudo apt-get update" thinking this might work better than update manager. This didn't show any errors but I'm new and don't know if the updates were installed because update manager still list the same updates needed

Randy

---

### Post by gethighprlinks on 2010-04-28
I think this is a real helpful post and will work as an alert. Hope you will get solution soon.

---

