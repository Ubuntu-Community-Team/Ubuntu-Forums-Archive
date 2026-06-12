---
title: "bad sector"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by pvplahing138 on 2009-12-16
i have one bad sector is this dangerous

[http://www.upload.ee/files/303913/Screenshot.png.html](http://www.upload.ee/files/303913/Screenshot.png.html)

---

### Post by gs777 on 2009-12-16
Same problem with me.although I checked the box "dont warn .....". I would like to know if thi s is really a problem

---

### Post by Paqman on 2009-12-16
Not if your disk correctly remaps them, no. I have 2 bad sectors on one of my drives. Give it a reboot and see if it switches that sector into the "reallocated sector" count.

Disks pick up bad sectors during normal use. The on-board electronics detects this and normally marks them out of use seamlessly.

---

### Post by pvplahing138 on 2009-12-16
> **Paqman said:**
> Not if your disk correctly remaps them, no. I have 2 bad sectors on one of my drives. Give it a reboot and see if it switches that sector into the "reallocated sector" count.
 
Disks pick up bad sectors during normal use. The on-board electronics detects this and normally marks them out of use seamlessly.
 
 
 
is this stuf dangerous??
if you have some bad sectors? on ur hardrive

---

### Post by cj13579 on 2009-12-16
I picked got a couple of bad sectors on my drive recently and didn't think anything of it. Needless to say my drive deteriorated pretty rapidly and I lost a lot of data. 

Based on the price of new drives I wouldn't risk it. Replace it as soon as you can to avoid what happened to me. They are dirt cheap on the net and if you don't want to loose any data I would certainly recommend this! I wish I had replaced mine straight away and in the future I plan on doing so!!

---

### Post by bodhi.zazen on 2009-12-16
> **cj13579 said:**
> I picked got a couple of bad sectors on my drive recently and didn't think anything of it. Needless to say my drive deteriorated pretty rapidly and I lost a lot of data. 

Based on the price of new drives I wouldn't risk it. Replace it as soon as you can to avoid what happened to me. They are dirt cheap on the net and if you don't want to loose any data I would certainly recommend this! I wish I had replaced mine straight away and in the future I plan on doing so!!

+1

It is not "dangerous", but it is a sign of wear and tear on your HD.

You should back up any data you do not wish to loos to an external source (flashdrive , cd / DVD) ASAP and be prepared for HD failure, hard to predict how long the HD will last, could be months , could be weeks.

---

### Post by cj13579 on 2009-12-16
> A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. ~ Archbishop Desmond Tutu, 1999

I like this!

---

### Post by pvplahing138 on 2009-12-17
> **cj13579 said:**
> I like this!

i think its ubuntu bug cause hd tune shows that my disk is healty
and it did not find any disc errors

[http://www.upload.ee/files/304836/fyea.bmp.html]("http://www.upload.ee/files/304836/fyea.bmp.html")

---

### Post by lotharmat on 2009-12-17
Keep an eye on the reallocated sector count.

If this figure Looks sensible - ie not 16524578654 but a more sensible figure like 40 or 200 etc and starts rising. is can be indicative of imminent HD failure.


Back up the data and RMA the HD if it is still in warranty

---

### Post by pvplahing138 on 2009-12-17
> **lotharmat said:**
> Keep an eye on the reallocated sector count.

If this figure Looks sensible - ie not 16524578654 but a more sensible figure like 40 or 200 etc and starts rising. is can be indicative of imminent HD failure.


Back up the data and RMA the HD if it is still in warranty

but mine relocarted sector count is normal right?

---

### Post by Paqman on 2009-12-17
> **pvplahing138 said:**
> but mine relocarted sector count is normal right?

You currently have no reallocated sectors, but you have one pending. Normally the drive will reallocate a bad sector itself, so it's not great.

In your case, the fact that you've also got a fault under the "Ultra DMA CRC error" count shows that the actual problem could be a faulty cable, rather than an actual bad sector.

Try swapping the drive to a different cable and see if the fault transfers or vanishes.

---

### Post by pvplahing138 on 2009-12-17
> **Paqman said:**
> You currently have no reallocated sectors, but you have one pending. Normally the drive will reallocate a bad sector itself, so it's not great.

In your case, the fact that you've also got a fault under the "Ultra DMA CRC error" count shows that the actual problem could be a faulty cable, rather than an actual bad sector.

Try swapping the drive to a different cable and see if the fault transfers or vanishes.

but is it dangerous to hd if u dont deal wiht it?

---

### Post by Grenage on 2009-12-17
Either way, bad sectors can be a one-off blip, or the beginning of the end.  As long as you keep backups, don't worry too much.

---

### Post by Paqman on 2009-12-17
> **pvplahing138 said:**
> but is it dangerous to hd if u dont deal wiht it?

If you have a faulty cable, it could cause corruption of your data.

---

### Post by pvplahing138 on 2009-12-17
i used HDD HEALTH program it says that i havwe 79% pc health and its good???

---

### Post by Paqman on 2009-12-17
> **pvplahing138 said:**
> i used HDD HEALTH program it says that i havwe 79% pc health and its good???

You don't need that tool. You've already got a good diagnosis of where the problem is from the SMART data.

Is this a laptop or desktop? Did you try my suggestion to see if the cable is faulty?

---

