---
title: "Problem !!!"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by fabio cannavaro on 2011-04-28
i got Compaq Presario CQ60 & working with ubuntu 10.10 - everything is working properly except wireless driver - not working

anybody can tell me what to do ?!!

---

### Post by Leppie on 2011-04-28
could you post the output of the following commands:
```
lspci
lsmod
```

---

### Post by gullyt on 2011-04-28
i just started using linux this week, new to it all.i dual boot with zorin os 4 and ubuntu
11.0. 4 to try them both of them.  i have the same problem with ubunu 11.04, cant get my wireless to work, but it works with zorin os 4. help any one or point me in the direction o find help.

---

### Post by pi3.1415926535... on 2011-04-28
I would recomend following the instructions given by Leppie. Also the to the OP, if would be helpful if you were to use more helpful titles to posts in future.

Thank you

---

### Post by BertN45 on 2011-04-29
Problems with wifi are dependent on the wifi hardware used. So Leppie is right you have to start the Terminal in Accessories and type lspci. Copy / paste the text output in your reply and repeat the same for the lsmod command. Afterwards we know, what wifi hardware is used and whether the correct drivers are loaded.

---

