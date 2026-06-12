---
title: "Ext 4 or what for server extra space"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-28
Dear Forum,

I'm confused by the differing views of ext4 here in the forum and in google.

I've got a Karmic server with not enough space and an unused, empty 1TB drive lying around so I plan to solve the problem by installing and mounting the drive from within my home drive.

I guess there is no need for anything other than a single partition. The question is which one ext2, 3 or 4?

Reliability of not loosing the data is most important criteria speed improvements not bad but I can't see any point in exceeding the speed of the computer's network connection.

Thanks in advance,


Richard

---

### Post by mbzn on 2009-11-28
I have never had a problem with any of these (yet), i'm using ext4 with Ubuntu9.04. i believe the difference is in tweeking, which I find unnecessary at this stage.

---

### Post by Findarato on 2009-11-28
I haven't tried it on one of my servers yet, but on my desktop and laptop I have switched to EXT4, which gave me a major performance leap.

Especially on my laptop it was like I bought a new computer somehow. In terms of stability, I am a little unsure. After installing Ubuntu 9.10 on my laptop, it said my HD was screwed up. I am not sure if it wasn't before, but I AM sure that ubuntu 9.04 didn't tell me, so I have the impression the drive got screwed up by the installation somehow. 

If you are really looking for stability (production server) I guess you could wait a bit with EXT4. If it's a "fun server", I think EXT4 is stable enough.

---

### Post by XCan on 2009-11-28
> **Findarato said:**
> 
If you are really looking for stability (production server) I guess you could wait a bit with EXT4. If it's a "fun server", I think EXT4 is stable enough.

I tend to agree. For my workstation I have decided to stay with ext4 when going Karmic. But for Lucid, I will most likely switch to ext4 if it still is the default filesystem, due to the LTS labeling which makes me feels safer.

---

### Post by RichardCL on 2009-11-30
> **Findarato said:**
> If you are really looking for stability (production server) I guess you could wait a bit with EXT4. If it's a "fun server", I think EXT4 is stable enough.

That sounds plausible, many thanks for all the answers.

The data is pretty critical for my job so I've decided to install the OS (Karmic) with ext4 but keep the data on a separate drive running ext3.

I don't backup my desktop usually but send important data to the server and keep that backed-up. That allows me to store my data on the road with file transfer over SSH. There is usually up to two weeks worth of work on the server that isn't backed up.

I'll probably switch to ext4 in a while but for now I need to be sure.

---

