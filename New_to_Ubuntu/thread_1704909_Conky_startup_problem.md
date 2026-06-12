---
title: "Conky startup problem"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by samgonsalvis on 2011-03-11
I just started using conky. I managed to push conky into startup applications by typing "conky" in the text box for command. But once i tried rebooting, the conky window covered up my panels. It stays on top of my running programs. But when I start it from terminal, it behaves in the normal way. I tried reading the code in .conkyrc. The window property was set to behind. How do I set conky to begin at startup without making it cover up all windows?? Please help.:confused:

---

### Post by TeoBigusGeekus on 2011-03-11
Create an empty file
```
#!/bin/bash
sleep 5
conky
```
Save it as conky_start, or something. Make it executable
```
chmod +x conky_start
```
and put in your startup applications an entry with
```
/path/conky_start
```
as its command.
If you still have the same problem increase the value in the sleep command.

---

