---
title: "[SOLVED] ? use the old Thunderbird profiles / Firefox bookmarks from the Vista/Window"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by ThailandTom on 2008-12-05
How do I use the old Thunderbird profiles / Firefox bookmarks from the Vista/Windows environment in the new Ubuntu environment?

**Background:**
Pretty standard story… Having a firm belief in open source, I have been using Firefox, Open Office and Thunderbird to do my work on a Vista platform. Vista, while nice in some respects, was a bit of an underperformer. Probably, the hardware was barely Vista compliant.

So, the machine poops out on me. "Cannot find boot menu." OK. Probably b/c dual boot corrupted grub? Tried HP recovery and backup discs, but nothing. Life goes on.

Having Dual-booted Ubuntu before, I had the USB stick set up, did a demo install, mounted the vista partition, copied all my files, and saved the data. Whew. Slight panic attack avoided.

 (I had backed up T'bird and Firefox and OpOff docs the session before the crash! So the panic was minor – critical stuff was safe. This is a plug for best practices. Smart computing rocks – back up essentials regularly and be happy! How many day's work can you lose? Backup, please!)
[B]
The issue:[/B]

How do I use the old Thunderbird profiles from the Vista/Windows environment in the new Ubuntu environment?

 
Had backed up Vista T'bird and Firefox with MozBackUp, so I unpacked the profiles on a friend's XP, got both programs running with all my data. Then copied the profile files onto USB stick, (learned to force mount) then copied again onto my big old wonderful Ubuntu drive.

 
*Have tried to import in Thunderbird. No option – import seems to be for other apps.

 **Have tried to copy bits of the profiles to the Ubuntu profile. Permission conflict. Nope.

So, opened file manager as root, (and copied here and there in T'bird. Nope –

*** deleted new profile, copied over old profile changing permissions. Also deleted other folder under T'bird (prefs?)


**** tried this:

[http://www.seoras.com/2008/05/28/how-to-transfer-thunderbird-profile-from-windows-to-ubuntu-804/Stuck](http://www.seoras.com/2008/05/28/how-to-transfer-thunderbird-profile-from-windows-to-ubuntu-804/Stuck).

AM using this in terminal: to copy, circumvent permissions

gksudo nautilus


Am delighted to be on the Ubuntu (8.04) path. Loving the terminal. Learning is good. The crash was the nudge to get me to jump. It has been all good, even when I bonked on the first couple installs through impatience. Am becoming skilled! (or not so - total newbie)

Hook me up, my Ubuntu tribe. Thanks.:p

---

### Post by nhasian on 2008-12-05
not sure about thunderbird but i imagine its similar... but with Firefox just copy over the bookmarks.html and you'll have all your old bookmarks.

---

### Post by 73ckn797 on 2008-12-05
This applies to Thunderbird:

[http://ubuntuforums.org/showthread.php?t=969448](http://ubuntuforums.org/showthread.php?t=969448)

---

### Post by ThailandTom on 2008-12-11
Solved my problem after searching the threads.

Ubuntu is easier than I thought. Don't over complicate things.

Was copying files to root directory instead of user directory.

Again... open your user account....
View .... show hidden

Copy Firefox bookmarks html into mozilla Firefox folder - same location
(had to restore bookmarks to pre-install date from migration.)
Copy Thunderbird files into mozilla Thunderbird folder - same locations.

Everything working perfectly. No need for permissions stuff on root folders.

Thank you, community!

---

