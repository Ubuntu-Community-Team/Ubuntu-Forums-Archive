---
title: "How Do I View My System Information?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by jozmoz on 2009-01-16
Hi does anyone know how I can view my system information? I'm trying to find out in particular my ram memory size without going into the bios.

Thanks for any help.

---

### Post by binbash on 2009-01-16
for memory : free -m

---

### Post by Sealbhach on 2009-01-16
You can find that in System/Administration/System Monitor. It's on the first tab.


.

---

### Post by perlluver on 2009-01-16
> **jozmoz said:**
> Hi does anyone know how I can view my system information? I'm trying to find out in particular my ram memory size without going into the bios.

Thanks for any help.

I see that you are in Xubuntu, you can either use the free -m option in the terminal, or you should have a System Monitor.

---

### Post by lovelyvik293 on 2009-01-16
You can see it by going System->Admin.->System monitor.

---

### Post by hyper_ch on 2009-01-16
Or make a file you can share with others:
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by SteveDee on 2009-01-16
> **jozmoz said:**
> Hi does anyone know how I can view my system information? I'm trying to find out in particular my ram memory size without going into the bios.

Thanks for any help.

Sysinfo is a great application for this.

---

### Post by jozmoz on 2009-01-16
thanks everyone!:P

---

