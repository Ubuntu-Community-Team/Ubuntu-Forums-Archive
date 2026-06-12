---
title: "Error messege when i open Synaptic Manager"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-20
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.




what should i do/?  i cannot open Synaptic??.

---

### Post by Skol312000 on 2009-03-20
i also receive this messege when i try to open "Add/Remove" under Appplications .............this is a big deal...what tdo i do?//

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by ramjet_1953 on 2009-03-20
All you have to do is what the message tells you.

Navigate to [COLOR="Blue"]Applications>Accessories>Terminal
[/COLOR]
When the window opens copy and paste this into the terminal:

```
sudo dpkg --configure -a 
```

Regards,
Roger :D

---

### Post by Skol312000 on 2009-03-20
thanks

---

