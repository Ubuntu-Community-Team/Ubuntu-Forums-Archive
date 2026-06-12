---
title: "reinstall ubuntu 11.04?"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by YellowBronco on 2011-07-11
i have nothing worth saving in my ubuntu computer, is there a way to wipe the drives and start over?
i would like to install the 64 version? 

it was a vista ultimate ver 6.0.6002sp2 machine , 
ubuntu on and off
amd athlon 64x2 dual core pro 5000+ 2.59 gh
bios american megatrends v1.6
smbios 2.5
power thermaltake tr2-500pp psf450s
6 g ram crucial
nvidia gforce 7900 gt/gto grapics w/ dual 22 monitors
dr A zid citizen tuv
hd B seagate st340810a 40g 
hd C crucial ssd 64g
hd E western digital 1600aajs 160g
dr q memorex 16x double layer 5395 cd-r/rw drive
dr r sony optiarc dvd rw ad-7190s ata 1.02

---

### Post by bodhi.zazen on 2011-07-11
you can wipe the hard drives if you wish using dd (write zeros to the hd), but you can also just format them.

[http://www.marksanborn.net/howto/wiping-a-hard-drive-with-dd/](http://www.marksanborn.net/howto/wiping-a-hard-drive-with-dd/)

---

### Post by MG&amp;TL on 2011-07-11
Maybe I'm missing the point here, and I'm really sticking my neck out here, what with an admin on the case (lots of respect to bodhi.zazen [-o<), but can you not just insert a ubuntu 64-bit cd and choose the 'install over existing ubuntu' or 'delete everything and make clean install' ?

---

### Post by westie457 on 2011-07-11
> **YellowBronco said:**
> i have nothing worth saving in my ubuntu computer, is there a way to wipe the drives and start over?
i would like to install the 64 version? 

it was a vista ultimate ver 6.0.6002sp2 machine , 
ubuntu on and off
amd athlon 64x2 dual core pro 5000+ 2.59 gh
bios american megatrends v1.6
smbios 2.5
power thermaltake tr2-500pp psf450s
6 g ram crucial
nvidia gforce 7900 gt/gto grapics w/ dual 22 monitors
dr A zid citizen tuv
hd B seagate st340810a 40g 
hd C crucial ssd 64g
hd E western digital 1600aajs 160g
dr q memorex 16x double layer 5395 cd-r/rw drive
dr r sony optiarc dvd rw ad-7190s ata 1.02

Quite a few ways actually.

They all start the though. Download the ISO, create the LiveCD\USB. Boot into the Live environment and select install.

During the install setup process select various things pertinent to your location. IE Time zone and keyboard and language.
In the where to install screen optons are there to install side by side with other OS, use the whole drive (this wipes everything off). The last option here is called Something Else, in this one you get to choose which drive and partition to use. If you choose to use the partition that already has an EXT3 or 4 file system on in the box with Do Not Use change this to EXT4 tick the small box to format and then in the box Use as select / . if you have separate partitions for /boot /swap and /home these will need to be formatted as well. Click okay/forward/continue. A warning box will appear about losing data and changes being written to disk. Clicking Accept also mean these changes cannot be undone and the install goes ahead. After a while a prompt about Grub should appear accept the default unless you have an esoteric disk arrangement and want/need Grub somewhere else. A short while after this a prompt to reboot shows. Click okay.
If the install was from a CD you have chance to eject it.
If from USB you will need to change bios settings to put the USB after the hard drive. Voila a brand new install of Ubuntu.

Enjoy.

---

### Post by YellowBronco on 2011-07-11
> **westie457 said:**
> Quite a few ways actually.

They all start the though. Download the ISO, create the LiveCD\USB. Boot into the Live environment and select install.

During the install setup process select various things pertinent to your location. IE Time zone and keyboard and language.
In the where to install screen optons are there to install side by side with other OS, use the whole drive (this wipes everything off). The last option here is called Something Else, in this one you get to choose which drive and partition to use. If you choose to use the partition that already has an EXT3 or 4 file system on in the box with Do Not Use change this to EXT4 tick the small box to format and then in the box Use as select / . if you have separate partitions for /boot /swap and /home these will need to be formatted as well. Click okay/forward/continue. A warning box will appear about losing data and changes being written to disk. Clicking Accept also mean these changes cannot be undone and the install goes ahead. After a while a prompt about Grub should appear accept the default unless you have an esoteric disk arrangement and want/need Grub somewhere else. A short while after this a prompt to reboot shows. Click okay.
If the install was from a CD you have chance to eject it.
If from USB you will need to change bios settings to put the USB after the hard drive. Voila a brand new install of Ubuntu.

Enjoy.

wow , kool , thanks for all the info, i was about to run a nuke program, 
what does  " :~$ " mean?  i keep getting that error

---

### Post by westie457 on 2011-07-11
> **YellowBronco said:**
> wow , kool , thanks for all the info, i was about to run a nuke program, 
what does  " :~$ " mean?  i keep getting that error

Have absolutely no idea, never heard of it and never had it.

---

### Post by bodhi.zazen on 2011-07-11
> **MG&TL said:**
> Maybe I'm missing the point here, and I'm really sticking my neck out here, what with an admin on the case (lots of respect to bodhi.zazen [-o<), but can you not just insert a ubuntu 64-bit cd and choose the 'install over existing ubuntu' or 'delete everything and make clean install' ?

The only reason to use dd is the OP stated he wanted to "wipe" the drives.

As you say, that is not necessary, one can simply install / format at will

---

### Post by alquery on 2011-07-11
> **YellowBronco said:**
> wow , kool , thanks for all the info, i was about to run a nuke program, 
what does  " :~$ " mean?  i keep getting that error

When do you get that error? After you reinstalled Ubuntu? Is there anything after the ":~$"?

---

### Post by westie457 on 2011-07-11
> **alquery said:**
> When do you get that error? After you reinstalled Ubuntu? Is there anything after the ":~$"?

Not so sure it is an error message. this is visible in every instance of using a terminal. EG ```
graham@graham-Aspire-3690:~$ 
```

---

### Post by YellowBronco on 2011-07-12
yes , its after i log in with name and password, 
lools like this
"yellowbronco:~$"
i think it was like that, there might have been something in between, i am at the memtest86 v4.10 pass 90%

should my chipset read : "amd k8 imc (ecc : disabled)"   ?

---

### Post by YellowBronco on 2011-07-22
well, its been almost 2 wks and im finaly to where i can reinstall   11.04, it was my own stupidity, i put a version 6 on top of 11.04. i   thought it was just info from the library , not a whole new install.   like i said^ i like ubuntu, ive been too enamored in the bill gates   world to fully get it all of ubuntu yet, i guess if u are starting out   fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,   re-installed a new os , xp not the vista stuff, had to re-find all   drivers this way and reinstall from bios, in order to do that i had to   take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

---

