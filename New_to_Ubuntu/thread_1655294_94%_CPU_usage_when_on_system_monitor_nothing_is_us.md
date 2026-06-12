---
title: "94% CPU usage when on system monitor nothing is using any CPU."
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-12-29
Ive been getting this problem for about a week, when i use my laptop for about an hour it gets really slow and my cpu is at about 94%. When i go to system monitor there is only chrome that is running 6% of cpu and everything else is sleeping or in zombie mode. What would be causing this ?

---

### Post by endotherm on 2010-12-29
try running htop from the command line (install it from the repos first). run it with sudo so you can be sure you are seeing all the processes, including roots.
```

sudo htop

```

it should give you a much more reliable view of the actual process consumption (GSM really impacts the measurements it;s attempting to display). the process using all the CPU shoudl appear at the top of the output.

---

### Post by Rave Gloves on 2010-12-29
> **endotherm said:**
> try running htop from the command line (install it from the repos first). run it with sudo so you can be sure you are seeing all the processes, including roots.
```

sudo htop

```

it should give you a much more reliable view of the actual process consumption (GSM really impacts the measurements it;s attempting to display). the process using all the CPU shoudl appear at the top of the output.
```
andrew@andrew-R610:~$ sudo htop
sudo: htop: command not found

```

Looks like you have made a slight mistake :) it's top im sure

---

### Post by endotherm on 2010-12-29
> **Rave Gloves said:**
> ```
andrew@andrew-R610:~$ sudo htop
sudo: htop: command not found

```Looks like you have made a slight mistake :) it's top im sure
nope, htop is a big upgrade on top, but as I mentioned you have to install it, with a command like
```
sudo apt-get install htop
```however you are correct, top will display much the same information. I just like htop better.

did you get the info you need from top?

cheers

---

### Post by kgarbutt on 2010-12-29
Just enter top at the command line. Ctl c to quit

---

### Post by Rave Gloves on 2010-12-29
```
13761 root      20   0  6912 2604 1892 R   96  0.1  15:14.45 apt-get            

```

This seems to be the problem, what will i do?

Sorry it didn't copy right, the CPU% is 96 :/

---

### Post by endotherm on 2010-12-29
if you try
```
sudo kill 13761
```does cpu usage drop again, or does the process respawn?

---

### Post by Rave Gloves on 2010-12-29
It seems to have gone and everything looks like it's back to normal :) thank you :).

I will know what to do next time this happens. Why did apt-get take up so much cpu?

---

### Post by endotherm on 2010-12-29
> **Rave Gloves said:**
> It seems to have gone and everything looks like it's back to normal :) thank you :).

I will know what to do next time this happens. Why did apt-get take up so much cpu?

that's the next question. 
if you run a command like:
```
sudo apt-get update && sudo apt-get upgrade
``` (check for updates and install if check succeeds)  does the command complete correctly, or does it get stuck again?

---

