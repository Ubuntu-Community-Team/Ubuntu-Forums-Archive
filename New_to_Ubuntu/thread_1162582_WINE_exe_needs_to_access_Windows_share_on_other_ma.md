---
title: "WINE exe needs to access Windows share on other machine"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by JaimeZX on 2009-05-17
How do I accomplish this? I can access my Windows share from the file managers, etc, but if I need to find the same Win directory through a (click-only Explorer window) I can't because I only see C:\ and U:\. I could make a "shortcut" to the Windows share and put it in the WINE C:\ directory, but Ubuntu won't let me do that for some reason; possibly because it's a network folder?

Help!

Thanks!

:) Jim

---

### Post by MontelEdwards on 2009-05-21
No, that is because WINE does not have Samba support.
IIRC

---

