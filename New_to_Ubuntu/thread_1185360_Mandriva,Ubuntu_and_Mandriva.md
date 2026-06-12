---
title: "Mandriva,Ubuntu and Mandriva"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by jmfa59 on 2009-06-12
Hello,
I had Vista and Mandriva on my PC then I added Ubuntu after installing Ubuntu I got a new bootloader different than Mandriva which I think it Ubuntu's my question is it possible to get Mandriva Bootloader's back as a default bootlaoder menu.
THANKS

---

### Post by pastalavista on 2009-06-12
I believe you would need to boot from the Mandriva live CD and setup its bootloader (grub? I don't know) in place of Ubuntu's Grub.

---

### Post by lamego on 2009-06-12
Since most of us are not familiar with Mandriva and it's boot loader, the best place to ask would be the Mandriva forums.

---

### Post by louieb on 2009-06-12
Last OS installed will change the MBR to point to its boot loader.  Just guessing Mandriva like Ubuntu uses **grub** for its boot loader. Is that right?

You just need to go to the grub command line and change the MBR back to loading Mandriva's copy of grub. (You can get there by pressing c when you boot the PC and it displays the grub menu).

You will need to know what partition Mandriva is installed in.
for example if mandriva is in /dev/sda5 in grub talk that would be (hd0,4) 
to change the mbr to point to Mandriva grub
```

root (hd0,4)
setup (hd0)
```

a couple of useful links[IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.htm")  
[IDBS Remove/Replace/Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.htm")

---

