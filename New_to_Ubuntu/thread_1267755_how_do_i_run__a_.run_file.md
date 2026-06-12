---
title: "how do i run  a .run file????"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-09-16
how do i run  a .run file????

---

### Post by misfitpierce on 2009-09-16
Easiest way is probably with terminal by finding it and executing it by doing this example:
[quote="TERMINAL"]sudo sh /home/USERNAME/FILENAME.run[/quote]

Something like that as an example.

---

### Post by pmlxuser on 2009-09-16
command is 
```

./filename

```
so in this case i guess
```

./.run

```

---

### Post by misfitpierce on 2009-09-16
> **pmlxuser said:**
> command is 
```

./filename

```so in this case i guess
```

./.run

```

You can do this as well but I did this on a game one time and it did not install into the correct root directory so icons and menu setting did not set up right... It's dependant... Can try either way. The sudo sh is usually what I use I believe for .sh or .run or .bin files to just execute it as root so it goes into root directories as it needs.

---

### Post by dagoth_pie on 2009-09-16
Keep in mind that you should never put sudo in front of any command to run binaries if you don't know how trustworthy they are.

---

### Post by fanglinyong on 2009-09-16
well, you should use the ls code ```
ls -l  name.run
```
if the file didn't have x properties,you should use this command```
chmod u+x name.run
```
and then, you can do ```
sudo ./name.run
```
good luck!!!

---

