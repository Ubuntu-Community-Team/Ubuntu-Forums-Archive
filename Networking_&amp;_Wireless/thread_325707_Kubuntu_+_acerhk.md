---
title: "Kubuntu + acerhk"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Muis24 on 2006-12-26
Are there any (k)ubuntu users around that have the acerhk source tarball, of even beter, a debian package? The main site [http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/) is inaccesible, so I can't get my acer hotkeys to work (that is, my wireless button doesn't work. My volume buttons **do** work, just like the mail button and the mute button.) Since my wireless button doesn't work, I can't switch my wifi card on :( . Can anybody help, please? I have a acer aspire 1522 WLMi laptop with a built-in AirConn. wifi card and I'm running Kubuntu 6.10 in 64-bit mode.

---

### Post by romeo2 on 2007-01-04
I am having exactly the same problem, but then with Ubuntu 6.10 and a Acer Travelmate 654lci.

Did you managed to get it working? Or does someone else have a solution?

---

### Post by janmartin on 2007-01-04
A short Google search brought up this:

[http://lists.debian.org/debian-devel/2006/03/msg00056.html](http://lists.debian.org/debian-devel/2006/03/msg00056.html)
leading to 

[http://kanotix.com/files/debian/pool/main/a/acerhk/](http://kanotix.com/files/debian/pool/main/a/acerhk/)

Happy download!

---

### Post by Muis24 on 2007-01-05
Thank you very much, but since the packages are for i386, do you think I can compile it on a 64-bit platform?:-k Anyway, thank you for your help :)

---

### Post by Muis24 on 2007-01-05
Remeo2, if you're also using a 64-bit version, maybe you could try compiling acer_acpi on your machine. I'm going to try that now, because there are only 32-bit versions of acer_hk :-k Have a look at this: [http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

---

### Post by romeo2 on 2007-01-05
I installed the .deb debian package from [http://kanotix.com/files/debian/pool/main/a/acerhk/](http://kanotix.com/files/debian/pool/main/a/acerhk/)
But how do I get my keys working now? Do I need to add this to my kernel? Or did the debian package already do that for me? And how do I do that?


Muis24: (Un)fortunately I am using the default 32bit version. I haven't even checked yet if my processor supports 64-bit.
Please tell us in this forum if and perhaps how you got it working in 64bit.

---

### Post by Muis24 on 2007-01-06
Romeo2: maybe you could get them to work by typing "modprobe acerhk" in a console window as a root, then check if the buttons work.

---

