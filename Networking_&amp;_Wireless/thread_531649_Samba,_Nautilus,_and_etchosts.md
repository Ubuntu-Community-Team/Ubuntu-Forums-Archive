---
title: "Samba, Nautilus, and /etc/hosts"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by kidcharles on 2007-08-21
I don't have a problem (anymore) but I thought I'd post my solution here since I couldn't find the issue or fix anywhere on the forums.

I had a problem viewing samba shares using Places->Network. The machine would show fine with its name in Nautilus, but after double clicking on the icon it would hang for a bit then say:

"The folder contents could not be displayed. Sorry, couldn't display all the contents of 'Windows Network: hostname".

I noticed that what Nautilus did after I double-clicked on the icon was to try to reach 'smb://hostname' using the hostname, not the IP address. Well, I hadn't added this particular host to the /etc/hosts file, so this of course meant that Nautilus didn't know where to look. After adding a line to the hosts file (e.g. 192.168.1.2 hostname), Nautilus was able to show the files.

---

