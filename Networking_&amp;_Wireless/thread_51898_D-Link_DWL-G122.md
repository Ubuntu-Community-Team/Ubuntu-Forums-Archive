---
title: "D-Link DWL-G122"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by grman3 on 2005-07-25
Hello all

I am very very new to linux. I got ubuntu to install with no problems on my thinkpad 600E. Every thing works great...but i cant get my wireless usb to work. It's a D-link DWL-G122 A2. the laptop sees the hardware but no drivers ](*,) . anyone know how to fix this? If you can help me i might need your help in layman's terms because this is my first time with any linux :roll:  .

thanks for any help Jonathan

---

### Post by jdong on 2005-07-25
Cut and paste output from 'lspci'

---

### Post by grman3 on 2005-07-26
im sorrry if this sounds stupid but like I said i know almost nothing about linux. How do i get the "lspci'? do i do it from a terminal?

thanks Jonathan

---

### Post by jdong on 2005-07-26
Yep, just pull up a Terminal and type 'lspci'

---

### Post by grman3 on 2005-07-26
Ok here it is 

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host brige (rev 03)
0000:00:01.0 PCI bridge: Inel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP brige (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [crystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:01.0 VGA compaeible controller: Neomagic Corporation NM 2200 [MagicGraph 256AV] (rev20)



well i hope thats the only one of them you need because i have no way of copy and pasting them so i had to type it out...but But if i dont have to use Winblows its worth it.

`Jonathan

---

### Post by grman3 on 2005-07-27
So from what I have found with google I need to use ndiswrapper to get this to work. Is this some thing that i can down load to my mac and burn to a cd to load in linux of is there some thing more to it. Also if this is the way it needs to be done can some one point me to the right one for ubuntu. sorry for all the stupid questions but like i said this is my first time using linux.

~Jonathan

---

### Post by grman3 on 2005-07-28
ok so I found all the things i need for ndiswrapper and got them on my laptop and I am following the directions from ( [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) )
but when I put in the make deb command I get

 "/bin/sh: line 1: fakeroot: command not found make: *** [deb] Error 127"
I have no idea what that means or how to fix it. 

any help is apresheated 
~Jonathan

---

### Post by gmc on 2005-07-28
You need to install the "fakeroot" package.

Open a terminal window.
Type the following:

sudo apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r) (it'll ask you for your password)

When it's done, try following the ndiswrapper instructions again.

G.

---

### Post by jdong on 2005-07-28
The 122's are either prism54's or rt2570's. I have rev B, which is the RATECH chip. The prism54's are also supported under Linux quite well, with the build headers mentioned by the person above :) Just go download the sources from the prism54 site, then do a:

tar xzvf filename_of_sources.tar.gz
cd new_directory_made_by_last_command
make
sudo make install

---

### Post by grman3 on 2005-07-29
ok I got the fakeroot to work but now when i enter the make deb command it starts to do its thing but it is still having problems ( or maybe its the newbie using it :-) ). the last 8 commands are errors 

make[3]: cc: command not found 
make[3]; *** [loadndisdriver.o] error 127
make[3]: leaving directory ' /home/jon/ndiswrapper-1.1/utils'
make[2]: *** [build-utils] error 2
make[2]: leaving directory '/home/jon/ndiswrapper-1.1 '
make[1]: *** [binary] error 2
make[1]; leaving directory '/home/jon/ndiswrapper-1.1 '
make: *** [deb] error 2

---

### Post by gmc on 2005-08-04
Looks like you're missing the c compiler. Try:

sudo apt-get install gcc

---

### Post by RCPR on 2005-08-10
I am having the same problem with the same wireless card but my problem is that when I enter the command "make" I get this error...

Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give tha path to kernel sources with KSRC=<path> argument to make
make[1]: ***[prereq_check] Error 1

how can I fix that?

---

### Post by luc1972 on 2005-08-25
> **RCPR]I am having the same problem with the same wireless card but my problem is that when I enter the command "make" I get this error...

Can't find kernel sources in /lib/modules/2.6.10-5-386/build said:**
> : ***[prereq_check] Error 1

how can I fix that?

I've got a different wireless card, but the same problem.  After checking which kernel I  have and downloading it, I still get this error message even if I type "make KSRC=" with the correct path to the downloaded kernel source.  HELP!

---

### Post by luc1972 on 2005-08-25
[QUOTE=luc1972]I've got a different wireless card, but the same problem.  After checking which kernel I  have and downloading it, I still get this error message even if I type "make KSRC=" with

And then I read GMC's message on the previous page about fakeroot and the headers etc.  Did what he said and it is all working fine.    COuld someone explain what that is about?  Just for future reference?  Is it ubuntu specific, becuase Ubuntu doesn't have a root account?

---

### Post by p_mirowsky on 2007-02-27
This is the location of more current information regarding this problem.


[http://anirudhs.chaosnet.org/blog/2005.10.23.html](http://anirudhs.chaosnet.org/blog/2005.10.23.html)

For Ralink (the chip maker) website support for linux goto...

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

