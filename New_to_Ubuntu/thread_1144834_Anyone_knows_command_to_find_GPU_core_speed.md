---
title: "Anyone knows command to find GPU core speed?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by nhat on 2009-05-01
I used a few commands for my mini 9 which has a 945 chipset and GMA 950. One of the commands is the HWINFO. Unfortunately it showed too much info and cuts half of it out. Any suggestions for an application or command?

---

### Post by Malta paul on 2009-05-01
You can find some good information just Use 'Sysinfo'
Applications>Add/remove search for Sysinfo
Have fun :)

---

### Post by nhat on 2009-05-01
Thanks for the reply. I found it in synaptic manager. Unfortunately it doesn't show much info about the video info. It seems like there are a lot of info for cpu,etc but not gpu.

---

### Post by ddnev45 on 2009-05-01
ignore, misread of question.

---

### Post by Malta paul on 2009-05-02
Sorry that 'Sysinfo' didn't show your _GPU_ core speed. I have a Nvidia card and it shows my core speed plus lots of additional info. 
:)

---

### Post by eilios on 2009-05-02
Try hwinfo | less .

---

### Post by bodhi.zazen on 2009-05-02
```
grep cpu /proc/cpuinfo
```

---

