---
title: "Command for hardware"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by jhazard112 on 2010-01-19
Is there any commands that you can run in the terminal window that will show you all of the hardware currently installed on your system?  I thought there was but i cant remember how to do it...any help is much appreciated.

---

### Post by diesch on 2010-01-19
```
sudo lshw
```

---

### Post by nick_goodfate on 2010-01-19
```
sudo lshw
```

---

### Post by sisco311 on 2010-01-19
lshw

```
sudo lshw
```

You may want to pipe it to less:
```
sudo lshw | less
```

Or save the output as a html file:
```
sudo lshw -html > hw.html
```
and open it with your favorite web browser:
```
w3m hw.html
```

If you want a gui app, I would recommend [hardinfo]("apt://hardinfo").

---

### Post by Iowan on 2010-01-19
An abbreviated list:
```
sudo lshw -short
```

---

### Post by sandyd on 2010-01-19
```

*lshw* -[I]html >> ~/Desktop/lspci.html

```

will create a pretty nice clean html page thats easily readable on your desktop
[/I]

---

### Post by PenguinInside on 2010-01-20
There's also a graphical program hardinfo that displays hardware information, sort of like some programs in Windows do.

sudo apt-get install hardinfo
[apt://hardinfo]("apt://hardinfo")

---

