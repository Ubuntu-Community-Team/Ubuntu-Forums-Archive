---
title: "cannot execute files on a different partition"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by gaston5 on 2010-10-13
i'm having trouble executing files. I have 2 partitions one with ext4 and another one with fat32. I used to be able to execute files in the last one(fat32) but since I upgraded to maverick, I can't.
When I moved the file to the ext4 partition and chmod +x file I could execute it, I know fat doesn't support metadata and permissions but I didn't have this problem before the upgrade. Any thoughts on this?

---

### Post by the_jlx on 2010-10-13
i have had similar issues but they went away...
Maybe lack of updates?
only problem i have now is the T#¤&/%()%(%%/()/#()(/&/&#( keyring not working right
or not exiting promt after password entry but the execute has been solved.
Check if the partition is owned by root if so change it to your ownership.
if i am of no help then reply /slap lol
Sincerely JLxsolutions
AKA Janne Lukkarinen

---

### Post by AndyM3 on 2010-10-13
Looks like the fat32 partition is mounted with the "noexec" option. Mind posting the contents of your /etc/fstab file? (type "gedit /etc/fstab" in a terminal to get them)

---

