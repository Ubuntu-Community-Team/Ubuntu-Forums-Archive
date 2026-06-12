---
title: "Very Simple CD Question"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Planetes on 2010-08-17
I have an old age of empires disc and i was wondering how to copy it and if copying it would ruin the disc.

Thanks.

Also i was planning on using brasero 1:1 copy but it said the process was unavailable.

---

### Post by linux18 on 2010-08-17
dd if=your_cd of=your_iso bs=4M

---

### Post by Planetes on 2010-08-17
Concise.

Thanks I'll give 'er a shot

---

### Post by Planetes on 2010-08-17
Did not work for me. Here is what i got.

```

if=/media/AOE2 of=AgeofEmpires.iso bs=4M
dd: reading `/media/AOE2': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000204519 s, 0.0 kB/s

```

---

### Post by linux18 on 2010-08-17
dd if=/dev/cdrom of=your_iso bs=2048 conv=sync

if only I thought of it first, it would have been concise and accurate

---

### Post by Planetes on 2010-08-17
Okay, The line worked without flaw but when i burn the iso to disc it doesn't play as a game or autoplay.
I'm trying to use it on windows by the way.

---

### Post by Planetes on 2010-08-18
I feel like i'm missing something fundemental here. I'm just trying to make a copy of this game.

---

