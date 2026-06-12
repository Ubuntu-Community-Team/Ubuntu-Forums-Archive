---
title: "Advice on Reinstalling 9.10?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by lakelovers on 2009-12-12
I haven't research this because I have no idea how to ask the question. Since upgrading to 9.10, I've had multiple problems: most irritating is random freezing. Also, no sound and no video. Do you think I might solve some problems with a fresh install of 9.10? I assume I would have to remove 9.04, first, but I'm not sure how to do this. Fortunately I do have most files backed up. I use Gnome but have KDE on my computer. No Windows. I'm thinking about making my desktop exclusively Gnome .I rarely go to KDE, but I do use some KDE apps. I'll welcome all thoughts on these actions.

---

### Post by NCLI on 2009-12-13
Reinstalling might fix your problem, so it sounds like a good idea.

Make sure everything is backed-up, then download Ubuntu 9.10, write it to a cd(or request one from ShipIt), then install it. Make sure you install to the partition you currently have the not-working 9.10 on.

---

### Post by running_rabbit07 on 2009-12-13
To add to NCLI's post, I would recommend creating the /home partition. The /home partition allows you to reinstall without losing data.

---

### Post by lakelovers on 2009-12-15
Thank you very much. I've downloaded an ISO, and now have a problems burning it to a CD. (I get and message saying the ISO is too big for the CD.) Don't have a solution for that, yet, but I may download another ISO. I'll definitly install it on a /(home) partition.

---

### Post by Anuovis on 2009-12-15
> **lakelovers said:**
> Thank you very much. I've downloaded an ISO, and now have a problems burning it to a CD. (I get and message saying the ISO is too big for the CD.) Don't have a solution for that, yet, but I may download another ISO. I'll definitly install it on a /(home) partition.

I do not think any Ubuntu ISO files are bigger than the standard CD. You might want to check that disk first or try another one.

You do not install the system on /home, that one is for your documents and personal settings. Install it over the present Ubuntu partition. Btw, if you do not have a separate /home partition now, it is possible to create one on new install. Just be sure to check manual partitioning during the setup and go from there. You have to specify the size and add the mount point as ***/home*** . The ***/*** (root) mount point will be for the rest of the system.

---

### Post by northern lights on 2009-12-15
While the rabbit's suggestion is one you ought to follow, it's both phrased weird and you haven't understood it correctly.

If you create a separate /home partition during the installation process, a possible future fresh install will not require backing up personal data.

A reinstall is most likely your best option as it will be the fastest way to a functioning Karmic. From what you describe, your system appears pretty shot and troubleshooting would be much more tedious than a fresh install.

---

### Post by audiomick on 2009-12-15
allow about 10 - 15 GB for the system partition, mounted at /
swap should be a bit bigger than your RAM
the rest of your disc for the /home partition

---

