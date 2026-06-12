---
title: "how? update drivers/direct x and backups of"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by bodyharvester on 2009-07-10
i have had ubuntu for less than 24 hrs, and a big thanks to everyone who has helped so far, but how do i update my drivers again and update direct x back to 9.0c? this was easy enough in windows but im still finding my way around gnome.

i have a cd which came with my dell mini 9 which has the "dell support centre" which searches for updates and bios updates and drivers, etc, will this work in ubuntu too?

before i installed ubuntu though, i saved the folder of DELL drivers on my external hard disk, can they still be used by moving them somewhere or do i need to re-download them?

thanks
any help would be appreciated

i tried playing doom 3 linux after hearing about all the better performance compared to windows and was shocked by the framerate:lolflag:

---

### Post by nothingspecial on 2009-07-10
All the drivers you need should (hopefully) be included in the linux kernel.

You get updates through your update manager.

Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://www.hintsandthings.co.uk/musichall/CDroms.htm")

---

### Post by libra1780 on 2009-07-10
sometimes there is a firmware file to be loaded, or you have to compile the driver manualy because the one in the kernel doesn't work like you please, sometimes the proprietary driver shipped by manufacturer works better or has more features.. in this cases, update has to be done manualy.
for all the others, it goes automaticaly with the apt updates

> before i installed ubuntu though, i saved the folder of DELL drivers on my external hard disk, can they still be used by moving them somewhere or do i need to re-download them?windrivers are not compatible

> how do i update my drivers again and update direct x back to 9.0c? this was easy enough in windows but im still finding my way around gnome.there is no directx in linux. you can find a directx interface, like it's used in wine (windows emulator, or maybe not :) ) but nothing else

---

### Post by bodyharvester on 2009-07-10
thanks, but doom 3 runs with awful framerate even after every effect is disabled, how can i have the right drivers or latest direct x when doom 3 ran great on windows?

is there any way to check what directx i have or my drivers like the dxdiag menu in windows?

edit: im getting more updates now

also how does it get all those dirvers and bios updates automatically/in the kernel anyway?

im used to windows where i did everything on my own

edit: hold on, in software update thing i can add CD-ROM to the list, if i enter a cd will it get dell drivers?

---

### Post by jolx on 2009-07-10
> **bodyharvester said:**
> thanks, but doom 3 runs with awful framerate even after every effect is disabled, how can i have the right drivers or latest direct x when doom 3 ran great on windows?

is there any way to check what directx i have or my drivers like the dxdiag menu in windows?

edit: im getting more updates now

also how does it get all those dirvers and bios updates automatically/in the kernel anyway?

im used to windows where i did everything on my own

edit: hold on, in software update thing i can add CD-ROM to the list, if i enter a cd will it get dell drivers?

1) I doubt you would have Microsoft DirectX on your Ubuntu Linux operating system

2) the BIOS is separate to the kernel, kernel updates do not affect the BIOS

3) I don't think adding a cd full of windows software to the software sources will help (assuming it is windows software)

Do you know how to use the terminal?
Go to Applications --> Accessories --> Terminal and copy & paste the following command, then press enter
```
lspci | grep VGA
```
It should give some information about your graphics chipset, please paste that information here

---

### Post by bodyharvester on 2009-07-10
joseph@joseph-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

does this help? like i said doom3 was fine on windows, low qual of,course and without shadows, the game is so damn dark anyway:( its hard to see

---

### Post by jolx on 2009-07-10
> **bodyharvester said:**
> joseph@joseph-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

does this help? like i said doom3 was fine on windows, low qual of,course and without shadows, the game is so damn dark anyway:( its hard to see

sorry it seems as though that's just a really bad chipset at the moment [[link]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_intel_shape")]
but just make sure you have the drivers installed by going to [apt://xserver-xorg-video-intel]("apt://xserver-xorg-video-intel")

---

### Post by bodyharvester on 2009-07-10
so, doom 3 will never run as well as it did in windows?](*,)

well, i love ubuntu, and wierdly i may as well just re-install windows, complete doom 3 then rew-install ubuntu :) im not bothered, ubuntu does work, "out of the box" whereas with windows ill update it to run doom 3 

when i come back to ubuntu everything will be exactly the same

\\:D/ hoorah ubuntu!:lolflag:

actually when i re-install ubuntu it will be the netbook remix

---

