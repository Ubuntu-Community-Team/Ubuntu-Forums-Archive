---
title: "Changing video drivers to non-proprietary"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-08
I need to uninstall the NVidia driver I have installed. If I do this, while I'm using the driver what happens? Does it blow up the GUI? Harm the OS? 

Once I reboot, will Karmic find some linux video driver inside itself and use it?

Can the NVidia drivers be removed during a LiveCD session, much like the OS not being mounted in a LiveCD session?

---

### Post by ukripper on 2009-12-08
you can disable System-->Administration-->Hardware drivers and disable the nvidia driver in Live cd/normal installtion if you want. It will revert to lower resolution VESA drivers by default. 

Why do you want to do that anyway?

---

### Post by Mark_in_Hollywood on 2009-12-08
Why? you ask . . .

After d/l the Karmic "Desktop Install" cd, I changed from ext3 to ext 4.

Upon Karmic install, the screen or desktop, as it "comes up" had 2 problems. I have asked about this multiple times, and don't find a solution.

When the desktop is loaded, the cursor never turns into an arrow, it continues, indefinitely as round "loading" wheel (icon).

The top panel "cuts off" the applications as they run. The apps cannot be moved around the desktop, they are all locked "under" the panel, and the panel "cuts off" the top portion of whatever is there.

I hope that answers your question.

---

### Post by ukripper on 2009-12-08
> **Mark_in_Hollywood said:**
> Why? you ask . . .

After d/l the Karmic "Desktop Install" cd, I changed from ext3 to ext 4.

Upon Karmic install, the screen or desktop, as it "comes up" had 2 problems. I have asked about this multiple times, and don't find a solution.

When the desktop is loaded, the cursor never turns into an arrow, it continues, indefinitely as round "loading" wheel (icon).

The top panel "cuts off" the applications as they run. The apps cannot be moved around the desktop, they are all locked "under" the panel, and the panel "cuts off" the top portion of whatever is there.

I hope that answers your question.

Ok! As i have read your other post [http://ubuntuforums.org/showthread.php?p=8462855](http://ubuntuforums.org/showthread.php?p=8462855) where you don't want to solve Nvidia problem. I guess i have answered your query and now you can mark this thread as solved from thread tools. have fun!!

---

### Post by Mark_in_Hollywood on 2009-12-08
I am marking this as "solved", as it tells me whether I can uninstall an active driver. 

I did the uninstall, next I warm-booted. The same problem appeared. I selected "Normal" from Appearances and the OS went to the 'net, found the NVidia driver I had previously uninstalled, installed it, said to re-boot and select "Normal", again.

I did as it requested, on clicking "Normal" it did a search for drivers and after clicking "Keep Settings", the desktop is as before. Yet, every time I boot, I must go through all this again.

---

