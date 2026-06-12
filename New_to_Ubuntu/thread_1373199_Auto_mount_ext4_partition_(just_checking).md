---
title: "Auto mount ext4 partition (just checking)"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Max_Mackie on 2010-01-05
I just want to make sure I'm doing this right so I don't screw anything up. I want to automatically mount my "storage" partition at boot. The partition is NOT windows.

```
sudo gedit /etc/fstab
```

then I add:

```
/dev/sda7 /media/Storage ext4 nls=utf8 umask=0222 0 0
```

Its the part after "ext4" that I'm not sure about. Can someone clear this up for me.

---

### Post by bodhi.zazen on 2010-01-05
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Max_Mackie on 2010-01-05
Thanks bodhizazen :)

---

### Post by Zoot7 on 2010-01-05
The part directly after "ext4" are the parameters that are used when mounting the parition. The "0" after that is the "Dump" option, which is a backup feature that is scarcly used really, and the last "0" specifies for fsck to check the partition for errors upon booting.

In actual fact all you really need to add is this:
```
/dev/sda7 /media/Storage ext4 defaults 0 0
```

---

### Post by bodhi.zazen on 2010-01-05
> **Zoot7 said:**
> The part directly after "ext4" are the parameters that are used when mounting the parition. The "0" after that is the "Dump" option, which is a backup feature that is scarcly used really, and the last "0" specifies for fsck to check the partition for errors upon booting.

In actual fact all you really need to add is this:
```
/dev/sda7 /media/Storage ext4 defaults 0 0
```

Well, I would use 0 2 rather then 0 0 (no need to disable checking your partition for errors, lol )

---

### Post by Zoot7 on 2010-01-05
> **bodhi.zazen said:**
> Well, I would use 0 2 rather then 0 0 (no need to disable checking your partition for errors, lol )
Haha, fair enough! :)

---

### Post by Max_Mackie on 2010-01-05
Thanks guys. I'll give it a try

Edit: Just tried it. Worked perfectly. Thanks! :)

---

### Post by victorhugo289 on 2010-11-14
Below.

---

### Post by victorhugo289 on 2010-11-14
You should run tests before saying everything's alright.
> **Zoot7 said:**
> 
```
/dev/sda7 /media/Storage ext4 defaults 0 0
```

Have you tried to delete a file from the so mounted partition? It will say "Cannot move file to trash, delete permanently?"

So before saying it 'works perfectly' please check again.

---

