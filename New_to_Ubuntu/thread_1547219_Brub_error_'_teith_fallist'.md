---
title: "Brub error '_teith_fallist'"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by AlfyBoy on 2010-08-06
Type mistake on the title, it should be: Grub error '_teith_fallist'


Hi, I'm stuck on "grub rescue"

I've tried using the following commands from these [**[COLOR="Red"]page[/COLOR]**]("https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29")

> 1. ls

2. set prefix=(hdX,Y)/boot/grub

3. set root=(hdX,Y)

4. set

5. ls /boot

6. insmod /boot/grub/linux.mod

7. linux /vmlinuz root=/dev/sdXY ro

8. initrd /initrd.img

9. boot 




But i get stuck when I enter:


```
insmod /boot/grub/linux.mod
```

which throws back

> error: the symbol '_teith_fallist' not found.

And as the page explains in the following step I get linux command as unknown.
What can i do?
I haven't been able to find any info on that error.
Help. :(

---

### Post by AlfyBoy on 2010-08-06
Hi, I'm stuck on "grub rescue"

I've tried using the following commands from these [**[COLOR="Red"]page[/COLOR]**]("https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29")

> 1. ls

2. set prefix=(hdX,Y)/boot/grub

3. set root=(hdX,Y)

4. set

5. ls /boot

6. insmod /boot/grub/linux.mod

7. linux /vmlinuz root=/dev/sdXY ro

8. initrd /initrd.img

9. boot 




But i get stuck when I enter:


```
insmod /boot/grub/linux.mod
```

which throws back

> error: the symbol '_teith_fallist' not found.

And as the page explains in the following step I get linux command as unknown.

I have also tried these page to solve it: [Reinstalling GRUB 2 from the LiveCD]("http://ubuntuforums.org/showthread.php?t=1195275")
No luck

What can i do?
I haven't been able to find any info on that error.
Help. :(

---

### Post by cariboo on 2010-08-07
Please don't create multiple threads on the same subject, I have merged your two threads.

---

