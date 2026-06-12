---
title: "Can't find grub to edit"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Schapper on 2010-09-04
Hello,

I need to edit grub to sort out this blank screen on startup problem with 10.04, but can't seem to find it. for instance, the command:

sudo nano /etc/default/grub

just brings up a blank nano screen and the caption [NEW FILE] at the bottom of it. I assume this command should open up the grub file for editing, but it can't find one in that location, so it makes to open a new one. There is a file called grub-save in this directory, but that seems empty. 

Can someone help me please with what sems a fairly basic question? Cheers.

---

### Post by Rubi1200 on 2010-09-04
Do you by chance have more than 1 Ubuntu installation (i.e. an older version on 1 partition and 10.04 on another)?

---

### Post by Schapper on 2010-09-04
I don't think so. I was running 9.10, but updated to 10.04 a couple of weeks ago, and I don't have a partitioned HDD.

---

### Post by Rubi1200 on 2010-09-04
You ran the command above in the terminal?

Strange! Maybe try gedit instead of nano?

---

### Post by Schapper on 2010-09-04
Same result. There is no file called grub in the etc/default directory, but my computer boots up just fine... except that I have to open the grub screen on startup and type in i915.modeset=1 before "quiet splash", before continuing to boot. That's what I want to insert permanently, so I don't have to keep doing it.

---

### Post by Rubi1200 on 2010-09-04
It sounds as if the files may not be in the default places.

Run this in the terminal and post the output:

```
whereis grub
```

---

### Post by Schapper on 2010-09-04
Thanks for all your help, Rubi. Here is the output:

grub: /usr/sbin/grub /etc/grub.d /usr/lib/grub /usr/share/grub /usr/share/man/man8/grub.8.gz

---

### Post by Rubi1200 on 2010-09-04
> **Schapper said:**
> Thanks for all your help, Rubi. Here is the output:

grub: /usr/sbin/grub /etc/grub.d /usr/lib/grub /usr/share/grub /usr/share/man/man8/grub.8.gz
I get a different result with this command.
Why would grub be in /usr/sbin?

I would try looking for the file there.

---

### Post by johnson094 on 2010-09-19
Have been troubleshooting a intel chipset problem, was looking at modeset in grub and came across this thread.  My grub is located in the same place as is Schapper's.  Anyone figure out why? I know when I was looking for /etc/x11/xorg.conf it too was under the usr/* folder.
 
David

---

### Post by sandyd on 2010-09-19
> **Schapper said:**
> I don't think so. I was running 9.10, but updated to 10.04 a couple of weeks ago, and I don't have a partitioned HDD.
was 9.10 an upgrade as well?

If it was, you don't have grub2 installed.

If the above conditions apply, see [https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%20and%20newer%29](https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%20and%20newer%29)

---

### Post by drs305 on 2010-09-19
You should be able to check your grub version with```

grub-install -v
```

Grub 0.97 is grub legacy. 1.96 or later is Grub 2

---

