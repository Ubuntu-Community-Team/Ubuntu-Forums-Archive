---
title: "uninstall and reinstall"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-09-03
girlfriend is currently dual booting vista and ubuntu, She wants to remove and then reinstall ubuntu without destroying her vista partition. How should she go about doing that?

---

### Post by k33bz on 2009-09-03
> **LunaticHiatus said:**
> girlfriend is currently dual booting vista and ubuntu, She wants to remove and then reinstall ubuntu without destroying her vista partition. How should she go about doing that?

She already has Ubuntu and Vista on her computer?

---

### Post by Geoff918 on 2009-09-03
Which has authority, GRUB or Windows boot system? I would assume GRUB, but it helps to be sure.

---

### Post by drs305 on 2009-09-03
Write down the / and /swap partition designations (e.g. sda5, sda6).
Use a LiveCD, select install.
In Step 4, select manual partitioning.
Designate the / partition and the /swap partition.
In each case, make sure to tick the 'format' option to overwrite the existing data.

Added: Note that none of her configurations will be retained by this method unless she is using a separate /home partition, designates it during installation, and makes sure it is NOT formatted.

---

### Post by LunaticHiatus on 2009-09-03
yes, She has ubuntu and vista dualbooted already on her computer. She was having some issues with ubuntu while fiddling around and figured it would be easier just to reinstall everything then figure out what she did.

---

### Post by LunaticHiatus on 2009-09-03
yeah, she is using grub.

---

### Post by LunaticHiatus on 2009-09-03
any other solutions that might be less risky then playing around with partitions?

---

### Post by drs305 on 2009-09-03
> **LunaticHiatus said:**
> any other solutions that might be less risky then playing around with partitions?

Your Ubuntu options:
1. Leave things as they are.
2. Attempt to fix the things that are broken.
3. Upgrade to a newer release in hopes it will fix things (not yet to Karmic, which is still Alpha).
4. Move /home and reinstall /. Will preserve most of her configuration settings.
5. Reinstall everything, reformatting partitions.

---

