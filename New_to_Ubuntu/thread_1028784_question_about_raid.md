---
title: "question about raid"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by pshootr on 2009-01-02
I have an old socket 370 Abit-bp6 which is SMP capable, and has a raid controller. I would like to tranfer my server over t it. Question is When I try to format the dives and build the array, should this be done while the drives are plugged in to the IDE channel or should they be plugged in to the raid controller channel?

EDIT: The raid controller is highpoint 366

---

### Post by blueridgedog on 2009-01-02
I had a bp6 that I setup as a server.  I ended up having a boot disk oni the ide controller and other disks on the raid controller.  The drives (number depending on the raid level you opt for) will need to be plugged into the raid controller prior to formating, as they will be formated not as individual drives, but as the volume (or volumes) exposed by the raid controller.

---

### Post by pshootr on 2009-01-02
> **blueridgedog said:**
> I had a bp6 that I setup as a server.  I ended up having a boot disk oni the ide controller and other disks on the raid controller.  The drives (number depending on the raid level you opt for) will need to be plugged into the raid controller prior to formating, as they will be formated not as individual drives, but as the volume (or volumes) exposed by the raid controller.

Ok thanks. Only problem is I just hooked up the board on the bench today and I get no post, just long beeps. I unplugged the keyboard and it booted. But then I switched the ram chip for a bigger one, then got nothing but long beeps again. So I put back the original ram chip and long beeps still. Now no matter what is plugged or unplugged I get nothing but long beeps.

---

### Post by blueridgedog on 2009-01-02
Well, keep trying to debug it...it was a good board.

---

