---
title: "Installed wrong and unable to remove"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by fly360 on 2009-07-26
I installed a JAVA package and now it is stuck on my desktop and I'm unable to remove it. I have attached a screen shot of the mess I'm in.
 I used :

cd Desktop

sudo sh ./jre-6u14-linux-i586.bin

It looked like it ran fine but it ended up on my desktop locked and unable to move or remove it.

Any help would be appreciated.

---

### Post by Liolikas on 2009-07-26
try:
sudo rm -rf it
OR
try to find in folder properties where to disable that lock.

---

### Post by wojox on 2009-07-26
```
chmod a+x name_of_file
```

---

### Post by gjoellee on 2009-07-26
Press Alt + F2 and run
```
gksu nautilus
```

Navigate to your users desktop and remove the folder.

---

### Post by NullHead on 2009-07-26
Lets change the permissions so you can delete it. ```
sudo chmod 777 ~/Desktop/jre1.6.0_14
```

After that, you should be able to delete it like you normally would ;)

---

### Post by theozzlives on 2009-07-26
Here's the right way:

```
sudo chown yourusername jre1.6.0_14 -R
```
(note the capital R not r), delete it....
```
chmod +x filename.bin
./filename.bin
```

---

### Post by theozzlives on 2009-07-26
.

---

### Post by theozzlives on 2009-07-26
> **gjoellee said:**
> Press Alt + F2 and run
```
gksu nautilus
```

Navigate to your users desktop and remove the folder.

That'll fill up the trash in the root folder.

---

### Post by fly360 on 2009-07-26
Thanks to everyone. Its gone.
Ever since I've installed Jaunty I haven't been on my other OS system computers.

---

