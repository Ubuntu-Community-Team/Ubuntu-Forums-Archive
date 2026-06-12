---
title: "scrn freezes and scars"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by nnjond on 2011-04-03
Hi, 

My screen is frequently freezing and even the keyboard or mouse doesn't work.

I've been told to read the logs, But I don't know where thy are or what to look for?

Can you help me please?

Thanks

---

### Post by Dutch70 on 2011-04-03
> **nnjond said:**
> Hi, 

My screen is frequently freezing and even the keyboard or mouse doesn't work.

I've been told to read the logs, But I don't know where thy are or what to look for?

Can you help me please?

Thanks

Well, you should definitely start by reading this...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

After you've read that, please post the output of...
```
lspci | grep VGA
```

---

### Post by nnjond on 2011-04-03
Thanks for your help. I know where to find the logs now.

```
spci | grep VGA
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

```

---

### Post by Dutch70 on 2011-04-03
I'm not really familiar with that card, I did find this though if it helps any.
[[COLOR="RoyalBlue"]https://answers.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+question/151343[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+question/151343")
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1570260[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1570260")

---

