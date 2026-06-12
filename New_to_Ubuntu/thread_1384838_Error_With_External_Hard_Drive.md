---
title: "Error With External Hard Drive"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by Phantomhive on 2010-01-18
So, stupid me decides to partition my external hard-drive. I didn't even realize I had partitioned it either until I unplugged it (USB) and Ubuntu was like, lolwat? and then my computer would just show an error with GRUB unless the external hard-drive was plugged in. I figured I'd just reinstall everything; I reformatted and put Windows back on today.

Now, I copied all the needed files from my external hard drive to my desktop so I'm ready to delete everything on it and reformat it, but for some reason it only reformats as 294GB even though it's a 500GB hard drive. My guess is that Ubuntu is still on there but I just can't see it. Any ideas how to restore it to it's 500GB status? =X

I haven't attempted to put Ubuntu on yet and am currently in Windows 7.

---

### Post by presence1960 on 2010-01-18
I need a whole lot more info. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

