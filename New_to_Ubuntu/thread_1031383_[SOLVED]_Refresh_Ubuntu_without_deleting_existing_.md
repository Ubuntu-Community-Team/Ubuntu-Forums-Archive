---
title: "[SOLVED] Refresh Ubuntu without deleting existing files"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-01-05
Good Morning, I am currently running Hardy 8.04.1. I ran into an issue this past weekend with what I believe to be a kernel effecting my wireless connection. In trying to find a 'cure', I managed to mess up GStreamer. This morning I went through my files to confirm I had backed-up everything. (Of course there's always something you miss). Originally, I went from 7.10 to 8.04 due to an update error effecting a program I use for work. Then on to 8.10 in an effort to keep on top of the 'latest', but ran into a Java JRE conflict with another program I use... I reverted back to Hardy. It seems as though 20% of the time I download the updates I run into issues with my computer or additional software I need for work. As you can tell I spend a lot of time looking for answers on this forum. I now spend more time chasing solutions than I do actual working. Does anyone know of a way to re-load Ubuntu (Any Version) without loosing files already on the drive:confused:

If I need to reinstall Ubuntu (ie:7.10) is there a problem with refusing the updates ? (as that is where my problems began).

---

### Post by CoCoKnots on 2009-01-05
Any Ideas re:updates???

---

### Post by pastalavista on 2009-01-05
you could try:```
sudo aptitude safe-upgrade
``` and if that doesn't help, try:```
sudo aptitude full-upgrade
```

---

### Post by CoCoKnots on 2009-01-05
> **pastalavista said:**
> you could try:```
sudo aptitude safe-upgrade
``` and if that doesn't help, try:```
sudo aptitude full-upgrade
```

Thanks Pastalavista, I tried both, but neither worked. I'm going to start over (Again) with 7.10 which I have the disc for... Do I need to download all of the updates &/or 8.04 before I'm able to load 8.10 ??? It has been a couple of months since I tried Intrepid. I would like to try it again. Does anyone know if perhaps more of the 'bugs' are out of Java.

---

### Post by gettinoriginal on 2009-01-05
Suggestion, since you ran into trouble with updates going from 7.10 to 8.10, it would be better for you and your system to do a fresh install of 8.10.  If you do not have a burner on your computer, maybe a friend or relative could burn one for you??  :P

---

### Post by CoCoKnots on 2009-01-05
> **gettinoriginal said:**
> Suggestion, since you ran into trouble with updates going from 7.10 to 8.10, it would be better for you and your system to do a fresh install of 8.10.  If you do not have a burner on your computer, maybe a friend or relative could burn one for you??  :P

Thanks GettinOriginal, I do have a burner. I'm installing this on a Sony VAIO Notebook. Is there a problem if I jump from 7.10 to 8.10 ?

---

### Post by gettinoriginal on 2009-01-05
you cannot jump from 7.10 to 8.10, but since you have a burner, save any personal files you need by burning them to disk with brasero or your choice of burner, then burn an ISO of Ubuntu 8.10 (be sure to burn at the slowest speed possible) and install from it, then you can use the disk you burned with personal files on it to restore them to your computer.  :P

---

### Post by CoCoKnots on 2009-01-05
Great... Thanks again. I have 7.10 on the system now. It sounds like I will need to install 8.04 before moving on. I'll post again afterwards.

---

### Post by CoCoKnots on 2009-01-06
> **gettinoriginal said:**
> you cannot jump from 7.10 to 8.10, but since you have a burner, save any personal files you need by burning them to disk with brasero or your choice of burner, then burn an ISO of Ubuntu 8.10 (be sure to burn at the slowest speed possible) and install from it, then you can use the disk you burned with personal files on it to restore them to your computer.  :P

I have tried three times to download & burn a CD for 8.04. I keep getting an error in one file. I was able to download & burn 8.10 without any problem. However, I did not install the either... I'm still on 7.10. Should I just order the original 8.04 CD from Ubuntu & wait until I receive it before continuing. (You said I can not jump to 8.10 from 7.10).

---

### Post by CoCoKnots on 2009-01-07
"Solved..." Somewhat. I assume there isn't anyway around the format game... I went ahead & re-installed 7.10 then 8.04 thru the update manager option.

---

### Post by markbuntu on 2009-01-07
You can install over an old install without formatting, just uncheck the format box. Everything will get overwritten except the /home directory. That said, all the hidden configuration files in your /home/user directories could make a mess of things since all your apps will get upgraded to newer versions.

---

### Post by linux_tech on 2009-01-07
Be sure to backup all your data before installing.

---

