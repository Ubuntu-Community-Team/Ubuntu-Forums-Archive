---
title: "Trying to get my second hard drive to work"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by tonsil on 2010-05-03
I have a second hard drive which wasn't plugged, so I set the jumper settings on both drives and booted. BIOS recognizes the correct master and slave drives, but right after the system counts up the memory the system freezes. Any opinions on what I could do?

Previously I had installed Fedora on that second drive and had checked an option which I think was something like lock the file system or something, which would prompt me for a password on each boot. Could that be related? Pardon my ignorance :)

---

### Post by spiky001 on 2010-05-03
I had a prob with grub when 2nd harddrive fitted, it was to do with the way it was on the ribbon?  the booting disk for better words, had to be the 1st 1 on ribbon 2nd drive was at end, might not solve your prob but it worth a thought

---

### Post by kaltoza on 2010-05-03
If the system is freezing during the POST test, or shortly just after, try setting the
jumpers to both CS (Cable Select). Then you can set the priority of the drives in
your BIOS configuration.
 
This sounds familiar, and this is what I did to work around this announce.
 
Well hope this helps
 
Cheers

---

