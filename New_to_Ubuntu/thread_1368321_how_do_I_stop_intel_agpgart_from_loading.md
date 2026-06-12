---
title: "how do I stop intel_agpgart from loading?"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by stoked acid city on 2009-12-30
I've tried to blacklist it in /etc/modprobe.d and edit my modules file to stop it, but it's still loading at boot (at least some of the time).

I've got an acer aspire, and most of the time it hangs at boot. I'm dual booting 9.10 w/ xp, and when I choose ubuntu in grub, four times out of five it goes to a blinking cursor but no further. XP boots fine every time

I found a bug on launchpad that seems related, and and there these intel_agpgart drivers are the problem. When I boot in recovery mode, if it hangs, it hangs right after it loads them. Also, when the ubuntu logo does show up, it looks fuzzy, which also makes me think it's a graphic driver problem. BTW, I had the same problem with vanilla ubuntu

So, please, help! This is driving me crazy

---

### Post by stoked acid city on 2009-12-31
Anyone? If I could disable agp totally that would work for me.

I've tried to blacklist it in modprobe.d/blacklist.conf and i've tried putting "set agp=off" in grub.conf, but intel-agpgart still loads

---

