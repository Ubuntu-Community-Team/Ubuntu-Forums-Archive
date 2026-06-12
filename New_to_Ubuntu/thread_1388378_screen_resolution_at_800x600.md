---
title: "screen resolution at 800x600"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by cleverturtle on 2010-01-23
Hi,
 
I have looked and tried a few suggestions so far but am stuck.
 
The highest screen resolution available is 800x600. With WinXP, before I got rid of it, I used 1280x1024. How can I get it back using Ubuntu 9.10? I just installed today and don't know much about linux. The file others suggested modifying "xorg.conf" is not on my system anywhere, I searched for it. I reloaded the video driver from the Synaptic Package Manager (it is a SiS) and the video playback + audio works well. The resolution still can't be changed above current for the 4:3 ratio. I tried detecting the monitor, switching the monitor to a newer + another vga cable, no change.
 
When I type $ xandr --output VGA --mode 1280x1024 nothing happens.
I'm willing to try any workaround to get it to 1280x1024. Any help appreciated.
Thank you.

---

### Post by slooksterpsv on 2010-01-23
> **cleverturtle said:**
> Hi,
 
I have looked and tried a few suggestions so far but am stuck.
 
The highest screen resolution available is 800x600. With WinXP, before I got rid of it, I used 1280x1024. How can I get it back using Ubuntu 9.10? I just installed today and don't know much about linux. The file others suggested modifying "xorg.conf" is not on my system anywhere, I searched for it. I reloaded the video driver from the Synaptic Package Manager (it is a SiS) and the video playback + audio works well. The resolution still can't be changed above current for the 4:3 ratio. I tried detecting the monitor, switching the monitor to a newer + another vga cable, no change.
 
When I type $ xandr --output VGA --mode 1280x1024 nothing happens.
I'm willing to try any workaround to get it to 1280x1024. Any help appreciated.
Thank you.


SiS doesn't play well with Linux. What you're going to have to do is manually enter in the resolutions your monitor can support in your xorg.conf, found in: /etc/X11

I had to do this with my AMD Sempron 3400+ - Sis chipset. In terminal type: man xorg.conf for help


EDIT: Here we go:

Here we go: 

[php]
Section "Monitor"
  Identifier "name"
  entries
  ...
  DisplaySize  width height
EndSection
[/php]

---

### Post by cleverturtle on 2010-01-23
Thanks. Can I just create a xorg.config? I don't have one.

---

### Post by slooksterpsv on 2010-01-23
> **cleverturtle said:**
> Thanks. Can I just create a xorg.config? I don't have one.

What version of Linux are u running, it could be in a diff. location

---

### Post by cleverturtle on 2010-01-23
ubuntu 9.10

---

