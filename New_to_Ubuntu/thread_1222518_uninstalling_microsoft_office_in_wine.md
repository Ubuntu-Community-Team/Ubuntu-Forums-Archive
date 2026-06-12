---
title: "uninstalling microsoft office in wine"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by libihero on 2009-07-25
microsoft office in wine has been workin well for me, but i think i jacked somethin up in the powerpoint, and it's not workin for me anymore.  i wanna uninstall it but i can't figure out how.  i tried the "uninstall wine software" but that doesnt work

---

### Post by llamabr on 2009-07-25
i"m no wine expert, but navigate in the terminal to ~/.wine/ and rm the word directory.

---

### Post by libihero on 2009-07-25
rm?

---

### Post by llamabr on 2009-07-25
```
cd ~./wine
ls
```

find something that looks like microsoft windows.  And use the rm command to remove it.

---

### Post by Chronon on 2009-07-25
Or turn on viewing of hidden files in your file browser and do it from there.

---

### Post by Zero++ on 2009-07-25
> **libihero said:**
> rm?
RM is the terminal command for remove

---

### Post by Mark Phelps on 2009-07-25
Following long-standing tradition, MS doesn't seem to be able to leave well-enough alone, and by that I mean, MS Office 2007 is up to 2 SPs (or is it 3 now) -- and Wine is VERY SPECIFIC regarding the office app, the version and the SP that is supports.

Not all Office 2K7 produces work equally well in Wine, so there's every possibility that if you updated PP at all, the update now stops it from working.

I would suggest that you reinstall (or repair, if it will let you) the PP 2K7 installation.  That should get it working again by resetting it to the version you first installed.

---

### Post by libihero on 2009-07-25
i tried manually deleting it, but i think i made things worse....
i accidently removed the "programs" folder under wine in the applications tab

---

### Post by libihero on 2009-07-28
bump....
is there anyway to completely remove everything i downloaded with wine along with wine?  like have a totally fresh start with it?

---

