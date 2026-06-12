---
title: "bcm4306 driver problems"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by sludge99 on 2006-12-16
hi i got a belkin f5d7001 pci wireless card with id 14e4:4320 (rev 03)
and lspci says it is a 4306 broadcom chipset

i have prity much followed this how to here [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174") and the page in the wiki 

but after putting the firmware using bcm43xx-fwcutter in /lib/firmware and then using modprobe bcm43xx or restarting the computer i get a kernel panic along the lines of

<0> Kernel panic - not syncing:Aiee, killing interrupt handler!

ive used a few different firmwares that i could find the first wl_apsta.o in the thread mentioned above then the bcmwl5.sys from my driver cd that came with my card
then a bcmwl564.sys that i picked up from somewhere

i am on a prity much default amd64 ubuntu edgy install

this card works fine on 386 with ndiswrapper but i cant get it to work on amd64 with the bcm43xx driver or ndiswrapper

ndiswrapper does a kernel panic as well when i use the only 64bit driver i could find for the card

any help at all would be so greatly appriciated because i am without internet

---

### Post by Subw00fer on 2006-12-16
I wish that link would work for me but you need a wired connection.  I don't so I am typing this on a laptop next to my PC

---

