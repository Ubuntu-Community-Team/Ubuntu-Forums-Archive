---
title: "Tar / bzip2 Speed"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by jv2112 on 2010-01-02
"tar jcpvf destination  source --totals" is moving at .37 GB  Per Minute .

Source & Destination are on two separate hard drives.

I am backing up 600 gig so I want to make sure this sounds good.


Does this sound correct ? :confused:

---

### Post by starcraft.man on 2010-01-02
Speed depends on quite a few factors, the HDD types (read/write speeds), your CPU (ability to perform compression), the connector types (IDE slower than sata), the kind of files being compressed (text will compress much better than video), lastly the algorithm (gzip is much faster, less compression).

So, I don't know, I'm pretty sure it goes faster on my system, but it's a bit of a beast compared to most folks.

---

### Post by jv2112 on 2010-01-02
Mixture of media (avi,MP4,MP3) Text , Excel Files from the Seagate to the Samsung.

I wanted more compression so I selected Bzip.

Thoughts ? :confused:

System->

AMD| X2 245  2.9 :Regor / 235*14.5=3408
CPU COOLER ZALMAN|9700
MB GIGABYTE GA-MA770-UD3 AM2+ (Revision 2)
OCZ ModXStream Pro OCZ700MXSP 700W
G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) 
SAMSUNG Spinpoint F1 HD753LJ 750GB 7200 RPM 32MB Cache 
Seagate Barracuda ST31500341AS  SATA 3Gb/s  1.5TB
EVGA GeForce 9800GT SSC
NEC ND-3550A / DVD+ /-RW 16X / SAMSUNG DVD Burner : SH-S203B 
Sunbeam Freezing-Storm IC-FS-BK Black

---

### Post by starcraft.man on 2010-01-02
One thing I'll tell ya right up front is that attempting to compress media files like AVI/mp3/mp4 and what not is usually futile. The reason is that during encoding the algorithms used to originally compress the source from raw video/audio is usually pretty good, and it's unlikely that bzip can get any more out of it. So bzip will struggle and try it's best but ultimately I don't think it's worth it. If you exclude such files from the compression you'll see it take less time.

Text, pictures, spreadsheets and such do gain from compression and archiving.

It's up to you. Also, see my sig, I wrote a well explained backup section.

---

