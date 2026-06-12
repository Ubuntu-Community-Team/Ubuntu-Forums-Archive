---
title: "Strange problem: all my internet traffic is fast except for web pages."
date: 2010-05-15
forum: New to Ubuntu
---

### Post by klanko on 2010-05-15
Ubuntu 10.04 LTS. Brand new user here. I have a peculiar problem.

All web pages that I visit load excrutiatingly slow. This is true for both image intensive sites, as well as ones that contain just text. I have used 3 different browsers (Firefox, Chrome, Opera), and the problem is the same on all of them.

The strange part is, its only the web pages that are slow. All other internet traffic is fine, if not faster than I expected. Downloading large files through the browsers is very fast. Downloading through Software Center and Update Manager is also very fast. I went to speedtest.net, and it gave me the correct speed (once it finally loaded). It's just the web pages that are slow.

I am using a HP dv6000 laptop. I understand that the IntelPRO 3945ABG used to be a pain, but it is now supported. I never had a problem with it detecting networks or connecting to them. Hardware Drivers says I have no proprietary drivers. Any ideas?

Not sure if this related, but the official Ubuntu documentation says that when you type "sudo lshw -C network" into the terminal, all listed devices should be either CLAIMED, UNCLAIMED, ENABLED, or DISABLED. However, none of these 4 words are displayed when I do so.

---

### Post by -humanaut- on 2010-05-15
Sounds like its a hardware problem (graphics) try searching the software center for i915 intel graphics should fix the problem.

---

### Post by klanko on 2010-05-15
Thanks for your reply. I searched for i915, and the only thing that came up was a driver is already installed on my laptop. I had a slight inclination that the problem did indeed involve the graphics. But other then check the driver and change a few obvious preferences, I'm not sure what else to do.

> **-humanaut- said:**
> Sounds like its a hardware problem (graphics) try searching the software center for i915 intel graphics should fix the problem.

---

### Post by 4Orbs on 2010-05-15
I would suspect your flash player browser plugin is causing the problem, and suggest you go to the Multimedia and Video section of this forum and follow the steps in the Comprehensive Multimedia and Video How-To sticky thread at the top of the forum. The problem could also be your browser java plugin. That how-to will take care of both.... and more.

---

