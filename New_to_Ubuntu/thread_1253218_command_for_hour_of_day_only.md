---
title: "command for hour of day only?"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by garyed on 2009-08-29
I know if I do ```
date
``` it will show the complete date & time.
Is there a way to just  have it output the hour of day only & nothing else?
I want the command to output a single number from 1 to 24 so I can use it in a script.

---

### Post by BenAshton24 on 2009-08-29
```
date +%H
```

Read the man pages? :P

Hope this helps you, Ben.

---

### Post by garyed on 2009-08-29
> **BenAshton24 said:**
> ```
date +%H
```

Read the man pages? :P

Hope this helps you, Ben.

Thanks, that's exactly what I needed.
I read the man pages & tried ```
date %I 
date %H 
```but I didn't see to put the
"+" sign in front of the letters.

---

