---
title: "How do I auto mount dirs to my window shares?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Jynks on 2009-01-25
At the moment i have networking working fine between my xubuntu system and my windows box. The only problem is that the shares are not mounted when i boot into xubuntu...

I made a .sh file
```
#!/bin/bash
mount.cifs //10.1.1.3/Archive ~/Network/Showreel-Archive01
mount.cifs //10.1.1.3/D ~/Network/Showreel-Archive02
```

And i simply right click it and select [b]execute[b] and the shares are mounted.

How can I get xubuntu to auto mount these dirs?

---

### Post by bgerlich on 2009-01-25
A nice tutorial to do exactly what you want:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

