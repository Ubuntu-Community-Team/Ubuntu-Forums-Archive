---
title: "Simple copy script"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by ajn946 on 2010-05-30
Greetings, 

Apologies for the extreme newbie question but I am wanting to make a simple script to copy a directory from a usb drive the computer and overwriting any existing contents.

Would anyone be able to advise me how to do this?

Greatly appreciated :)

---

### Post by Ozymandias_117 on 2010-05-30
```
cp /media/name_of_usb_drive/* ~/where/you/want/files
```

Edit: To make a script, just start a text document with ```
#!/bin/bash
```

---

### Post by ajn946 on 2010-05-30
Thanks mate.

---

### Post by ajn946 on 2010-05-30
Ok, tried this but cant get to work. Below is what I have, I did chmod 755 to make it executable. 


#!/bin/bash
#Test Script

cp /home/andrew/Downloads/test ~/home/andrew/Documents

---

### Post by lisati on 2010-05-30
"~" at the start is a shortcut to  "/home", so one or other is probably unnecessary..... :)

---

### Post by Ozymandias_117 on 2010-05-30
> **lisati said:**
> "~" at the start is a shortcut to  "/home", so one or other is probably unnecessary..... :)

Guess I should have mentioned that to the OP :oops:

---

