---
title: "Please       help !"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-05-20
Hello
I installed Ubuntu 9.04 just now on MY OTHER computer. I had two hard disks a normal one and a portable one I installed Ubuntu on the Portable Hard Disk but I don't know how I think it was installed      on the internal Hard Disk. This is not the problem the problem is when I open my computer It says: 

"Grub Loading, Please wait..
Error 21"

And it doesn't  boot at all
Please Help me

---

### Post by MuH4hA on 2009-05-20
Hey mosaabJ,

my advice would be to install GRUB again:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

hope it works this time ;-)

---

### Post by jimingkui on 2009-05-20
You need a live CD for ubuntu install and boot with it,in a terminal window
execute:
        sudo grub
        find /boot/grub/stage1
        root (hd0,x)
        setup(hd0)
"x" is a number present after run "find /boot/grub/stage1"

---

### Post by bacardiandwatermelon on 2009-05-20
Is there a grub sticky telling people how to rebuild grub? It seams this question keeps getting asked over and over again...

---

### Post by mosaabJ on 2009-05-20
I,ve done what everyone says and it says it succeeded but when I restart the computer the problem still occur

---

### Post by mosaabJ on 2009-05-20
Does it make a difference if Ubuntu is installed on a portable hard disk

---

### Post by mosaabJ on 2009-05-20
Can               some one help  me please

---

### Post by mosaabJ on 2009-05-21
The problem now is different I can open Windows but I can't boot to ubuntu

---

