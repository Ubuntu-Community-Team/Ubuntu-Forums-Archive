---
title: "How do I remove older version?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Alfx on 2009-01-12
Every time I upgrade unbuntu, the older version still shows up
on the boot loader.

Can anyone tell me **exactly** how to remove these?

Thanks a lot.

---

### Post by iaculallad on 2009-01-12
Linux Images? Navigate to System-Administration->Synaptic Package Manager and search for the "linux-image" string (w/o the double quote). You will be shown the complete list of installed images, try to right-click on an OLD image and select "Complete Removal". Click on "Apply" after choosing the images you want remove. This will automatically update your GRUB settings.

NOTE: You can leave a *single* previously working image just in case things won't work what you expected on your new installed image.

---

### Post by andrewc6l on 2009-01-12
You can edit /boot/grub/menu.lst and comment out the ones you don't want after the "## ## End Default Options" section. (You would comment out instances of the lines beginngin "title", "root", "kernel", "5-75...", "initrd" and possibly "quiet". I don't know if this will break the automatic updating, though - probably not, but it would be wise to keep a backup of the original menu.lst for safety.

Also note that if you get something wrong, you can make your system unbootable by doing this, so be cautious.

I just did a refresh: iaculallad's way is probably better :-)

---

