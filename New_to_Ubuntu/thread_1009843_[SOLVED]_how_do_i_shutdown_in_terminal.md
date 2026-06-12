---
title: "[SOLVED] how do i shutdown in terminal?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-13
what is the command line for that? without having to ask for the password.

i remember reading some where its 'sudo init -some letters'

i have used 'sudo poweroff' than the password.

---

### Post by nakama85 on 2008-12-13
> **shiningkenmonster said:**
> what is the command line for that? without having to ask for the password.

i remember reading some where its 'sudo init -some letters'

i have used 'sudo poweroff' than the password.

it should be 

```
sudo shutdown -h now
```


for more info on the shutdown command in terminal type
```
shutdown --help
```

it will show you all the filters you can apply

---

### Post by Michael.Godawski on 2008-12-13
```
sudo shutdown -h now
```
I think the shutdown process is linked with root rights so the password is necessary.

---

### Post by iaculallad on 2008-12-13
Drop to your terminal and issue the command below:

```
sudo chmod u+s /sbin/shutdown
```

Now, you don't have to use sudo everytime you shutdown your system, simply:

```
shutdown -h now
```

---

### Post by billgoldberg on 2008-12-13
```
sudo shutdown
```

is enough for me.

---

### Post by billgoldberg on 2008-12-13
> **iaculallad said:**
> Drop to your terminal and issue the command below:

```
sudo chmod u+s /sbin/shutdown
```

Now, you don't have to use sudo everytime you shutdown your system, simply:

```
shutdown -h now
```

What good is having sudo then?

---

### Post by Joeb454 on 2008-12-13
I just use ```
sudo poweroff
``` If I ever need to shutdown from a terminal :)

---

### Post by iaculallad on 2008-12-15
> **billgoldberg said:**
> What good is having sudo then?

We'll, if you want other users to shutdown the computer without any privileges on doing that action. The OP's choice, just a suggestion.

---

### Post by Tatty on 2008-12-15
```
sudo halt
```

is the same as sudo shutdown -h now

---

### Post by Poyntz on 2008-12-15
> **billgoldberg said:**
> ```
sudo shutdown
```

is enough for me.

Bizarre. I have to type **sudo shutdown now**

I personally use:
```
sudo init 0
``` to shutdown

---

### Post by Drakkor on 2008-12-15
I like to sometimes schedule a shutdown, while I listen to radio at night, so 
I can go sudo shutdown -h 23:30 , and it'll shutdown at 11:30 pm. :p

---

