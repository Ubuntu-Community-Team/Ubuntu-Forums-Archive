---
title: "Permisions Prob: accessing files on Flash"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by nnjond on 2010-03-28
Hi,

I've transfered some files to a Pen and now i dont have permission to copy them back again! Now I'm hoping there are some terminal commands to solve it.

---

### Post by tom.swartz07 on 2010-03-28
> **nnjond said:**
> Hi,

I've transfered some files to a Pen and now i dont have permission to copy them back again! Now I'm hoping there are some terminal commands to solve it.

I dont quite understand what youre saying, did you try using the terminal copy?

```
sudo cp /path-to-file/ /path-to-copy-file-to/
```?

If that doesnt work, you might just have to change the permissions of the file using chmod and chown.

---

### Post by nnjond on 2010-03-28
Thanks for your help. What's the modification to cp all files in directory?

---

### Post by tom.swartz07 on 2010-03-28
> **nnjond said:**
> Thanks for your help. What's the modification to cp all files in directory?

```
cp -r /path-to-file /path-to-destination
```


If you ever have any questions about any command, you could just type
man 'command'

and it will tell you everything you ever need about it. 

In your specific case, ```
man cp
```
You could exit out of the manual pages with the Q key.

Have fun!

---

