---
title: "Boot and video Problems"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by Kedster on 2011-08-31
I got a new laptop recently, and set up a dual boot. It had been years since I had windows but I figured id give it a try. anyways, the problem I think stems from the video card.

The issue is that it boots grub then begins to actually boot ubuntu. Either it sits on a purple screen or it shows the white cursor and then goes to a black screen. Most times as if the screen were off but sometimes the back light it on.

Sometimes when I hit ctrl+alt+f1 I get the verbose output or what ever, but lots of times nothing happens. 

The output on the screen either reads one of two things (these are not precise, only from memory, but will try to get better later)

```
starting trace....
A bunch of stuff about drivers ending in radeon
code 00 00 41 8b  24 e4 0a 00 85 f6 0f 8e 03 00 00 41....
RIP <fffffffffa0418c86> evergreen_cp_start
RSP <fff8801d1f8faf8>
CR2 ffffc90412081ffc
---[ end trace c4a6ae06f14e478a ]---
end trace 
```

OR
```
BAD LUM
Bad target line 1 
Bad target line 2 
and so one
```

---

