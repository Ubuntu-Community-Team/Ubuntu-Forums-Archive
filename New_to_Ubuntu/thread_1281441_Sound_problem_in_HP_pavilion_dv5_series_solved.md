---
title: "Sound problem in HP pavilion dv5 series solved"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by nns2006 on 2009-10-03
Hi,
I found this solution which help me get sound on my friend computer.

this is the link of webpage [http://29a.ch/2009/6/2/getting-audio-to-work-on-a-hp-pavilion-dv5-ubuntu-9-04]("http://http://29a.ch/2009/6/2/getting-audio-to-work-on-a-hp-pavilion-dv5-ubuntu-9-04")

```
 cd /etc/modprobe.d 
```
```
sudo gedit alsa*conf 
```

and add the following lines at the end of the file:

```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
```

---

### Post by nns2006 on 2009-10-04
This solution also work with Compaq Presario CQ40 .

---

### Post by jhk30 on 2009-10-07
too bad this doesnt work on my HP dv2 1027ca.
I wish i could get sound working. I guess ill go back to windows 7.

---

