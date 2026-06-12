---
title: "Reset grub cache during boot"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by J V on 2010-01-30
I had an embarrassing issue today...

I ran linux as a demo for someone, who plugged in a network cable while it was booting for the first time and because of this, the grub cache (or whatever it is that records it for faster boot) got f*cked up, and grub wouldn't boot. I had to boot a live disc and completely reinstall grub to get it to run.

I remember there is an option you can edit when running grub (by pressing e at the menu) that will tell it to "re-cache" the hardware settings and use them to boot instead... What was that option again? (Google turning up nothing...)

---

### Post by mcduck on 2010-01-30
I suppose you are talking about readahead, not Grub (since Grub is already loaded at that point, and doesn't have any cache).

Just add "profile" to the end of kernel options, let the system bot until all disk activity stops and then reboot.

(and no, that's not a cache either, and has nothing to do with hardware settings. It simply stores information about what files are accessed during startup and where those fles are located on your hard drive, so that those files can be read in most effective order instead of randomly searching for each fil at the time wen it's needed.)

---

### Post by J V on 2010-01-30
yes it "cahces" what it needs to load and you edit the settings in grub, thanks for the help :)

[SOLVED]

---

