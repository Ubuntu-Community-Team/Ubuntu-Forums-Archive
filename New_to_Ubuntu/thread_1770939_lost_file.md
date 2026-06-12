---
title: "lost file"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by squrl on 2011-05-29
Through my own ignorance I lost a file. 

I tried to make an image file with part image. The program did its thing and seven minutes later it said it finished successfully

The problem is I put in thisone.000 for the saved file namje. Now I cant find any ref to it. Can someone give me a suggestion where it might be

Thanks.

---

### Post by jtarin on 2011-05-29
In a terminal enter the command "sudo updatedb" (without quotes). Let it run and when it finishes enter the command "locate filename" (without quotes and "filename" is the name of your file)

---

### Post by webofunni on 2011-05-29
You mean, you dont know where you saved that file ?

---

### Post by webofunni on 2011-05-29
If you ran it as a user, usually it will be in users home directory. 

```

find ~/ -iname thisone.000

```

will also work

---

### Post by jerrrys on 2011-05-29
find thisone.000 :D

---

### Post by webofunni on 2011-05-29
already suggested ;-)

---

