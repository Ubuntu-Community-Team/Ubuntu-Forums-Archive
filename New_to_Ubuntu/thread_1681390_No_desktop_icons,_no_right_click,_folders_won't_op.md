---
title: "No desktop icons, no right click, folders won't open"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by ArchaeopteryxAlex on 2011-02-04
I am new to Ubuntu so I am asking for a little help

I turned on the computer this afternoon and it asked for a disk check. I waited and it said it found an error and I waited why it said it was searching for /tmp/ (it said that /tmp/ was unready). After nothing happened for a while it restarted. But when it was fully loaded I noticed my wallpaper was now just a black screen. So I tried to get to my folder with the wallpaper in but it wouldn't open saying,
Could not open location 'file:///home/alex/Pictures' 
No application is registered as handling this file
Then I noticed the few things I had saved on my desktop were missing. I tried to click around when I noticed right click wasn't working. So I searched through other forums and most said it was something to do with nautilus and that it should restart it but none really said how. I also tried other methods which they said would work but, for me, none of them did. Can someone help please

---

### Post by coffeecat on 2011-02-04
Welcome to the forum. :)

From the error message you saw, it's likely that you have filesystem damage on your Ubuntu root partition and that the bootup filesystem check did not complete. This could explain all the other problems you are experiencing. Did you have an unclean shutdown before all this happened?

I suggest the first thing to do is to check (and hopefully repair) the filesystem again. The easiest way is to boot up the Ubuntu live CD. When you get to the choice between try Ubuntu and install, choose try Ubuntu which will take you to the live desktop session. Now open System > Administration > Gparted. It will show you all your partitions on your hard drive. Your Ubuntu root partition will be the one listed as Filesystem ext4. If there is only one, that will be the one to check. If more than one, you might as well check them all. In passing - did you specify a separate home and/or boot partition when you installed?

Right-click on the partition to check and click on 'Check'. Now click on the Apply button - the green tick in the toolbar. Repeat for any other ext4 partitions you may have. Did the check complete without any error messages, or did you get some significant feedback?

Now try to reboot. Does that solve anything?

---

### Post by ArchaeopteryxAlex on 2011-02-04
I tried that and the scan said it finished and it all looked fine so I rebooted but everything remained the same - still a problem

---

### Post by ArchaeopteryxAlex on 2011-02-05
Also, when I try and update the system is says it can't update and is says I should check my internet connection, while at the same time I am surfing the web

---

### Post by odysseusjak on 2011-02-05
Do you have a lot of data stored on your drive? Do you have it backed up? It might be a lot easier to just reinstall Ubuntu.

---

### Post by coffeecat on 2011-02-05
> **odysseusjak said:**
> It might be a lot easier to just reinstall Ubuntu.

I have to agree with this. You have a number of serious issues that don't seem to have any relationship - except perhaps  filesystem corruption originally. This seems to have been repaired, but some system files themselves may have become damaged. You could spend hours tracking down each problem and trying to fix it.

---

