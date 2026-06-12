---
title: "App to get info about graphic card???"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by ptmax13 on 2009-11-01
Hi to all!
I've been using ubuntu for about a month now. The last couple of days I am searching for a way to get detailed info about the installed graphic card. I need it for my job. I used GPU-Z with windows but GPU-Z and WINE doesn't work in Ubuntu. I need something similar to GPU-Z for my job.

Anybody who can help me?

thanks...:D

---

### Post by wojox on 2009-11-01
Open a terminal:

```
sudo lshw -C video
```

---

### Post by tudor117 on 2009-11-01
Also try sysinfo.
Download from software center/add remove programs.

---

### Post by ptmax13 on 2009-11-01
Thank you wojox for the quick response. Usefull command but I needed something more detailed. To be more specific, I'am mainly looking for clock values (GPU, Memory, Shader) and Memory type and size.

Thanks tudor117 but Sysinfo provides little to no info for the graphic card...

---

### Post by wojox on 2009-11-01
Try this:

```
sudo lshw -html > ~/Desktop/hardware.html
```

---

### Post by ptmax13 on 2009-11-01
still no use to me, I get the same info with the former command you gave me...

---

### Post by coetzewc on 2009-11-01
In only ran System Administration Hardware Drivers in 9.04 It picked up my NVIDA drivers and two earlier versions to choose from. I Quess your repositries should be setup correct.

---

