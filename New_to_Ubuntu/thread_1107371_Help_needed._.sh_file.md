---
title: "Help needed. .sh file"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by necronzero on 2009-03-26
I downloaded the PS3 media server  for linux, which comes in a tar.gz, so i decompressed it, (btw, i alrdy installed java) and when i try to run the .sh for it to open, i always get the "open with" window... how do i get it to run as a program???

---

### Post by SuperSonic4 on 2009-03-26
You'd run in in a terminal. You can use dolphin's konsole plugin (by pressing F4 inside dolphin) or konsole itself. Navigate to the directory the sh file is in and type ```
sh <file>.sh
```. It may not need root permissions to install but if it does type ```
sudo sh <file>.sh
```

---

### Post by linuxisevolution on 2009-03-26
> **necronzero said:**
> I downloaded the PS3 media server  for linux, which comes in a tar.gz, so i decompressed it, (btw, i alrdy installed java) and when i try to run the .sh for it to open, i always get the "open with" window... how do i get it to run as a program???

right click the file and select properties, then select the permissions tab, then change all the drop down menus to read/write and check the "make executable" box.

Next click applications >> accessories >> terminal and type:

sudo ~/Desktop/file.sh 

change ~/Desktop/file.sh to the location the file is in.

---

### Post by necronzero on 2009-03-26
fenrir@fenrir-desktop:~$ sudo '/home/fenrir/Desktop/Fenrir/PS3 Media Server/pms-linux-1.10.5/PMS.sh'
dirname: extra operand `Media'
Try `dirname --help' for more information.
Unable to access jarfile //pms.jar

I got that... o.o

---

### Post by linuxisevolution on 2009-03-26
> **necronzero said:**
> fenrir@fenrir-desktop:~$ sudo '/home/fenrir/Desktop/Fenrir/PS3 Media Server/pms-linux-1.10.5/PMS.sh'
dirname: extra operand `Media'
Try `dirname --help' for more information.
Unable to access jarfile //pms.jar

I got that... o.o

To use spaces you have to use a backslash, so the command is:
```

sudo '/home/fenrir/Desktop/Fenrir/PS3\ Media\ Server/pms-linux-1.10.5/PMS.sh

```

---

### Post by necronzero on 2009-03-26
> **linuxisevolution said:**
> To use spaces you have to use a backslash, so the command is:
```

sudo '/home/fenrir/Desktop/Fenrir/PS3\ Media\ Server/pms-linux-1.10.5/PMS.sh

```

Oh, ****, you're right, its running now... thanks a lot... is there a way to run it via clicking it XD?

---

### Post by linuxisevolution on 2009-03-26
> **necronzero said:**
> Oh, ****, you're right, its running now... thanks a lot... is there a way to run it via clicking it XD?

Yes, double click it and click run in terminal :lolflag:


Sorry, but it's best to learn the way in terminal first. :)

---

### Post by necronzero on 2009-03-26
> **linuxisevolution said:**
> Yes, double click it and click run in terminal :lolflag:


Sorry, but it's best to learn the way in terminal first. :)

Yeah yeah, ive tried doing that, but it doesnt let me click "OK"

---

### Post by linuxisevolution on 2009-03-26
Well that's odd...

There is one way:

open text editor:

at top of file, write:

!#/bin/bash
sudo '/home/fenrir/Desktop/Fenrir/PS3 Media Server/pms-linux-1.10.5/PMS.sh'
exit0


and save it as something.sh

(you can name it whatever you want as long as it has .sh.)

Then double click the icon after saving.

---

### Post by necronzero on 2009-03-26
Weird, i still get the "open with" window when i double click it... I guess ill hafta stick with terminal to open .sh files =/

---

### Post by linuxisevolution on 2009-03-26
> **necronzero said:**
> Weird, i still get the "open with" window when i double click it... I guess ill hafta stick with terminal to open .sh files =/

Well, if the program has no gui to it then of course it requires the cli :P

---

### Post by necronzero on 2009-03-26
> **linuxisevolution said:**
> Well, if the program has no gui to it then of course it requires the cli :P

The program has a gui bro... XD

---

### Post by linuxisevolution on 2009-03-26
> **necronzero said:**
> The program has a gui bro... XD

Well that's odd. Maybe you can look in the program's .sh file and see if it's relating to a .bin file somewhere in your system, then you could just double click the .bin file :)

---

### Post by necronzero on 2009-03-26
> **linuxisevolution said:**
> Well that's odd. Maybe you can look in the program's .sh file and see if it's relating to a .bin file somewhere in your system, then you could just double click the .bin file :)

Well, its a java based program... it depends on PMS.jar. any ideas?

---

### Post by SuperSonic4 on 2009-03-26
Is it marked as executable?

---

### Post by necronzero on 2009-03-26
> **SuperSonic4 said:**
> Is it marked as executable?

Yes, both are.
HEY! ur a brummy! i got a good friend in birmingham.

---

