---
title: "how do i open a folder and keep terminal'in?"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by ithinkitschad on 2009-08-13
I got a second question...I guess my first was too hard for anyone to answer.....So anyway, if i got a terminal open and i wanna open Nautilus with the folder that im in and keep the same terminal free while i can also browse that folder. huh, thats a bad sentence...is that possible?

:guitar:

---

### Post by colau on 2009-08-13
> **ithinkitschad said:**
> I got a second question...I guess my first was too hard for anyone to answer.....So anyway, if i got a terminal open and i wanna open Nautilus with the folder that im in and keep the same terminal free while i can also browse that folder. huh, thats a bad sentence...is that possible?

:guitar:
I think , yes it's possible.:P

---

### Post by cocopuffz on 2009-08-13
Do you mean that you want to keep the terminal window open ontop of the nautilus window? 

If that is indeed the case, just right click the terminial window titlebar and select "Always on top"

If you press alt and use the middle mouse scroll wheel you can turn your terminal window transparent so you can view whats under it... and of course open tabs in terminal to do multiple things are the same time

Is that what you meant?

---

### Post by Buce on 2009-08-13
Try 'nautilus &'.

EDIT: Or, if you've already got nautilus running, hit CTRL+Z, then type 'bg' in the terminal.

---

### Post by amac777 on 2009-08-13
If I understand what you want to do, you should type this in the terminal:

```
nautilus . &
```

The . means to open the current directory, and the & means to run the program in its own thread so you can continue using the terminal.

---

### Post by andru183 on 2009-08-13
or just use two terminals, open another one and have it do the other task

---

### Post by stumbleUpon on 2009-08-13
I dont know if you meant this. I used to encounter this problem.

You are using the terminal in a particular directory and want to open nautilus in the same directory. Also you want to continue using the same terminal. Is that so?

In the terminal type

```
 nautilus $PWD 
```


This is the inverse of opening a terminal in a particular folder when you using nautilus to browse it. However this second task can be done be installing nautilus scripts. 

```
sudo aptitude install nautilus-open-terminal 
```

You then right click in a folder and select 'open terminal here'

---

### Post by ithinkitschad on 2009-08-13
> **amac777 said:**
> If I understand what you want to do, you should type this in the terminal:

```
nautilus . &
```The . means to open the current directory, and the & means to run the program in its own thread so you can continue using the terminal.

Perfect! Yeah thats exactly what I meant. Thanks that works perfect. Thanks for everyones quick responses, you guys pretty much kick ***. Hey whats "bump" mean by the way? First time using a forum.

---

### Post by Bachstelze on 2009-08-13
> **ithinkitschad said:**
> Perfect! Yeah thats exactly what I meant. Thanks that works perfect. Thanks for everyones quick responses, you guys pretty much kick ***. Hey whats "bump" mean by the way? First time using a forum.

"Bump" means that someone, usually the person who created the thread, is posting into it just to make it appear on the first page again, not to give an actual answer. Use with care, abuse is frowned upon. ;)

---

### Post by ithinkitschad on 2009-08-13
> **HymnToLife said:**
> "Bump" means that someone, usually the person who created the thread, is posting into it just to make it appear on the first page again, not to give an actual answer. Use with care, abuse is frowned upon. ;)

Oh, okay thanks.

---

