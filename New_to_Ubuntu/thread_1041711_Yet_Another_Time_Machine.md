---
title: "Yet Another Time Machine"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by bsharp on 2009-01-16
I have yatm installed to help learn some songs on guitar, but it won't play any files that I want (they are in .ogg format). I installed vorbis-tools but it gave the same error.

Here's the output:

```
brandon@brandon-desktop:~/Music/Wintersun/Wintersun$ yatm -t 0.9 08*
libsndfile: Supported file format but file is malformed.
Vorbis stream has 2 channels and 44100hz sampling rate.
*** glibc detected *** yatm: double free or corruption (!prev): 0x0000000000616c00 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fc90faf708a]
/lib/libc.so.6(cfree+0x8c)[0x7fc90fafac1c]
/lib/libc.so.6(fclose+0x14c)[0x7fc90fae5dac]
yatm[0x403617]
yatm[0x40472b]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7fc90faa11c4]
yatm(__gxx_personality_v0+0xf1)[0x4029d9]

```

---

