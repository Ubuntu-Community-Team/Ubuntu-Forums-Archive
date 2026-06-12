---
title: "Thoughts on user configuration for a file server/workstation"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by 50words on 2008-08-28
I am doing my own IT work, and I don't really know what I am doing, so please help me figure out the best way to structure my network.

Right now, my office is just me. I will be adding an assistant soon. I just ordered an Ubuntu workstation from Dell, which the assistant will use.

Currently, I have a file server that is doing double duty as a workstation.

The home directory for the primary user account, "businessfiles," holds all the business files (obviously). This is also the account I use to maintain the system. It has permission--through sudo--to run updates, install software, etc. Users in the group "employees" have permission to access the business files folder.

All other accounts (just me, for now) on the server are simple user accounts, with no permission to administer the system.

Is this a good setup? Should I consider creating a separate account for administrating the system, and turn the businessfiles account into a non-privileged user account?

I am currently using SSH to access files remotely, and I figured I would continue to use SSH for intra-office networking once I get the new workstation set up. Is this a good idea, or should I go another route?

Thanks for your thoughts.

---

