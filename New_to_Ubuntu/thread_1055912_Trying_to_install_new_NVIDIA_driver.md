---
title: "Trying to install new NVIDIA driver"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Luehrs1 on 2009-01-31
ok, i am a noob here and have tried everything.There are like a million threads for stoping x server but nothing is working for me. Is there a step by step guide to installing NVIDIA-Linux-x86-180.22-pkg1.run. or can anyone help.

Thanx

---

### Post by SnakeHips on 2009-01-31
> **Luehrs1 said:**
> ok, i am a noob here and have tried everything.There are like a million threads for stoping x server but nothing is working for me. Is there a step by step guide to installing NVIDIA-Linux-x86-180.22-pkg1.run. or can anyone help.

Thanx

what graphics card do you have?
```
lspci | grep VGA
```

and which version of Ubuntu ?

---

### Post by Gulyan on 2009-01-31
Copy the NVIDIA-Linux-x86-180.22-pkg1.run file in your home folder (for easy access to it)
Press: Ctrl+Alt+F1
this will switch you to a virtual terminal
Login and then type:
```

sudo /etc/init.d/gdm stop
./NVIDIA-Linux-x86-180.22-pkg1.run

```

Follow the steps there (generally you have to answer 'yes' or 'no' to some questions)

then, when it's finished type:
```

sudo /etc/init.d/gdm start

```

to start the display manager.

Good luck with this. :)

---

### Post by simtaalo on 2009-01-31
ignore advice above, there's a much easier way [http://ubuntuforums.org/showpost.php?p=6632383&postcount=377](http://ubuntuforums.org/showpost.php?p=6632383&postcount=377)

---

### Post by Luehrs1 on 2009-01-31
> **SnakeHips said:**
> what graphics card do you have?
```
lspci | grep VGA
```

and which version of Ubuntu ?

I have a e-GeForce 8600 GT and am running Ubuntu 8.10 the Intrepid Ibex - released in October 2008

---

### Post by SnakeHips on 2009-01-31
edit: posted before ^^^^^

me thinks we need to confirm the OP's card is supported by the driver ,i'm sure it is but as assumption is the mother of all ......

---

### Post by SnakeHips on 2009-01-31
> **Luehrs1 said:**
> I have a e-GeForce 8600 GT and am running Ubuntu 8.10 the Intrepid Ibex - released in October 2008

Please backup your xorg before proceeding

In terminal:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup
```

---

### Post by jespdj on 2009-01-31
Instructions for manually installing the nVidia driver here:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

