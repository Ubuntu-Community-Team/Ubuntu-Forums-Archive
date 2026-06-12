---
title: "Dead MBR entries?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by McTwitch on 2011-01-27
Right, I'm running Ubuntu 10.04 on a Sys 76 laptop. I plugged in my Portable Harddrive, which has 10.04 installed and running, and booted from it. When I booted back to the laptop, instead of just booting to 10.04, it brought up the screen where I can choose what to boot to. Seeing as there is only the one operating system on it, all of the other links are just dead. They are the same links, though, that show up when I boot onto the harddrive on my Windows Desktop Computer.

So, my question is, would sudo apt-get update grub remove these dead entries, and if not, what will?

---

### Post by Bucky Ball on 2011-01-27
Try this:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

It honestly rocks and will let you reorder or remove entries from grub. ;)

---

### Post by psusi on 2011-01-27
You want sudo update-grub.

---

### Post by wojox on 2011-01-27
> **Bucky Ball said:**
> Try this:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

It honestly rocks and will let you reorder or remove entries from grub. ;)

Leave it someone to make a GUI for 


> **psusi said:**
> You want sudo update-grub.

---

### Post by McTwitch on 2011-01-27
I went with sudo update-grub. It said that it found some entries, but nothing about deleting the older ones that were there when I tried to boot. Does that mean it has deleted them?

---

### Post by wojox on 2011-01-27
Run it again and post it back up here.

---

### Post by McTwitch on 2011-01-27
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done


Apparently the first message was too short. So this is how I extended it.

---

### Post by wojox on 2011-01-27
Your fine. You have two kernels. You shouldn't have a problem when you reboot. :P

---

### Post by McTwitch on 2011-01-27
Awesome. Thanks for the help!

---

