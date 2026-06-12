---
title: "What is maximum ram?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by strangepork on 2009-06-29
Assuming the mother board can handle it, whats the max ram i can use in 9.04 amd64 ubuntu please?  what about 9.04 x86?

thanks!

---

### Post by shifty_powers on 2009-06-29
in 64-bit far more than you'll ever be able to fit in the near future. in 32-bit then you can fit as much as you please, but there is an address limit of about 3.5gig.

---

### Post by paul_be on 2009-06-29
this may answer:
[http://ubuntuforums.org/archive/index.php/t-1128488.html](http://ubuntuforums.org/archive/index.php/t-1128488.html)

---

### Post by starcraft.man on 2009-06-29
> The emergence of the 64-bit architecture effectively increases the memory ceiling to 264 addresses, equivalent to approximately 17.2 billion gigabytes, 16.8 million terabytes, or 16 exabytes of RAM. To put this in perspective, in the days when 4 MB of main memory was commonplace, the maximum memory ceiling of 232 addresses was about 1,000 times larger than typical memory configurations. Today, when over 2 GB of main memory is common, the ceiling of 264 addresses is about ten trillion times larger, i.e., ten billion times more headroom than the 232 case.

[Wikipedia.]("http://en.wikipedia.org/wiki/64-bit")

I don't think you ever need worry in the short term about hitting the 64 bit wall.

---

### Post by nmaster on 2009-06-29
i was beaten to it.

---

### Post by ELD on 2009-06-29
It just a pity about 64bit support from a lot of things.

---

### Post by RD1 on 2009-06-29
> 640K ought to be enough for anybody.
Bill Gates  :lolflag:

---

### Post by lykwydchykyn on 2009-06-29
If you install the server kernel, you can use up to 64 GB in 32 bit (x86) Ubuntu.  That's what I do, I had too many compatibility issues with 64 bit.

---

### Post by strangepork on 2009-06-29
good to know.  the google i found for 6.06 said it was capped at 8gigs, even for 64bit, which boggled me!

---

### Post by Sef on 2009-06-29
> It just a pity about 64bit support from a lot of things.


With GNU/Linux, almost all programs havea 64-bit equivalent.

---

### Post by ELD on 2009-06-30
> **Sef said:**
> With GNU/Linux, almost all programs havea 64-bit equivalent.

True for a lot of things. I will eventually use 64bit Ubuntu when i get 4GB ram.

---

### Post by lisati on 2009-06-30
> **ELD said:**
> True for a lot of things. I will eventually use 64bit Ubuntu when i get 4GB ram.

Why wait? I'm using 64-bit with 2Gb RAM

---

### Post by magh-87 on 2009-06-30
> **lisati said:**
> Why wait? I'm using 64-bit with 2Gb RAM

Perhaps I should do the same then.. I'm using 32bit with 2gb of ram on my old pc which now hosts ubuntu on it.. I'm curious about what sort of improvements that I could see in it as a system though. Additionally, I'm also considering turning that computer into a server for external network uses (primarily: hosting friends sites, etc)

---

### Post by mcduck on 2009-06-30
> **magh-87 said:**
> Perhaps I should do the same then.. I'm using 32bit with 2gb of ram on my old pc which now hosts ubuntu on it.. I'm curious about what sort of improvements that I could see in it as a system though. Additionally, I'm also considering turning that computer into a server for external network uses (primarily: hosting friends sites, etc)
Most common situations where 64-bit system increases performance would be media-related tasks, like audio and video encoding/processing, 3D-rendering and image processing.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks]("http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks")

---

### Post by scorp123 on 2009-06-30
> **lykwydchykyn said:**
> If you install the server kernel, you can use up to 64 GB in 32 bit (x86) Ubuntu.  That's what I do, I had too many compatibility issues with 64 bit. Bingo. Same thing here. I use the "linux-server" kernel package for 32-bit. And it "just works" whereas 64-bit was giving me too many headaches.

---

### Post by ELD on 2009-06-30
> **lisati said:**
> Why wait? I'm using 64-bit with 2Gb RAM

I wait because i have it setup how i like it :P, and don't want to change unless i really need to, which for now i don't. Although it may be worth trying anyway for when i do upgrade and then i can see if the lockups i get exist in the 64bit version too.

---

### Post by Paqman on 2009-06-30
> **strangepork said:**
> good to know.  the google i found for 6.06 said it was capped at 8gigs, even for 64bit, which boggled me!

Most mobos seem to be 8GB max, so in practical terms it usually is the case.

---

