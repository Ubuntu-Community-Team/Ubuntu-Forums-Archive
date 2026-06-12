---
title: "Blank after logo 9.10 Nvidie 9600 GT"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by lilj8069 on 2010-03-27
I just installed Ubunto 9.10 and during bootup after the white circle logo comes up and pulses the screen goes blank. I am brand new to linux and really want to get this working on my computer. I have an HP pavilion with a Intel Quad Core processor and a Nvidia Geforce 9600 gt video card. I've seen lots of threads complaining about video drivers but not sure if that is my problem here and how i can disable it if it is. 
 
Any help is greatly appreciated.
 
Thanks,
John

---

### Post by s_ø on 2010-03-27
Hi.
Reboot your ubuntu. In the grub menu, press 'e' to edit the boot option. Select the one with kernel and press 'e' again. There should be a long text line ending in 'quiet splash'. Replace 'quiet' with 'verbose'.
Hit enter and press 'b' to boot the edited option.
It should give you an idea about where the problem is.

---

### Post by lilj8069 on 2010-03-27
I did that, and now it gives me more feedback but it goes by so fast and doesn't crash on a line, the screen just goes black and it sits there. I've seen alot of people with this problem, just not alot of fixes for it.

Anyone have an idea?
 
--John

---

### Post by s_ø on 2010-03-27
can you get to a terminal?
Type ctrl+alt+F1 (ctrl+alt+F7 to get back to the graphical)


edit:
Can you boot the live cd?

---

