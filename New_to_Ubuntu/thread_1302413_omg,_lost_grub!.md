---
title: "omg, lost grub!"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by vikramaditya on 2009-10-27
So, here's the deal.  I dual boot 8.04 with XP.  The OS's are on 2 separate internal drives, with Grub having been written to XP's MBR.  2 nights ago, I got into Hardy and installed updates, including the latest kernel.  After the required reboot, I used Synaptic to uninstall the previous "backup" kernel, leaving only the newest version and its predecessor intact.  I Rebooted again and Grub had faithfully updated itself to reflect the current state of affairs.  So far, so good.

I launched Synaptic again, wanting to check if any old headers were still installed.  Lo and behold, there was one of the very earliest ones in there, so I removed it in a tidy fashion.  Next, I used my custom "Orphans" filter in Synaptic to remove 2 items presumably left over from the old kernel wipe.  Finally, I opened Terminal and did the time-honored "sudo apt-get autoclean" thingy.  No idea what got cleaned up, but it wasn't much.  I like to run a tight ship!  Anyway, I then shut down and secured the hatches.

Long story short, Grub ist now kaput!  When I power up, the PC boots right into XP, with no hint that Hardy ever existed.  I've tried Auto Super Grub Disk to no avail and also tried booting from the Hardy Live CD to restore Grub from a terminal, as outlined in one of the many helpful tutorials I Googled up.  I don't want to wreck anything else, so I'm wondering if any of you fine forum folks might point me towards a safe and reliable method to restore Grub.

---

### Post by revanb on 2009-10-27
Hi

Sounds like your /boot/grub/menu.lst might be messed up...Check it, it has an option where you set the default option by number to boot and the time to wait before taking the default route. When you deleted some of the kernels the arrangement changed and the default is probably pointing to XP. the first os is number 0 and you count from there.

Good luck!

By the way, you can boot from your ubuntu live CD and then access the above mentioned file.

P.S. For anyone else reading this. This is not relevant if you clean installed Ubuntu 9.10 because it uses Grub 2 which works a bit different.

---

