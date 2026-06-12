---
title: "Won't boot"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by DarkAz on 2009-02-08
I warn you all in advance, this is probably the biggest mess anyone ever did in Ubuntu for this specific situation.

After 3 days of trying (to no avail) to get my new Sound Blaster X-Fi Platinum working in Ubuntu (and in the process setting up OSS4), I was left with a soundless computer, except for VLC and MPlayer. So I decide to undo everything and just use the card on Windows.

The problem begins with the "undo" part. Well I decided to uninstall OSS4, and just to be sure reinstalled the alsa package. I noticed an alsa-oss version, so I installed that one too, as a last atempt. Finally I went to the sound config and changed all of the options to alsa (they were previously so, and I changed them to OSS in the middle of my adventures).

As I am restarting the PC, it takes a very long time loading the drivers, and when it reaches the point where the screen would flash and (in my case) show the Nvidia logo it stays there.

Thanks to Grub I tried the safe mode, still took a while but loaded and used startx to, well, start X. New user, alsa works, everything works. Rebooted again, no go.

Can anyone give me any tips or pointers? I'm using 8.04 ATM, and I can format it, but would much rather have an alternative. Thanks in advance to all who reply.

---

### Post by DarkAz on 2009-02-08
Little bump as a last hope?

---

