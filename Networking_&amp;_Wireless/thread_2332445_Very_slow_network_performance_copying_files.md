---
title: "Very slow network performance copying files"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by andrewgerm on 2016-07-31
Good day all
I've spent a weekend troubleshooting this now, and been reading up on many things, but seems I have yet to find a solution.

I recently did a complete re-install of a home / office server, running Ubuntu 16.04.1 LTS (Kernel 4.4.0.31 generic) 64 bit.
When I backed up files from the server, I copied them to a USB 3 drive attached to my Windows 10 64 bit machine. Both machines are connected via GB NICs to a GB unmanaged switch. Speeds were around 80mbps then. I also had jumbo frames enabled then.

With the re-install, I have speeds around 1 or 2 mbps, copying files back. I have tried this with default MTU of 1500, and using 9000 (and 9014, matching the Win 10 machines card). I have also tried adding "socket option TCP_NODELAY" to no avail.

This is a rather general purpose server, running websites that are being developed (via Apache), MySQL databases, file server for shared home media, as well as storage for raw footage of videos for current film projects (so they can be accessed by anyone working on the project), as well as synchronising to cloud storage for access by any devices.

Any hints, help or tips as to where to begin looking for the cause of the slow performance would be greatly appreciated.
All software updates have been applied to the server as of posting this request. It is a headless server, with administration done via SSH from any number of other devices in the office or house, connecting via GB, 100MB or wireless networks.

Thank you in advance.

---

