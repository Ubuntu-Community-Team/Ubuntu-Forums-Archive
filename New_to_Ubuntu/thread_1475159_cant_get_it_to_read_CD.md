---
title: "cant get it to read CD"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by andyfew on 2010-05-06
So this is a pretty noobish question, but I can't get my computer to boot from the disk. It attempts to read it and fails continuously. I've tried ubuntu, xubuntu. I've burned it from a mac, from a PC. I've been using CD-RW.
Please tell me what information you need to help me.

Xubuntu startup error message:
"Isolinux: Diskerror 10, AK = 4280, Drive EF"

Ubuntu startup error message:
"Error reading boot CD"
then when i click reboot it gives me a chart of numbers or something

So please help, thanks ):P

---

### Post by madjr on 2010-05-06
hello

well you can follow this guide and see where you went wrong:

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

[http://youtube.com/watch?v=Z0tNpt5RZYI](http://youtube.com/watch?v=Z0tNpt5RZYI)

---

### Post by andyfew on 2010-05-06
thanks for the links, but it still isnt working

---

### Post by Miljet on 2010-05-06
Sounds like a dead or dying cd drive. Can you try your disks is another computer? A second choice is to try different disks in your computer. Not as definitive, but it is a start. Sometimes a defective drive will play music fine but will choke trying to read a large ISO file.

---

### Post by andyfew on 2010-05-06
@miljet

I think you may be right, I got it to go to the first title screen, then the initial language setup, then it froze and gave me the same error reading disk message. I will try swapping out CD drives or if i can find a USB thanggy big enough ill try it that way

---

### Post by narendraD on 2010-05-06
I too had trouble booting off the CD and no matter what i did, it would not boot and give me Error reading disk or I/O error. 

then i used the same CD to create a USB disk using Nerbootin and it worked. I used the BSB stick to install and am typing this from Ubuntu 10.04.

---

### Post by andyfew on 2010-05-07
ya so i swapped out CD drives, and i can get to the first install screen, with the different options, but then when i hit "enter" to install xubuntu it says error reading disk.

---

### Post by linuxman94 on 2010-05-07
Did you check the ISO for defects using md5sum?  Have a look here for how to do that.

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

Also, did you make sure to burn the disk at the slowest speed?  That would prevent defects on the disk.

---

### Post by andyfew on 2010-05-08
> **linuxman94 said:**
> 
Also, did you make sure to burn the disk at the slowest speed?  That would prevent defects on the disk.

It worked!!! you're amazing! lol if only i actually read the instructions WORD FOR WORD, jeeze sometimes I hate being male :P

---

### Post by JerichoKru on 2010-05-08
> **andyfew said:**
> It worked!!! you're amazing! lol if only i actually read the instructions WORD FOR WORD, jeeze sometimes I hate being male :P

Also, after burning, it is a good idea to check the disk's integrity before actually trying to boot off of it (last option in the CD's boot menu).

---

