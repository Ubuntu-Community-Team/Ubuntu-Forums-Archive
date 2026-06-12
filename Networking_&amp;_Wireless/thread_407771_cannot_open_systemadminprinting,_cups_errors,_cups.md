---
title: "cannot open system/admin/printing, cups errors, cups server could not be contacted.."
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by koenie53 on 2007-04-12
I posted earlier and received no real help and only 1 reply, I am trying again in the hopes that someone out there has solved this problem. I checked all the posts and tried all the suggestions but none worked.
I tried uninstalling cups through synaptic and was unable to, it said that there were errors and they needed to be fixed first, but when I tried to fix, it said it was unable to fix. I keep getting the "cups server could not be contacted. I have made so many changes due to all the posts that I tried to follow that I don't even know where to begin, but if there is a way to fix the error without having to do a complete new install of Ubuntu, I really would want to go that route.
As I said, I cannot open System,Administration,Printing, and I have tried System/Administration/Services and cups is now disabled, I have reinstalled cups and nothing, I mean nothing has worked. My problems seemed to start when I was setting up my network to allow another printer to print from my local printer, I made changes in my /etc/cups/cupsd.conf and that was when the problems began. The only other change that I made was to disable ipv6 and I don't know it that could be the cause. I would be happy just being able to make my printer a local printer again, but cannot even do that, someone please help if you can.

---

### Post by dmizer on 2007-04-12
try going to:
system > administration > services and look for "printer service".  make sure there is a check next to it.

---

