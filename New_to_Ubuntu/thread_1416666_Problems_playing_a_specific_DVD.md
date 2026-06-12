---
title: "Problems playing a specific DVD"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-02-26
Hi, I'm trying to play a DVD in ubuntu, I have libdvdread4 and libdvdcss2 installed. When trying to play this particular dvd, Movie Player closes as soon as I try to play it. So I tried vlc, it opens, won't play, and I have to use killall -9 vlc to close it. So I tried vlc --verbose 2 which kept giving off these errors until I used killall in a separate terminal:

```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1601 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1597 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1599 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1601 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1597 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***

```

Anyone have any ideas?

---

### Post by doas777 on 2010-02-26
I'd try ripping it up front, and see if you still get the same errors when you try to play off iso or vob.

some disks use non-compliant CSS, or the disk itself may be damaged at a critical sector. with luck a rip may bypass either of those issues.

---

### Post by Ozymandias_117 on 2010-02-26
Wouldn't the CSS be copied into the ISO? Why does it work from an ISO but not the disc then?

---

### Post by Sef on 2010-02-26
I would say that it is encoded with a encryption that cannot be read.

---

### Post by Mark Phelps on 2010-02-26
You didn't indicate what type of DVD (movie, data) but some Movie  DVDs are protected in such a way that they can't be read by DVD devices in PCs; instead, they can only be read by consumer DVD players.

---

### Post by Ozymandias_117 on 2010-02-26
Putting it as an ISO made it playable, I was just wondering, Why does this work?

---

### Post by doas777 on 2010-02-26
> **Ozymandias_117 said:**
> Putting it as an ISO made it playable, I was just wondering, Why does this work?

ripping a DVD either offline or on the fly involves decrypting the stream. with iso-writes, the decrypted version is what is written to the file.

I should have mentioned this before, but I'm sure you are in a country like canada where css circumvention is legal.

---

