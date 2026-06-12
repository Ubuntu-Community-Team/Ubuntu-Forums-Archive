---
title: "Reloading the BIOS"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-12-25
So I'm dual booting XP and Ubuntu atm and I think I need to reload my BIOS ([http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66759](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66759)) to get my bluetooth working again. I'm just wondering if I should be aware of any problems or issues this may cause or that I may encounter because I'd rather not mess up my Ubuntu install.

-SMRT

---

### Post by glotz on 2008-12-25
Well, flashing the BIOS at least could potentially brick old mobos if something went wrong, like you lost power at the critical moment or used defective medium to fire up the update. Probably it will be quick and painless though.

You said 'again', that makes me very curious, have you done something to your BIOS to break bluetooth then or what?

---

### Post by I[AM]SMRT on 2008-12-25
I reformatted my hard drive (so I could dual boot :D) and that's when my bluetooth stopped working.

[http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&thread.id=8847](http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&thread.id=8847)

He more or less has the same problem as me and so I'd like to try reloading the BIOS.

---

### Post by ieee488 on 2008-12-25
I've reformatted my hard drive and re-installed Linux on my PC numerous times and I've never had to re-flash the BIOS. It isn't necessary.

---

### Post by I[AM]SMRT on 2008-12-25
I'm all ears to getting my bluetooth working again.

P.S. Merry christmas

---

### Post by logos34 on 2008-12-25
I see nothing in the Bios update changlog to indicate that it will solve your bluetooth problems.  You say 'working again'--if the bios was the culprit it probably would never have worked. dunno  

I don't see any problem, really, with updating the Bios (you create a bootable CD), but don't expect it to fix things.  The manufacturers always tell you not to update if the computer works (and yes, you could--remote possibility--pooch your mobo/machine like glotz says)

---

### Post by I[AM]SMRT on 2008-12-25
Well instead of reloading the BIOS, I just reset it to its default configuration and now my bluetooth works (yay!). However, it seems to have killed my windows install (boo!). I get bluescreened when it tries to load up windows.

:(

---

### Post by logos34 on 2008-12-25
what error code is present (if any) on the bsod?

---

### Post by I[AM]SMRT on 2008-12-25
I just get a flash of blue and then it automatically restarts.

EDIT: Similar problem here [http://www.sudhian.com/index.php?/forums/viewthread/101852/](http://www.sudhian.com/index.php?/forums/viewthread/101852/)

I may try repairing the windows installation.

---

### Post by logos34 on 2008-12-25
just a tip: next time before you change any setting in the Bios, make sure to save the current working settings so you revert back in case of trouble

---

### Post by I[AM]SMRT on 2008-12-25
Hehe, lucky I've got a decent memory. I recognized that the SATA option was changed from "Compatability" to "AHCI", so I changed it back and everything works great now (+bluetooth!).

Thanks for the help guys ;D.

---

### Post by logos34 on 2008-12-25
> **'I[AM]SMRT said:**
> I recognized that the SATA option was changed from "Compatability" to "AHCI", so I changed it back and everything works great now (+bluetooth!).

I was about to mention you check that--I must have posted on that subject a dozen times in the last few days.  becoming a common problem

---

