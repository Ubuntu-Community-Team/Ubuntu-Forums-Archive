---
title: "stdin: error 0 and udevd [66] : worker failed"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by sreeshs on 2011-05-02
Hi,

I am pretty new to Linux and wanted to try Ubuntu as an alternative to Windows.

Downloaded the iso image "ubuntu-11.04-desktop-i386.iso" and burned it on to a cd.

The system on which I intend to run Ubuntu is an assembled one with AMD Athlon XP CPU and ASUS mother board.

Tried to boot from CD, it displays the screen with Ubuntu logo and 5 status dots beneath it alternating in white and red, that screen just stays on for ever, so I tried pressing the left key a screen with "stdin: error 0" is displayed. It repeats again while pressing the left arrow key.

Then ejected the cd and pressed enter, got the message 
"mount: mounting /dev/sr0 on /cdrom failed: No medium found
stdin: error 0
/init: line 7: can't pen /dev/sr0: No medium found
stdin: error 0"

So inserted the CD again and pressed enter, nothing much.
After some more time displays the error

udevd[66] : worker [122] failed while handling '/devices/pci0000:00/0000:00:09.0/host0/target0:0:1/0:0:1:0/blck/sr0'

Can somebody kindly guide on where the problem is :confused:

The same CD is booting up fine on my IBM T400 Thinkpad so the cd should be fine, right ?

I tried installing Ubuntu in Windows using the CD. It says "Extracting files from G:\" continues till the status panel reaches about halfway, then just remains there :confused:  

Thanks in advance,
Sreesh

---

### Post by sreeshs on 2011-05-03
Ok, so what I did is first check the md5 hash, which came out good, then burned the image on to a new cd with write speed of 10x

That one booted good and I am replying right from the Ubuntu loaded in my system :)

---

