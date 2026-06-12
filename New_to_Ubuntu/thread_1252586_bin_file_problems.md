---
title: "bin file problems"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by phillip1882 on 2009-08-29
i have a bin file that i'm trying to install, its currently on my desktop.
i went to my decktop folder with cd Desktop okay, but wen i try
./file.bin i get command not found error.
even with sudo ./file.bin i get the same error.

---

### Post by izziere on 2009-08-29
Have you ensured that the file is executable?

---

### Post by mapes12 on 2009-08-29
I've not heard of that command. What are you trying to install please?

---

### Post by credobyte on 2009-08-29
file.bin usually means that you need to replace "file" with an actual file name you have there .. :)

```
cd $HOME/Desktop
ls
```

Is there anything similar to file.bin ?

---

### Post by phillip1882 on 2009-08-29
here3's the exact name of the file that i typed in.
NVIDIA-Linux-x86-190.18.04-pkg1.bin
i only ment "file" in the general sence of typing in file name followed by .bin

---

### Post by XCan on 2009-08-29
I think it is as izziere claims, you have to make it executable. It would help if you posted your output of ```
 ls -l 
``` in the dir containing your file. If it's not executable you'll have to ```
 chmod +x NVIDIA-Linux-x86-190.18.04-pkg1.bin 
``` before trying to run it.

---

### Post by NoaHall on 2009-08-29
Note of warning before hand, you should really install the drivers from system -> admin -> hardware drivers as installing from the website might cause serious problems! You will also need to run it from a terminal using "ctrl + alt + 3" , and using sudo.

---

### Post by cavrep on 2009-09-12
I'm also having bin file problems. I went to desktop in file system and in terminal ran:

chmod a+x (name of file).bin

but got this output:

farang@farang-desktop:~$ chmod a+x ffmpeg_0.cvs20070307-5ubuntu7.3+medibuntu1_i386.deb
chmod: cannot access `ffmpeg_0.cvs20070307-5ubuntu7.3+medibuntu1_i386.deb': No such file or directory
farang@farang-desktop:~$ 

Please tell me what I am doing wrong?

---

### Post by NoaHall on 2009-09-12
It's just "chmod +x" you need

---

### Post by zman58 on 2009-09-12
Exactly what are you trying to do? Install nvidia driver?
If so, then you should be using a different approach. I believe that can be done directly using one of the selections below the System menu.

System -> Administration -> Hardware Drivers 

It is very simple.

---

### Post by pedro3005 on 2009-09-12
It appears your file is a .deb and not .bin . Just double click it and install. If you need it via CLI, ```
sudo dpkg -i file.deb
```

---

