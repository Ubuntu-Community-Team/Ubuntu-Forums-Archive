---
title: "Major Server Issues -- Need ASAP Help"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by dmaxel on 2010-02-15
Hi everyone,

I'm sad to say that I have some major issues with my Ubuntu Server, and need help pronto as it runs a website. Apparently while Ubuntu was minding its own business the power was knocked out for a few minutes. Since this, nothing worked. I hooked up a keyboard and monitor to see what it spits out. Weird enough, as soon as the BIOS is done booting, it just comes to a blinking cursor, and stays there, forever. I can't type anything in, so its stuck at a brick wall. What can I do to rescue the system without having to reinstall Ubuntu and all that?

To give some technical details, it was running Karmic on an ext4 partition. Hard drive is perfectly fine.

Thanks.

---

### Post by bodhi.zazen on 2010-02-15
Boot a live CD and run fsck on your HD.

```
sudo fsck -y /dev/sda1
```

If that does not fix the problem, try re-installing grub

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by dmaxel on 2010-02-15
OK, so I tried to boot into the Live CD, which wouldn't work either. I decided to see if the CD drive was causing the problem, and after making my HDDs boot first, it booted into Ubuntu Server flawlessly. Haha, weird fix, but it worked. I can already tell that too much change isn't the best thing for my system, so I'm changing it's release prompts from normal to LTS. Hope Lucid is gonna rock.

Thanks again for your help.

---

