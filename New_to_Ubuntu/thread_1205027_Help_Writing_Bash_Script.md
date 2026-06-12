---
title: "Help Writing Bash Script"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-07-05
Hey all,

I'm writing a quick bash script so that conky has a delayed autostart. 

```
#!/bin/bash

# Start conky 35 seconds after startup as to not break graphics

sleep 35 && conky -c .conkyrc1 && conky -c .conkyrc2;
```

The issue comes up because I've got two separate conky configs I want to run because they're in different places on the desktop. The second config will never start because the first config never comes to any "conclusion". As I understand "and" statements, they go like this:

```
statement 1 && statement 2
```

where statement 2 is executed on completion of statement 1. Now in my case the first conky config never actually completes since it's running the whole time my computer is so the second conky config doesn't ever start. Is there some way I can get around this and keep it in the same script? I realize I can just have a separate script for each config but I'd rather do something clever and learn something than do something easy.

Thanks,
SMRT

---

### Post by Cheesemill on 2009-07-05
Try replacing the second && with a ;
; will go onto the next task immediately whereas && waits for the previous task to finish.

---

### Post by I[AM]SMRT on 2009-07-05
It's still not working "/. Not even when I directly put it into the terminal.

```
brian@brian-laptop:~$ conky -c .conkyrc1; conky -c .conkyrc2
```

Strangely, when I do that, then kill it with "ctrl-c" it kills the first conky session then it starts the second conky session.

---

### Post by lswb on 2009-07-05
Just put the commands on separate lines and use a single '&' at the end of the conky lines, so that those commands run in the background:
```

sleep 35
conky -c .conkyrc1 &
conky -c .conkyrc2 &

```

---

### Post by I[AM]SMRT on 2009-07-05
> **lswb said:**
> Just put the commands on separate lines and use a single '&' at the end of the conky lines, so that those commands run in the background:
```

sleep 35
conky -c .conkyrc1 &
conky -c .conkyrc2 &

```
This worked, thanks!

I'm an idiot for not realizing that, haha.

---

