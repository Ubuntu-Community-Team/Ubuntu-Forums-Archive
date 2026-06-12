---
title: "[Wine] World of Warcraft"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Novnia on 2009-04-17
Is this possible? Im very new and just got interpid installed, was on feisty. After everyone was so helpful getting me on interpid i thought id try for wine. If i can get Civ 4 and WoW to work then my gaming fix will be sated.


I tried putting cds in, said it couldnt find installer, i looked around in wine and found it was on l:/media/cdrom0/installer.exe or similar and got it running, got to where it said insert CD 2 and i tried to eject it, didnt work said i didnt have permission

so i tried to go into su in terminal but it said authentication failed. i KNOW i used my root pasword though. not sure how to proceed. was gonna try to install wow on a windows pc and copy the dir over. would that work?

---

### Post by James_Lochhead on 2009-04-17
I have had no experience with it personally but I have heard people saying they play WoW on Linux. You should check the Wine HQ database for specific info.

---

### Post by James_Lochhead on 2009-04-17
Try [http://www.wowwiki.com/Wine]("http://www.wowwiki.com/Wine").

---

### Post by sandyd on 2009-04-17
could you post the EXACT directory of where you found your cdrom?
try this

update your root password
```

sudo passwd root

```

unmount cd
```

sudo umount /media/cdrom0/

```

P.S. you might wanna read instructions here....
[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

---

### Post by aldrinmirambel on 2009-04-17
I didn't experience that kind of problem. Just install it using CD, don't just link it at any site maybe there are missing files, it maybe corrupted, let just say.

____________________________
**[Art Framed, Posters, Art Prints](http://www.ichatart.com/)**

---

### Post by Novnia on 2009-04-17
/media/cdrom0/ is the dir exactly.

updated my pw unmounted the cd and am trying to inastall again. thanks for the wiki link, that is very useful. ill post as problems arise

my friend didnt lie when he said the linux community was great. more support here than for windows

---

### Post by Wiebelhaus on 2009-04-17
I've done it many times the best experience , almost seamless was with [crossover by codeweavers.]("http://www.codeweavers.com/")

---

### Post by jbaerbock on 2009-04-18
I would recommend Cedega as it is more meant for gaming whereas crossover is more for office type programs. I have WoW working flawlessly on my Ubuntu install with Cedega.

---

### Post by Novnia on 2009-04-18
doesent cedega cost moneies?

---

### Post by jbaerbock on 2009-04-18
Yeah but not that much and you only have to pay for it once, continued payment is for the support. For me its worth it if I can ditch windows.

---

