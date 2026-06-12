---
title: "/bin/bash /bin/sh symlink problem"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Duvelhedz on 2010-08-12
I*went*and*typed*this*into*my*terminal*when*installing*spoonwep.*I*have*had*no*problems*on*previous*versions*of*Ubuntu*but*10.04*didn't*like*what*I*did*to*it.*

Code:*"sudo*rm*/bin/sh*&&*sudo*ln*-s*/bin/bash/*/bin/sh"

I guess I*need*to*chroot*into*the*installation*from*a*live*cd*/*USB to fix it.*Do*I*need*to link /proc*,*/sys or any other folders from*the*running*system?*And*what*do*I*have*to*type*to*revert*the*changes? Please help!

Thanx.*

---

### Post by lkjoel on 2010-08-12
> **Duvelhedz said:**
> I*went*and*typed*this*into*my*terminal*when*installing*spoonwep.*I*have*had*no*problems*on*previous*versions*of*Ubuntu*but*10.04*didn't*like*what*I*did*to*it.*

Code:*"sudo*rm*/bin/sh*&&*sudo*ln*-s*/bin/bash/*/bin/sh"

I guess I*need*to*chroot*into*the*installation*from*a*live*cd*/*USB to fix it.*Do*I*need*to link /proc*,*/sys or any other folders from*the*running*system?*And*what*do*I*have*to*type*to*revert*the*changes? Please help!

Thanx.*
I just have a question... was those "*" intentional?

---

### Post by Duvelhedz on 2010-08-12
don't know how all the stars got in between every word. Apologies

here it is again

I'm blaming the stars on a stupid iphone. Appears fine before I post the message. Stars appear after I hit the post button. No idea why. 
  I*went*and*typed*this*into*my*terminal*when*installing*spoonwep.*I*have*had*no*problems*on*previous*versions*of*Ubuntu*but*10.04*didn't*like*what*I*did*to*it.*Code:*"sudo*rm*/bin/sh*&&*sudo*ln*-s*/bin/bash/*/bin/sh"
I guess I*need*to*chroot*into*the*installation*from*a*live*cd*/*USB to fix it.*Do*I*need*to link /proc*,*/sys or any other folders from*the*running*system?*And*what*do*I*have*to*type*to*revert*the*changes?*

---

### Post by lkjoel on 2010-08-12
> **Duvelhedz said:**
> don't know how all the stars got in between every word. Apologies

here it is again

I'm blaming the stars on a stupid iphone. Appears fine before I post the message. Stars appear after I hit the post button. No idea why. 
  I went and typed this into my terminal when installing spoonwep. I have had no problems on previous versions of Ubuntu but 10.04 didn't like what I did to it. Code: "sudo rm /bin/sh && sudo ln -s /bin/bash/ /bin/sh"
I guess I need to chroot into the installation from a live cd / USB to fix it. Do I need to link /proc , /sys or any other folders from the running system? And what do I have to type to revert the changes?
You made a slight typo in your code.
```
sudo rm /bin/sh && sudo ln -s /bin/bash**/** /bin/sh
```
That is what you did.
This is what you should do:
```
sudo rm /bin/sh && sudo ln -s /bin/bash /bin/sh
```
Now try it.

---

