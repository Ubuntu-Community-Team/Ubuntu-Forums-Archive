---
title: "Insane boot times, and laggy system after fresh install"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Maydie on 2010-11-20
Hi everyone,

After a fresh install and updates, my system is extremely laggy, and boot time is very long (nearly 10minutes). When I log on or out, I also have a very long wait time.

When I type in the terminal the buffer is refreshed every 3 or 4 typed characters so it makes it hard to use it.

If I play a movie, it's impossible to watch it because it freezes every second.

I have a decent computer with SSD and 6Go RAM on Intel i7 920. I installed Ubuntu 10.10 desktop 64bits.

Where should I start to look to get a clue about what's going on?

Thank you very much

---

### Post by Maydie on 2010-11-20
Any idea?

---

### Post by listerdl on 2010-11-20
Is it a dual boot?

---

### Post by Maydie on 2010-11-20
No, I only have Ubuntu, it's installed on my 64gb SSD on ext4 partition (I used the erase all disk option at the installation)

---

### Post by oldfred on 2010-11-20
Have you optimized settings for a typical SSD?

Herman has some suggestions at the end of this:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

Also for standard installs, not sure if SSD makes any difference or not:
BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS in not updated to latest revision
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Video issues - use f6 to set nomodeset or other options or f4
Various hardware issues - bad cables, loose cables,

---

### Post by Maydie on 2010-11-20
Going to check everything you suggested, thank you

---

