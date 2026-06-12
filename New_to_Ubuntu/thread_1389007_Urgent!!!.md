---
title: "Urgent!!!"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-01-23
i have installed karmic on a seperate partition to windows, and now wanna remove it, as its a Sims computer, and ubuntu and sims dont get along. if i remove ubuntu, will windows still boot because of grub being the bootloader

---

### Post by audiomick on 2010-01-23
You will have to repair the MBR. I think you need the Windows install CD for this. I haven't done it, so I am not too sure how it works.

---

### Post by lisati on 2010-01-23
> **audiomick said:**
> You will have to repair the MBR. I think you need the Windows install CD for this. I haven't done it, so I am not too sure how it works.

Sounds right to me.
The partition manager on an Ubuntu LiveCD can be used to delete the Ubuntu partition and resize the Windows partition to use the freed up space, and a Windows CD used to run something like fixmbr.

---

### Post by Merk42 on 2010-01-23
As said you will need to fix the MBR (Master Boot Record) for Windows with the Windows CD.  As for Sims and Ubuntu not getting along, you do know about [WINE](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732) right?

---

### Post by JamesParnell on 2010-01-23
i have the CD (somewhere).

should i remove Kk before i repair the MBR or after? or does it not  matter?

---

### Post by JamesParnell on 2010-01-23
> **Merk42 said:**
> As said you will need to fix the MBR (Master Boot Record) for Windows with the Windows CD.  As for Sims and Ubuntu not getting along, you do know about [WINE]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732") right?

Yes i do, but i'm running [The Sims2 ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942");)

---

### Post by audiomick on 2010-01-23
> **JamesParnell said:**
> i have the CD (somewhere).

should i remove Kk before i repair the MBR or after? or does it not  matter?

remove then repair, I think.
I would give up the sims before I gave up Ubuntu :)

---

### Post by lisati on 2010-01-23
> **audiomick said:**
> remove then repair, I think.
I would give up the sims before I gave up Ubuntu :)

+1 I have a copy of the original Sims somewhere, haven't used it for some time.

---

### Post by marshmallow1304 on 2010-01-23
> **JamesParnell said:**
> Yes i do, but i'm running [The Sims2 ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942");)

If you're dual-booting, why can't you run the game in Windows?

---

### Post by JamesParnell on 2010-01-23
> **marshmallow1304 said:**
> If you're dual-booting, why can't you run the game in Windows? i can, but i never use ubuntu on my desktop rig as i only have an 80gb HDD and all the parts are abour 6 years old lol.

so im gunna remove it. 

i've done it now, i think, i tried to "fixmbr" but it killed my computer each time, then i finally went into setup and repaired the installation, the tried to fixmbr again and it worked. now to see if the thing will boot (running a chkdsk now, just to make sure its oK)

---

### Post by JamesParnell on 2010-01-23
great help guys, thanks a lot.

---

### Post by JamesParnell on 2010-01-23
is it meant to go to the setup screen? you know, the "setup will complete in approx." screen?

---

### Post by luffy_chan_19 on 2010-01-23
yes they are all right all you basicaly have to do is remove ubuntu and then repair the master boot record, i beleive you have to do this by using an ERD, but the best way to do it is just to use the windows instalation disk. there should be an option that allows you to recover the MBR. i know with xp there is an option to recover NTloader. i am not sure with vista though. i am assuming that it is still the same. oh and i agree with a previos poster i would give up the sims before giving up ubuntu, its not that great of a game anymore.

---

