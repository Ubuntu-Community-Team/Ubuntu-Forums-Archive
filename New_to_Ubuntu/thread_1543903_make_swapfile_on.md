---
title: "make swapfile on /"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-08-01
i got this video from linuxjournal

lance@Therese:~/500gb/lance backintime$ sudo dd if=/dev/zero of=swapfile bs=1024 count=1024000
1024000+0 records in
1024000+0 records out
1048576000 bytes (1.0 GB) copied, 9.61435 s, 109 MB/s
lance@Therese:~/500gb/lance backintime$ sudo mkswap /swapfile
/swapfile: No such file or directory

so what do i do? the video said the last command would make the file so that all was left was to sudo swapon /swapfile to make it work what did i do wrong?

---

### Post by lance bermudez on 2010-08-01
forgot to say what i have for memory
lance@Therese:/$ free -tom
             total       used       free     shared    buffers     cached
Mem:          3891       3647        244          0        107       3228
Swap:            0          0          0
Total:        3891       3647        244

I have no swapfile that is why i wanted to add a 1gb swapfile just in case i ever need it. I have 2 sticks of 2048 mb pc5400 ddr2 667mhz installed in the computer for a total of 4096

---

### Post by sisco311 on 2010-08-01
```
sudo dd if=/dev/zero of=swapfile bs=1024 count=1024000
```
creates the file in the current working directory, in your case ~/500gb/lance\ backintime. Move it to /:
```
sudo mv ~/500gb/lance\ backintime/swapfile /
```
Or delete it and create a new one in /:
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1024000
```

[uhelp]community/SwapFaq[/uhelp]

---

### Post by lance bermudez on 2010-08-02
thank you that fixed my problem.

---

