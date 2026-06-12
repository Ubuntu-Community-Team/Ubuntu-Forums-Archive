---
title: "Reboot &amp; GRUB problem"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by klossor on 2011-01-20
During system reboot, on Ubuntu nb 10.10, I'm getting a system stop error.

"Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

Also during boot, upon hitting the GRUB menu I'm receiving duplicate entries, 2 identical Ubuntu listings, and 2 identical Ubuntu recovery listings. ( Mem test options unaffected ). Upon attempting to boot from the first entry the above error halts boot. If however the second identical Ubuntu listing is chosen bootup proceeds normally.

Any Ubuntu/Linux guru's out there that could shed some light on this? Thanks in advance for any info

Klossor

---

### Post by drs305 on 2011-01-20
Are the two entries exactly the same, or is there a difference in the last number (such as -23 vs -24)? There can be multiple kernels that appear the same except for the last two digits in the name. One kernel may work while the other one doesn't. Typically the older kernel works (since if it didn't you would not have kept it).

In any case, select the one that boots. Once you get into your OS, open a terminal (Applications, Accessories, Terminal) and run the following command:

```
sudo update-grub
```
That's the simplest solution and may fix your machine. If not, please go to the following site, download the boot info script, and then post the contents of the RESULTS.txt file it generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by klossor on 2011-01-20
Ah, my lack of linux knowledge (and apparently the ability to read lol) is showing. The two entries aren't actually identical upon closer inspection, as you said there are two kernel versions listed (the newer 2.6.35-24, and the older 2.6.35-22). The older kernel is the bootable one.

I booted in through GRUB using kernel 2.6.35-22. As you suggested i ran grub-update, and its solved the issue for me, for now anyway ;)

Thanks for the help, and for the speedy reply friend.

---

### Post by TechWiz2100 on 2011-01-20
I think the devs who make the kernel updates need to fix their packages because this seems to be a common problem with 2.6.35-24

---

