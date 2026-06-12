---
title: "Firmware updates for LITEON Atapi DVD A  DH20A3H"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by ricardisimo on 2010-02-28
The LITEON site has firmware updates [here]("http://us.liteonit.com/us/index.php?option=com_wrapper&Itemid=153"), but I have no clue how to implement them on Ubuntu.

The issue is that this optical drive of mine will not recognize Verbatim Lightscribe DVD+R DL discs. Apparently this is a problem for many people, and I have found threads to attest to this. Unfortunately, the solutions LITEON gives appear to be Windows-based.

Any help is appreciated. Thanks.

---

### Post by ricardisimo on 2010-03-02
Is it even possible for wine to run something like a firmware updating program? Would it make any difference if it were sudo wine?

---

### Post by Mark Phelps on 2010-03-03
> **ricardisimo said:**
> Is it even possible for wine to run something like a firmware updating program? Would it make any difference if it were sudo wine?

Depends on what the ZIP file expands into ...

When I've done firmware in the past, it required inserting a diskette to which it then wrote the firmware file.  The diskette had to be already formatted with the DOS boot files loaded.

While today, you more often update firmware from inside MS Windows by running a utility the hardware vendor provides, the risk you're running trying to do this in Wine is, if it fails, your drive will then be totally useless.

If you can find out the name of the utility program, you can check the WineHQ site application compabitility database for that program and see what ratings it has.  IF there are no ratings, or if it is listed as Bronze or Silver, I would not use it in Wine.

---

### Post by LowSky on 2010-03-03
> **Mark Phelps said:**
> 
While today, you more often update firmware from inside MS Windows by running a utility the hardware vendor provides, the risk you're running trying to do this in Wine is, if it fails, your drive will then be totally useless.
 

You can run into the same problem in Windows as well.

---

### Post by ricardisimo on 2010-03-03
> **LowSky said:**
> You can run into the same problem in Windows as well.

Does that mean that the older diskette system is safer, or that firmware updates are always risky, period?

---

### Post by LowSky on 2010-03-03
> **ricardisimo said:**
> Does that mean that the older diskette system is safer, or that firmware updates are always risky, period?

All firmware updates are risky. For instance if you loose power in the middle of the update, it could brick the drive., or if the disk has a problem or the creator messed up the code, or you accidentally cancel the operation mid-programing.

Firmware updates are something to be weighed out, For instance: What will the update offer me that I don't have now?
If the drive works fine for you now than updating it is a unnecessary risk.

Upgrading Ubuntu or Windows or any other software program has the same risk so don't think I'm trying to scare you. weigh out the benefits and go from there. personally I doubt you need it, as the firmware is from 2/24/09

---

### Post by Phrea on 2010-03-03
Pragmatic but maybe a solution: put the drive in a windows based machine, do the firmware upgrade and put it back into your own computer.

---

### Post by ricardisimo on 2010-03-04
Optical drives carry their own firmware? I would have thought the firmware would be somewhere in the regular system folders.

Well, it's a Lightscribe DVD RAM that won't read dual-layer LS DVDs at all, and apparently it is a firmware issue (at least as per the LITEON website and communications people have posted from them in various forums.) So, I have to decide if I want to keep the drive safe to burn other kinds of disks, or be able to use it on the stack of rather expensive Verbatim LS DL DVDs I just bought.

---

